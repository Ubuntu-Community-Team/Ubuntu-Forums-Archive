---
title: "Failed Install of 12.04"
date: 2012-05-02
forum: General Help
---

### Post by ddjolley on 2012-05-02
I posted this problem yesterday under the topic of "Video Mode Not Supported".  I got no responses.  I'm getting a bit desperate.

Basically the issue is this:  The computer involved is an HP s7727c desktop PC.  It runs the Ubuntu 12.04 (32 bit) live CD just fine.  It also has been running Ubuntu 11.10 just fine since it came out.  After installing 12.04 to the hard drive I get a "Video Mode Not Supported" error during the boot process.  What happens after that is a bit unpredictable.  Yesterday I was getting a follow-on error message at the console.  Today, I'm getting a login prompt at the console.  I'm actually able to log in using the credentials that I supplied during the installation. 

I would think that if there were some sort of hardware incomparability, I would not be able to run from the live CD.  I realize that video is a big issue with Unity; but, I was running Unity just fine under 11.10 and also from the live 12.04 CD.

I really need some help on this one.

Thanks.

         ... doug

---

### Post by jerrrys on 2012-05-02
Its 10o4 but I think check this out

[ATTACH]217125[/ATTACH]

found it here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=HP+s7727c+desktop+PC+video+mode&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=HP+s7727c+desktop+PC+video+mode&sa=Search&cof=FORID:9)

---

### Post by ddjolley on 2012-05-02
Thanks, jerrys.  You're post pointed me in the right direction so that I was able to solve the problem (kindof).  I'm going to document the fix for others:

You need to be root to do this.  Open /etc/default/grub in a text editor.  Locate the line that reads:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Edit that line so that it reads:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

After the edit has been made save the file.

Finally, as root at the command prompt issue the command:

update-grub

That seems to fix things so that I boot into the GUI.  There still are problems in that the Video-Mode-Not-Supported notice is still displayed momentarily; but, the boot process continues despite the notice and I wind up in the GUI.  My screen seems to be shifted a bit too the left.  I may be able to fix that with an adjustment to the monitor.  Anyway, I'm considering this a real good work-around (if not a fix).  I'm marking the problem solved.  Thanks for the help.

          ... doug

---

### Post by ddjolley on 2012-05-04
Hold on.  I'm not sure that this is a viable solution..

It seems that the effect of adding 'nomodeset' to the string value of GRUB_CMDLINE_LINUX_DEFAULT is to force operation in 2d mode.  That strongly suggests that, due to some change that occurred between 11.10 and 12.04, my hardware is no longer compatible.  (Recall that I was running 11.10 in 3d mode just fine.)  However, the fact remains that I am able to run 12.04 in 3d mode from the live CD just fine.  Therefore, I conclude that my hardware is capable of running 12.04 in 3d mode.  So why does it work from the live CD and not the hard drive?  That is the question.  BTW, in case anyone is wondering how I know what mode I am running in, I test the value of the $DESKTOP_SESSION environment variable.

Any thoughts?  I'm thinking that we are dealing with a bug of some sort.

Thanks.

         ... doug

---

