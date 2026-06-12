---
title: "ubuntu netbook remix with external monitor problems"
date: 2009-09-22
forum: General Help
---

### Post by Fatigoworld on 2009-09-22
I recently installed Ubuntu Netbook Remix 9.04 on my Acer aspire one 8.9 netbook.  when i mirror the display with an external monitor the external display says "no signal" and the highest resolution option is 800 x 600.  whats odd is that if i log out the external display shows the log in page...as soon as i log back in the screen goes black again and says "no signal".

i need help fixing this but i am a very basic user and cannot use the terminal.  please help me fix this...i know how to use add/remove and synaptic.  just no commands please

thanks!!

---

### Post by Fatigoworld on 2009-09-22
any help?

---

### Post by Fatigoworld on 2009-09-22
solved it on my own by messing around.  the external screen will only work if i use the quick key Fn+F5.  i dont know why but thats the only way it will work.  fine by me

the resolution is still off its stuck at 800X600.  i am going to search for a fix to that but if anyone reads this and knows how to do it without using the terminal, that info would be greatly appreciated as well.

---

### Post by surfed on 2009-09-22
It might be your video driver, on my eeepc the intel driver sucks, but karmic koala will apperently fix this...

---

### Post by Fatigoworld on 2009-09-22
my driver worked fine with windows all i had to do was raise the resolution.  anything i can do in the mean time until koala comes out?

---

### Post by surfed on 2009-09-22
You could manually install the new intel video driver, search around it has been done.

---

### Post by blackened on 2009-09-22
> **Fatigoworld said:**
> ...i am going to search for a fix to that but if anyone reads this and knows how to do it without using the terminal, that info would be greatly appreciated as well.

Eventually you'll have to get your hands dirty and learn to use the terminal. While you *might* be able to get by without it, you'd be missing out on easily the most capable tool on the entire OS. I know it's daunting at first, but the worst that can happen is you mess things up and have to learn to fix them. What's wrong with learning?

If you'd like, I can get you going in the right direction to fix this problem via the terminal.

---

### Post by Fatigoworld on 2009-09-22
> **surfed said:**
> You could manually install the new intel video driver, search around it has been done.

just read some instructions one this followed by this sentence....

"Careful, though: playing with Xorg can have adverse side effects, so backing up the original files might be a good idea."


guess im going to have to wait which is dissapointing because everything is HUGE on my external monitor..

---

### Post by surfed on 2009-09-22
You remind me of my mum when she said "Dont run you might fall..."

---

### Post by Fatigoworld on 2009-09-22
> **surfed said:**
> You remind me of my mum when she said "Dont run you might fall..."

more like "dont mess with expensive things you know absolutely nothing about."  ive had to reinstall countless times after messing things up, im at my wits end and dont want to go through it again.  ill stick with bikes where i actually know what im doing.

unless of course someone can tell me how to do it with my little mouse clicker...

---

### Post by t0p on 2009-09-22
> **Fatigoworld said:**
> just read some instructions one this followed by this sentence....

"Careful, though: playing with Xorg can have adverse side effects, so backing up the original files might be a good idea."


guess im going to have to wait which is dissapointing because everything is HUGE on my external monitor..

Sorry, I don't understand: why are you going to have to wait?

Are you scared to edit xorg because of that warning?  If you don't mind me saying, that is silly.  The warning says playing with xorg can have adverse effects, *so backing up the original files might be a good idea*.  In other words: Back up the original xorg file.  Then make changes.  If the changes cause problems, use the backup file to put things back to how they were.  You're not going to screw up your machine if you've made backups.

It's a shame that you're letting irrational fears stop you from tinkering with your computer.  Like what you said about not being able to use the terminal.  When people tell you to put certain commands into the terminal, usually all you need to do is copy and paste - you don't need to know advanced bash scripting or kernel hacking!  And if you make backups before editing configuration files, you're not going to have any problems.  Following the advice of forum members will not destroy your computer, nor will copying and pasting commands into the terminal.

But if you refuse to open a terminal or edit a file - if you simply refuse to leave your newbie comfort zone - then you will probably have to wait some time before your computer works the way you'd like it to.  To customize the OS to make the most of your hardware may well involve some harmless tweaking and tinkering. But if you're afraid to do that, just sit back and wait for a future release that may be perfect "out of the box".  But who knows how long that will be?  Good luck.

