---
title: "Start Weatherbug Automatically"
date: 2011-09-09
forum: General Help
---

### Post by waltwin on 2011-09-09
I would like to start weatherbug automatically when I start my computer but I am not having any success. I tried going to "System>Preferences>Start up Applications but no joy.

Any assistance would be greatly appreciated and thank you in advance.

---

### Post by Frogs Hair on 2011-09-09
To find the command to add in startup applications , open the main menu and locate Weatherbug . Right click on the line with Weatherbug , look in properties and copy / paste that command into the command box in startup applications . Check in the Weatherbug's preferences for an auto start option also .

---

### Post by waltwin on 2011-09-09
> **Frogs Hair said:**
> To find the command to add in startup applications , open the main menu and locate Weatherbug . Right click on the line with Weatherbug , look in properties and copy / paste that command into the command box in startup applications . Check in the Weatherbug's preferences for an auto start option also .
I did as you suggested but no joy. Perhaps I have something else in my machine messed up. Thank you very much for your response.

waltwin

---

### Post by Frogs Hair on 2011-09-09
Check to see if the case is correct in the name : WeatherBug . That is all I can think of .

---

### Post by ctsdownloads on 2011-09-12
> **waltwin said:**
> I would like to start weatherbug automatically when I start my computer but I am not having any success. I tried going to "System>Preferences>Start up Applications but no joy.

Any assistance would be greatly appreciated and thank you in advance.

I work with Earth Networks (owners of the WeatherBug brand) and was part of the reason why there was a Linux version in the first place. Few things.

1) WB for Linux hasn't been updated since Ubuntu 9.10. If it's working for you, awesome, but *_expect it to be problematic_* as the codebase hasn't been updated.

2) In Ubuntu 11.04, System>Preferences>Start up Applications with the command [HTML]weatherbug[/HTML] will autostart IF you have the application already running successfully. What I mean by this is that when you click on the application, it runs alright. If it still fails, then you'll want to do what I do with JungleDisk.

> #! /bin/sh
sleep 120
weatherbug

Then you'll use Start Up Applications to link to this bash script (/path_to_file/weatherbug_bash_script). Make sure to right click this script and make it executable.

It's entirely possible that there will be a new, non-java based version in the eventual future, but it's not on the map at the moment. Anyone wanting to roll their own is encouraged using the WeatherBug API. Cannot post the links here without spamming, but you can Google WeatherBug API for more info. I can be contacted at MHartley (at) WeatherBug Dot com if you still have questions.

---

