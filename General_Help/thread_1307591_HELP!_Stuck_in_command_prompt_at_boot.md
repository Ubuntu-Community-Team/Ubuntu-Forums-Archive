---
title: "HELP! Stuck in command prompt at boot"
date: 2009-10-31
forum: General Help
---

### Post by Martin_sensei on 2009-10-31
I have just installed Ubuntu 9.10 from fresh on a blank formatted partition.  The installation seemed to go well, but after rebooting I get a black screen with:

Ubuntu 9.10 martin-desktop tty1
martin-desktop login:

But the screen flickers very badly and keystokes are lost so I can't type in my password to log in.

---

### Post by doubtful wisdom on 2009-10-31
I have very similar problem and found your post while searching for help.  However, my display is stable and I log on, then enter password but still have only the command prompt.  Entering startx takes me to another bootup sequence (a gui one) and I must login again.  I am then in a gui environment.  Takes quite a while to get there.  I also would like to know how to directly boot up in a gui environment (with Karmic) and faster, please.  Boot is really quite slow.

---

### Post by Martin_sensei on 2009-11-01
Hello all,

Well this may not be too helpful, but I solved all my problems by formatting the partition and starting again.

This time I installed Ubuntu without booting to a live session.  GUI started straight away, then I installed the proprietary drivers though the GUI as normal.

Such a different experience the second time round...

Has anyone else experienced problems after installing from a lice CD session?

Cheers

Martin

---

### Post by hal8000 on 2009-11-01
> **doubtful wisdom said:**
> I have very similar problem and found your post while searching for help.  However, my display is stable and I log on, then enter password but still have only the command prompt.  Entering startx takes me to another bootup sequence (a gui one) and I must login again.  I am then in a gui environment.  Takes quite a while to get there.  I also would like to know how to directly boot up in a gui environment (with Karmic) and faster, please.  Boot is really quite slow.


I have just installed Karmic and also found boot time increased to 1 min 5 seconds; a little disappointing as With Hardy it was just 18 secs.

The normal boot process takes you to a particular run level (init 2) with ubuntu then after starting a number of tasks starts gdm the gnome display manager.
However, there seem to be many changes and there is no /etc/inittab in Karmic.
One thing you can try is use synaptic and install bootchart, you will find
an image of the boot process in /var/log/bootchart 
I have just done this and found many more services than Hardy, so as yet will be using google (and the ubuntu forum) to streamline my boot.

---

### Post by realmrealm on 2009-11-01
I also am having the issue but have found something interesting. After it comes to the text-based login prompt.

If I don't do anything after 90 seconds (approx.) the gui login comes up on its own.

Very strange. I can definitely say that it was not doing this when right away after installing ubuntu. It took a few reboots and updates before this happened.

I initially had installed 9.10RC 64bit. It is fully updated, and everything else seems to be ok.

help please.

-AndyS-

---