---

### Post by Fatigoworld on 2009-09-22
its not fear its ignorance.

i dont know what xorg is let alone how to back it up.  and whenever i read these forums i dont understand anything.  and when i type in commands the same way as shown nothing happens.  

Blackened....if you want to take the time to walk me through this, i will give the terminal one last shot....

---

### Post by blackened on 2009-09-22
> **Fatigoworld said:**
> its not fear its ignorance.

i dont know what xorg is let alone how to back it up.  and whenever i read these forums i dont understand anything.  and when i type in commands the same way as shown nothing happens.

Here is the Wikipedia page for the [X Window System]("http://en.wikipedia.org/wiki/X_Window_System")  

xorg refers to the current implementation of the X Window System (X) that Ubuntu uses. Sometimes people use it as a shorthand way of referring to the file /etc/X11/xorg.conf which is a (now largely obsolete) configuration file that controls aspects of X.

> Blackened....if you want to take the time to walk me through this, i will give the terminal one last shot....

Gladly, we'll start by gathering some information. Plug your external monitor in, then cut and paste this into the terminal, then cut and paste the results from the command back into the body of your next message:
```
xrandr --prop
```

---

### Post by Fatigoworld on 2009-09-22
heres what i got...

Screen 0: minimum 320 x 200, current 800 x 600, maximum 2048 x 768
VGA connected 800x600+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
	EDID_DATA:
		00ffffffffffff000472910074213092
		17130103683c22782a97b5a95438ae25
		13505423080081c0810081408180b300
		0101010101013b3d00a0808021403020
		350055502100001a000000fd00383c1f
		5e14000a202020202020000000fc0041
		636572204232373348550a20000000ff
		004c46423057303033343330300a00fb
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3*    56.2  
   640x480        59.9  
LVDS connected 800x600+0+0 (normal left inverted right x axis y axis) 195mm x 113mm
	EDID_DATA:
		00ffffffffffff0006afc21100000000
		0112010380140b780afa569256549824
		1a4f5400000001010101010101010101
		010101010101781500ae41581e201888
		3100c371000000180000000f00000000
		00000000000000000020000000fe0041
		554f0a202020202020202020000000fe
		004230383941573031205631200a001b
	PANEL_FITTING:	full_aspect
		supported: center       full_aspect  full        
	BACKLIGHT_CONTROL:	combination
		supported: native       legacy       combination  kernel      
	BACKLIGHT: 15625 (0x00003d09)	range:  (0,15625)
   1024x600       60.0 +
   800x600        85.1*    72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1

---

### Post by blackened on 2009-09-22
Ok, do this:
```
xrandr --output VGA --mode 1280x720
```

---

### Post by Fatigoworld on 2009-09-22
wow, that was too easy, thank you thank you thank you!!

ive been converted, ill try to be less wary of the terminal from now on!

---

### Post by blackened on 2009-09-22
Wait, because it gets better. xrandr can control pretty much all aspects of the display. This is especially beneficial for scripting what you want to happen based on events. Say you want your external monitor to automatically set itself to a certain resolution and your laptop screen to turn off when you plug the external in. 

The command to turn off your laptop screen is:
```
xrandr --output LVDS --off
```

If you're interested in just such a script, I have one, written very succinctly by someone else, that I could modify and forward to you.

**EDIT:** I also retract my former statement, you could've changed the mode through the Display Properties dialog (System -> Preferences -> Display) if you had selected the picture of your external monitor, then changed resolution in the dropdown menu. If a resolution shows up in xrandr --prop, then it will also show up in Display Properties.

---

### Post by Fatigoworld on 2009-09-22
that would be great!  do you have a script that will automatically change the resolution when i plug in the external monitor and then change it back on my laptop when i unplug it?  i would prefer to leave the laptop screen on if possible.

---

### Post by Fatigoworld on 2009-09-24
> **blackened said:**
> 

**EDIT:** I also retract my former statement, you could've changed the mode through the Display Properties dialog (System -> Preferences -> Display) if you had selected the picture of your external monitor, then changed resolution in the dropdown menu. If a resolution shows up in xrandr --prop, then it will also show up in Display Properties.

the drop down menu gave me the highest resolution of 800x600, nothing higher.  that was the original problem i had is that it didnt show up in the drop down menu in the display properties.  but thanks for fixing it with the terminal!!

---

