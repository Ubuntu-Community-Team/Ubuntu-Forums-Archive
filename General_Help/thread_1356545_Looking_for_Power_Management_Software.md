---
title: "Looking for Power Management Software"
date: 2009-12-16
forum: General Help
---

### Post by awildthingy on 2009-12-16
Hey all, here's the deal, my desktop computer resides in my bedroom and on occasion I like to watch a movie before bed. Unfortunately, I am not always awake by the end. Not a problem when I am running Windows, I can be sure the monitor will shut off when the video concludes just by popping open the power management window and selecting the proper preset that I have created for the job.

Unfortunately the Ubuntu Power Management Preferences Dialog is no equivalent. I was wondering if the crowd here knew of an application that adds a few more functions I am looking for in Ubuntu.

I am not so sure that I am communicating clearly so Ill list the things I am looking for in such a program:

[LIST]
[*]Equivalent in function to the Windows Power Management Dialog
[LIST]
[*]Allows me to set the computer to turn off the monitor after a definable time period of inactivity (Between 1 min up to x number hours and never)
[*]The ability to save preferences into multiple presets for fast switching of popular settings.
[/LIST]
 
[*]It is smart enough to know that when a video is playing its not in idle.
[/LIST]
I am savvy, but no programmer, so guys I really appreciate any advice or links you can give me. Thanks for making open source that much more appealing to the average joe; your hard work will pay off sooner or later. ;)

---

### Post by 3rdalbum on 2009-12-16
System > Preferences > Power Management.

On AC Power, put display to sleep when inactive for: (whatever period of time).

There are no multiple presets for this program, just different options for AC and battery. The setting is stored in gconf though, so you can actually write a little script that calls the command-line gconf get/set functions to change the settings. At the moment I don't have time to write such a thing for you; but if you get stuck I'd be happy to help.

If your video player has an option for "inhibit screensaver" then use it; it will also stop display sleeping while the video is playing.

---

