---
title: "Stuck at login screen 10.04"
date: 2010-05-01
forum: General Help
---

### Post by blademeld on 2010-05-01
As you can see I'm new to the forums, so I'm not aware of all the etiquette and such. I have for the past day or so been searching for the solution to my problem and was unable to locate a similar problem on the forums, so here I am, asking for help. If there's a better location for the topic to be in or if this is a redundant thread, please relocate or provide a link to the said thread.

My problem actually started when I upgraded from Jaunty to Karmic back when Karmic came out. I was unable to log into a GNOME session, however, I was able to log into failsafe GNOME and I was content. When Lucid came out, I updated immediately, hoping that this upgrade would solve my issue, to my dismay, it worsened it, I am currently unable to even use failsafe mode.

The symptom is that when I boot the computer, I am able to get to the login page, however, when I type in the correct password, it goes through the TTYS and goes back to the login page. I am able to log in through the terminal at TTYS 1-6, however, I am unable to use the GUI. When the wrong password is typed in, it tells me that I have a wrong password in it. Switching over to KDM seems to do something, and I was advised on IRC that it is most likely a GDM error.

Here is the result of the GDM log: [http://pastebin.com/XgPUrTxj](http://pastebin.com/XgPUrTxj)

Thanks and regards,
Steve

---

### Post by fireworld2406 on 2010-05-02
Hi!

I had the same problem as you, and this is how I fixed it.

**Part 1**
First, choose the "recovery" option at the grub boot menu. Then, choose the "root" option and press enter.

Now, if you are able to see console text at this point, you can continue to part 2 below; otherwise, continue here!

Type "clear" and press enter. This should get you some console text. Now, type in "nano /etc/default/grub" and press enter. In the file, type in the following two lines (without the quotes!) "GRUB_GFXMODE=800x600" [you can switch that to a different resolution, if you want] and "GRUB_GFXPAYLOAD_LINUX=keep". This will set the console to a normal resolution. Restart the computer, choose the "recovery" option again, and continue with part 2 below.

**Part 2**
At the recovery menu, choose the "root" option and press enter. Type "Xorg -configure" and press enter. It will tell you where the new file was placed. Then, type in "cp <location of file from the Xorg -configure> /etc/X11/xorg.conf". Finally, restart the computer, start Ubuntu normally, and it should hopefully work!

Good luck!

---

### Post by blademeld on 2010-05-06
Hi there,

thanks for the help, however, I'm almost certain it's not an issue with the xorg.conf file, I'd replaced that before coming here.

The reason my reply is late is that I'm a complete Ubuntu noob and this experience has forced me to work with shell for a while and it was rather interesting.

Thanks,
Steve.

---

### Post by Raditude on 2010-06-27
I'm having the same problem. I tried the xorg replacement idea that fireworld suggested, but it didn't work.

---

