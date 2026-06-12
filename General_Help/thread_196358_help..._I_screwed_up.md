---
title: "help... I screwed up"
date: 2006-06-14
forum: General Help
---

### Post by JonD25 on 2006-06-14
Well, I'm kinda new to Linux and Ubuntu, so please bare with me. I was trying to get xgl/compiz working on my laptop, and somehow, I screwed everything up. I honestly am not sure what to tell you guys to let you know how I screwed it up, but all I know is that when I boot in to Ubuntu, the login screen is just a plain white screen. I can type my username and password blind and it'll act like it's going to log me in, but then there's only the blank background before the wallpaper loads and the top and bottom toolbars completely blank. I can move the mouse around, but that's it. Nothing else does anything. I don't know if anyone can help me out with such a vague amount of information on how I got here, but all I know is that I was trying to get compiz to work with one of the tutorials, and it seemed to work great. I logged in, and it seemed like normal except none of the windows had any borders and they couldn't be moved at all. So after a little bit of trying to figure stuff out, I logged out and back in the default session, tried to figure stuff out more, logged out, and here I am. Any help would be greatly appreciated.

---

### Post by Lunar_Lamp on 2006-06-14
If you want to abandon your xgl setup and just go back to normal X for now, try something along these lines:

 - When you log in hit ctrl+alt+backspace, and you should get kicked out to a text prompt (i.e. no graphics).  It may be that it keeps trying to send you back to the screwed up graphical interface, but if you hit the ctrl+alt+del 6 times in 90seconds I think it gives up and tells you that there is an error.  Alternatively try pressing ctrl+alt+1 to get to a text prompt.

- Login at the prompt with your user/pass

- Now you need to try and undo what you did before.  Hopefully you made some kind of note of any files you edited, or made backups?

- One of the files you are likely to have edited is xorg.conf - you can try to edit it back to it's original state by using the command "sudo nano /etc/X11/xorg.conf".  Use your cursor keys to navigate and then make your changes.  When you are happy hit "ctrl+x" to exit, and press "y" to say you want to save changes and hit enter.

- I think you may have edited gdm by adding info about servers.  You can try to remove this by editing your gdm configuration file:

sudo nano /etc/gdm/gdm.conf-custom

note: don't edit /etc/gdm/gdm.conf - the two files complement each other and you should edit the changes you may have made in the gdm.conf-custom file.

- Try typing "startx" or "gdm" or rebooting to see if your graphics are up and running now.

If you could point us in the direction of any files you may have modified, or if you can even just remember some of the guides you used to get this far.  I have messed up my own system so many times by trying to fiddle with xgl/compiz that I can assure you that you should be ok. :)

---

### Post by JonD25 on 2006-06-14
Well, it seems that whatever I did wasn't actually fatal. I apolgize, but after it screwed up, I shut it down for the night. When I woke up, I checked the thread and started her up to try what you meantioned, and it seems everything is ok now. I even logged in the XGL session and it's working great. Go figure. Any idea why I might have had that problem at the start? Doesn't make much sense to me. Oh well. Thanks for attempting to help. I'll be sure to come back if anything else weird happens.

---

### Post by sarhento_lobo on 2006-06-14
Great to hear that you're running ok now. Would have been nice finding out what could've caused it to act up though. Oh well.

Cheers,
sarhento_lobo

---

