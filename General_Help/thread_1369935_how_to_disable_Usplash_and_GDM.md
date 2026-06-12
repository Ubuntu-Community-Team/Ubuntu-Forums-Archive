---
title: "how to disable Usplash and GDM"
date: 2010-01-01
forum: General Help
---

### Post by warlock85 on 2010-01-01
Hello, I want to disable Usplash in ubuntu 9.10 so that when i boot up there are not graphics and I want to disable a graphical login. So that when it asks me to login it is a text-based login. How would I do this?

---

### Post by Twiggeh on 2010-01-01
Go into synaptic package manager and remove "xsplash" and "gdm" should do the trick, i believe.

---

### Post by Groundswell on 2010-01-01
i can't remember the file you have to edit, but there's one somewhere in /boot that you can switch usplash to quiet. but there also some thing called startup manager that may do it for you, and might even get rid of your graphical login for you.

here  [http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html](http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html)

---

### Post by Groundswell on 2010-01-01
this got me curious and i checked it out, it won't do anything editing your grub files won't do, but it makes it easier i guess, but it won't get rid of your graphical login.

i'm not sure how to do this by default, but you could do a work-around. like set booting into command prompt to be defualt. so it boots to terminal asking you to log in. log in once you get there. and either type "sudo /etc/init.d/gdm start" or make a script so you can just type something simple. like "sudo bootgui"  

you could also just do automatic login, which would make more sense. thats what i have set and it just boots straight to my desktop. for me the sooner it gets there the better cause my graphics cards fans sound like a freakin jet takin off till the drivers kick in.

---

### Post by warlock85 on 2010-01-01
I tryed to remove xsplash with synaptic and it keeps on trying to remove ubuntu desktop instead of xsplash. The same thing is happening with GDM

---

### Post by john newbuntu on 2010-01-01
Here's a workaround you could try.  I have to admit it is risky and I have not tried it myself since I use gnome.
If you use Karmic, remove 'splash' from the kernel command line in /etc/default/grub and run "sudo update-grub2".  If non-karmic, make the change to menu.lst to remove #splash 

Next, the risky part, MOVE the file /etc/init/gdm.conf to say, your home directory or some other place and reboot.  My guess is that upstart will now skip gdm and start other daemons normally.
Now, should something bad happen and the startup is not as expected, restore the gdm.conf file from a recovery mode to its original location with permission 544 and owned by root (group root) and reboot.

---

