# ESPHome-BluetoothClock

## Idea
Make a bluetooth clock radio speaker radio thing better and more useful.
I bought one of these and it got delivered with a broken clock display segment, I got a replacement and two came and both had the same fault then a third got shipped with again the same fault. I ended up with all of them for free in the end.
So what do with them?
The missing segment in the clock is really annoying, the "moodlight" RGB colours and effects are horrible and the capacitive buttons stick and jump presses all the time.

What I have ended up with is a clock that is synchronised with a timeserver with a really nice mood light with effects and colours that I can change in Home Assistant.

But not only a clock! I have imported sensors from Home Assistant into the ESP32 running ESPHome that show me - the weather right now using animated icons - the temp of the living room - the temp of the bedroom - my phone battery % - the days hours, minutes and seconds till Ajax play their game - the days hours, minutes and seconds till Aston Villa play their game and when the next Formula 1 session is starting.
I have paired the bluetooth to the Raspberry Pi4 in the digital fireplace and use it to play Text To Speech (TTS) alerts from Home Assistant.
When there is a football game or F1 coming up it will play a TTS message to the speaker "One hour till Ajax kick off!" and another trigger for 15 minutes before a game/race.




## Parts used

- Denver CRLB-400
- LilyGO TTGO T-Display V1.1 ESP32
- 24 RGB LED ring

## Coding

### ESPHome
The display is made with "pages" within the display component, I built a page for each sensor I wanted to display.
It then displays these pages in a sequence with a ten second delay before showing the next page.
I made it so that the sequence displays the time then a sensor then back to the time again in a loop, so that the time is always ten seconds at max before being displayed again.

I spent a lot of time finding the correct fonts and font sizing for the display and ran out of memory on the ESP more than a few times!
The same with images for the weather display - lots of time spent resizing and saving in different formats to reduce the phyiscial sizes but also the file sizes.

The weather icons work by displaying different icons based on the weather condition from the local weather service station 5 km away so it is pretty accurate. I have an add on for Home Assistant that brings in about 30 different sensors from the weather station but I am only using the outside temp and the weather condition in this project.


### Home Assistant
Not really much to do with Home Assistant on this project other than sending ESPHome some existing sensors and a few little automations to turn things off and on and play the TTS alerts.

## Construction
So I took it apart and found the display is one board and the bluetooth radio - SD card reader - mini speakers - volume controls and battery are on another board.

So I had the idea to remove the display board and leave the bluetooth board intact.
At first I was going to buy a LED 7 segment display with blue LED's and use an ESP board to control it but after looking around I found an all in one solution that was going to cost 3 euros more than the ESP32 I was going to buy.

The TFT display on the Lillygo board is very clear and bright and looks good even behind the opaque diffuser on the front of the display.
The RGB "dumb" LED's were in a ring on the underneath of the display board, I sourced a 24 LED adressable RGB ring for 7 euro that would be able to do any kind of colour or effect and maybe even act as an "analogue clock" by using LED's for the hands of the clock.

I put the ESP32 and TFT board onto some protoyping board and screwed it down using the origonal plastic posts that held down the old display board.
The new LED ring was taped to the plastic surrond behind the display board.


## Pictures / Video

## Conclusion

This is my most complicated device so far and after using it for a while I can see some additions I could make such as making an "alarm" on the display and LED ring for certain triggers.
I am very happy with this project and will convert the other two clocks when the display boards arrive.

