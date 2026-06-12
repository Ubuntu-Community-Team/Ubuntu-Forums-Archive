---
title: "Erm... where'd my utility panel go?"
date: 2010-11-05
forum: General Help
---

### Post by jackechanprime on 2010-11-05
:confused:

He guys, this is probably kinda nooby, but i've run into a bit of a problem. All the little system icons on my system panel/bar/thing have decided to go AWOL on me. I'm not sure what it's officially called, but it's the set of icons on the main system bar at the top of the screen, the one that says "applications" etc on the left, and "time/date" and 'powerdown options' on the right.

The panel as a whole is still there, but the little icons on the right side, usually near the date that cover sound, wifi, and whatever else was there by default, vanished. Not sure how or why. (no i didn't accidentally delete the panel)

I'm not sure, but aren't these things supposed to be pretty permanent? Either way, after about an hour and a half of sifting through gnome help manuals and various interfaces i cant figure out how to add those standard functions back to the main panel. So question 1 is, where in gods name did these things get stashed as an option for adding them back, or, is there a way to just restore the default panel.

To top it all off, with the sound manager icon missing (no clue if that's the actual problem), my sound control seems to have gone with it. Master volume interface is no longer appears to exist, and other sound manager interfaces don't actually change the volume. Multi-media keyboard volume up/down/mute no longer work. System-wide mute not functioning. And some programs are unable to "grab" the sound, especially browser embedded programs.

;_; did i do it? i didn't f*** with anything, so i have NO idea what did it.

please help:
~Q

---

### Post by Brandel Valico on 2010-11-05
If the panel is still there as it seems it is lets try this. Right click the panel. You should get a drop down box with the option to "Add to Panel" select this. That will open a window up. Select the one labeled "Menu Bar" then click add. That should get your applications Places and System menus back at the top.

If they are missing

You also want "Indicator Applet Session" "Notification Area" "Clock" and "Indicator Applet"

Those will give you back your sound icon and network icons,Your user and power buttons the time and various programs in use at that moment. You may add or remove anything in that list using this method so play around with them. You may find other things of use.

If the above doesn't work. Then there is another issue that will take someone with more skill then me to help get fixed.

---

### Post by jackechanprime on 2010-11-05
Thanks, that got all the icons back. I can see why i skimmed over them, they weren't exactly named "sound manager icon." Oh well, such is life.

Well, that's dealt with... BUT...

Sound control is still not re-established. Master volume is not actually changing the system volume. wtf? System-wide mute command did squat. Something is definitely not communicating right. Did the system volume commands lose master setting or something? i dont even know what to ask, but how do i fix it?

While i'm on the topic, is there any sort of application out there where i can select which programs "grab" the sound? Manually assigning/blocking sound threads as i want, especially in cases where the system did not "grab" the sound right on first try?

---

### Post by Brandel Valico on 2010-11-05
It should allow you to adjust the volume using the sound applet.

If not then try this. Goto Applications-> Accessories->Terminal

When the terminal opens you will see your user name. Type in alsamixer and hit eneter. Then press F5 to get access to all the settings check to see if things like Master or PCM are muted. If they are unmute them.

You may have to add alsamixer not sure if it is still installed by default. If it says command not valid or found. Then type "sudo apt-get install alsamixer" minus the "" when it asks for your password type it in. If this is your first time using the terminal it doesn't show you typing but it is typing. Just hit enter when your done doing so. 

This should also let you see what card and such your using and if need be select a different card using F6.

Hope this helps.

---

### Post by jackechanprime on 2010-11-05
I'll try it. I'm good with terminal, so no worries there. it's just the "user friendly" stuff that gets me sometimes. lol... go figure.

~Q

It brought up the sound mixer interface. Everything appeared in working order, but more than half of that stuff i'm completely clueless about. I'm no DJ. I'll keep fiddling with it. Anything is SHOULDN'T do to it?

---

