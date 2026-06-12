---
title: "System&gt;Preferences&gt;No Sound Option?"
date: 2010-01-30
forum: General Help
---

### Post by GoogleJunkie on 2010-01-30
Hello I've been trying out Ubuntu Karmic for awhile its finally compatible with my Creative XFI soundcard, but my question is after installing and unistalling jack, jackEQ, etc because i i couldnt get them to work, i noticed my sound system preferences are no longer an option and the sytem tray doesnt show the icon either how do i get this bacK? 
PS my sound works though...strange Ive seen people here answer questions plenty of times about my exact problem but i lurk no more i couldnt find any thread that addressed this problem so im asking for some of that expertise and genuine advice please.

---

### Post by Elfy on 2010-01-30
Check that it has not just been turned off - either right click the menu and edit - go to Sound and check the sound option has tick

or run alacarte from the terminal.

---

### Post by garvinrick4 on 2010-01-30
> **GoogleJunkie said:**
> Hello I've been trying out Ubuntu Karmic for awhile its finally compatible with my Creative XFI soundcard, but my question is after installing and unistalling jack, jackEQ, etc because i i couldnt get them to work, i noticed my sound system preferences are no longer an option and the sytem tray doesnt show the icon either how do i get this bacK? 
PS my sound works though...strange Ive seen people here answer questions plenty of times about my exact problem but i lurk no more i couldnt find any thread that addressed this problem so im asking for some of that expertise and genuine advice please.

If it one in upper right hand corner. Right click on upper panal/add to panel/notification area and add it.

If need to add to panel, right click on far upper left hand corner icon/Preferences on left/
add sound icon

---

### Post by GoogleJunkie on 2010-01-30
Um i think im being misunderstood i took the advice and right cliked the specific spot to add not a new panel but to the tray panel but the program i want too add (which is the forementioned sound control where you adjust volume choose hardwaredrviers etc.) isnt even listed to bee added to the tray panel nor is it in the System>preferences>Sound, Sound is not listed  thats the problem how do iget it back?

Tried alacarte it brought up a list but its not that sound isnt ticked theres no sound option TO tick thats my frustration

---

### Post by garvinrick4 on 2010-01-30
> **GoogleJunkie said:**
> Um i think im being misunderstood i took the advice and right cliked the specific spot to add not a new panel but to the tray panel but the program i want too add (which is the forementioned sound control where you adjust volume choose hardwaredrviers etc.) isnt even listed to bee added to the tray panel nor is it in the System>preferences>Sound, Sound is not listed  thats the problem how do iget it back?

Tried alacarte it brought up a list but its not that sound isnt ticked theres no sound option TO tick thats my frustration
It is part of The Notification Area option for sound control.

Anything else will be in Pulse Audio in ubuntu software centers, there is about 6  or 7 options in Pulse Audio there and 1 gnome-volume-control program. That is all I can think
of.

---

### Post by GoogleJunkie on 2010-01-31
Thank you for the quick response everyone I downloaded the GNOME and Pulse audio it works but its not the volume adjuster that can be simply turned down w/o bringing up a menu  i DO want that but i dont wanna have to bring up a menu all the time just the one slider for master volume the original program or whatever came with Ubuntu is no where to be found (check your milk carton) I miss that volume icon, I took it for granted... :-({|=LOL in the mean time all necessities are handled but if anyone has ideas or has experienced this before give a noob a hand :smile:

---

### Post by Wizzu on 2010-02-24
The sound volume adjusting slider is probably provided by the program called gnome-volume-control-applet. Try running that from the command line and see if you get your control slider back. You might need to add it to manually start up on login (Preferences -> Startup Applications).

Didn't test any of this, so take it with a grain of salt..

---

### Post by Silent_Voice on 2010-03-20
Maybe a little late but go to terminal and type "sudo apt-get install gnome-media"
The Sound option will appear in the Preferences.. 
It worked for me though I am not sure how to bring the sound to the panel..

Edit: After restart the sound icon appered on the panel

---

