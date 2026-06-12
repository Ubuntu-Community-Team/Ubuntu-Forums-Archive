---
title: "Help! can't login to ubuntu! XDM error"
date: 2009-12-02
forum: General Help
---

### Post by Weepleman on 2009-12-02
Hi, yesterday I uninstalled and then reinstalled gdm because it was logging me out at random.  What happened was when I went to login later All I got was a black screen, but I was able to login through debugging mode with a root prompt.  Sicne gdm was not working, I tried installing kdm.  This allowed me to see a login screen, but would not allow me to get any further.  Here, I could still login through debugging mode.  Then, since I was frustrated I tried installing xdm.  Now all I see is a lot of bars and a barely illegible option menu that all I can do is press enter.  I cannot see what it says, so I do not know hat is going on.  Now, the real problem is that now I cannot even use debugging mode to login through a prompt because I get the screen I cannot read no matter what.  I really like ubuntu and do not want to go back to windows after getting a taste of linux.  Also, I want to avoid reinstalling ubuntu because I don't want to have to reinstall all of my programs.

---

### Post by Weepleman on 2009-12-02
You know, I never realized how much I hate Vista until I tried ubuntu, I thought that was the way all OS's worked!

---

### Post by Weepleman on 2009-12-03
Bump. I really need help with this!!!! Please!

---

### Post by renato.vitolo on 2009-12-03
I had exactly the same problem. I kind of solved it by reconfiguring gdm.
Of course, to do this you need a working root shell, don't you?

Try this: when the GRUB menu appears, edit the 'kernel' line by pressing 'e'
scrolling down and 'e' again (also see  here for more info:
[http://grumpymole.blogspot.com/2007/...arameters.html]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html")
[http://forum.soft32.com/linux/gentoo...ict321907.html]("http://forum.soft32.com/linux/gentoo-Interrupting-boot-sequence-ftopict321907.html"))

Remove everything at the end of that line from the 'ro' onwards and add 'rw init=/bin/bash' instead. Then press 'Enter' and 'b' to boot. This should give you a shell.

From there, do 'dpkg-reconfigure gdm' and select gdm again, then exit and reboot.

In my case, this was not enough. On top of that I had to boot using previous versions of the kernel and fiddle around a lot. I am now using gdm-2.20 (legacy) and the thing works by miracle and I am too scared to touch it again.

This seems to be a weird conflict between the various login managers (gdm, kdm, xdm, I too have them all installed), which seems to leave the X system not working even after rebooting, for some reason which I was unable to identify. In certain cases, the DRM system was not found and X started in a very slow and CPU-consuming fashion. The problem persisted across a few reboots. Then I rebooted with another kernel and the problem was gone. And so on...

I have an AMD 64 system with an Intel VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c). Kernel is
2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux
but I have used other versions in the process like Ubuntu 9.10, kernel 2.6.27-14-generic, Ubuntu 9.10, kernel 2.6.31-14-generic etc.

This is the first time that Ubuntu lets me down and it's not a pleasant one.

Good luck!

---

### Post by renato.vitolo on 2009-12-03
Might be related to more general issues with Intel graphics:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-freeze-test](https://launchpad.net/~ubuntu-x-swat/+archive/x-freeze-test)

---

### Post by Weepleman on 2009-12-03
Ok, I was able to reinstall gdm, and uninstall xdm.  I am able to login and start stuff, but I am back to the mistake I made in the first place.  I forgot, but before I changed to kdm, I picked on of the other options for the login in gdm.  It wasn't X, and it wasn't the X debug, it was the third one, I think it started with an A.  What it did was make it so I do not have a desktop, and I just have a terminal.  I am able to launch graphical applications, so I can live with this, if I have to, but it is really really bad, because I cannot configure things.  Now, when I logout, I do not see the options like X and the thing I chose.  Is there anyway to change back?

---

### Post by renato.vitolo on 2009-12-04
Weepleman,

I find it hard to understand what you are trying to say, but I will give it my best shot.

> 
Ok, I was able to reinstall gdm, and uninstall xdm.
If you have done the 'dpkg-reconfigure gdm' step, you have not uninstalled xdm, you have only de-selected it and selected something else. What did you select? If you are unsure, you can redo this step.

> 
I am able to login and start stuff, but I am back to the mistake I made in the first place. I forgot, but before I changed to kdm, I picked on of the other options for the login in gdm. It wasn't X, and it wasn't the X debug, it was the third one, I think it started with an A. What it did was make it so I do not have a desktop, and I just have a terminal. I am able to launch graphical applications, so I can live with this, if I have to, but it is really really bad, because I cannot configure things. 
My best guess is that you selected "Failsafe" from the list of window managers in the kdm (or gdm) login screen. This is the choice that you wish to alter that, I presume. But I don't understand the next bit:

> 
Now, when I logout, I do not see the options like X and the thing I chose. Is there anyway to change back?
There should be. Are there any buttons on the screen that you get when you log out? Clicking the right buttons should give you the list of window managers, including Failsafe. Just choose another one.

If there are no buttons, redoing the 'dpkg-reconfigure gdm' step might help.

Good luck again!

---

### Post by Weepleman on 2009-12-04
Sorry, I was wrong about uninstalling xdm, I got an error when I tried to do that.  But that's not important.  When I see the login screen, I see a button for keyboard layout, language, ease of access, and things like turning off my computer.  What I don't see, but have see before is the box where I changed the thing that I think starts with an A.  I think it was session manager, but I am not sure.  There is no box for that, and none of the other buttons have any way to get it back.  It is the same for all users on the computer.  I can show you if there is any way to take a screen shot from the login window.

---

### Post by Weepleman on 2009-12-05
Okay, I found out how to start gnome from the command line, so now I am able to use my stuff normally.  What I need now is to run the command ```
gnome-session
``` at start up.  I can't find the System > Preferences > Sessions, so I can't add it there.  Is there anyway to run a command at startup.

---

### Post by renato.vitolo on 2009-12-05
> 
Is there anyway to run a command at startup. 
Yes, there is. 

If you have a file called ".xsessionrc" in your root directory, make a backup copy
of it, e.g.
```
cp .xsessionrc .xsessionrc-backup-2009-12-06
```Then edit it, remove everything and add the single line "gnome-session".
If you don't have the file then just create it.

Regards

---

### Post by Weepleman on 2009-12-06
> **renato.vitolo said:**
> Yes, there is. 

If you have a file called ".xsessionrc" in your root directory, make a backup copy
of it, e.g.
```
cp .xsessionrc .xsessionrc-backup-2009-12-06
```Then edit it, remove everything and add the single line "gnome-session".
If you don't have the file then just create it.

Regards


That didn't work, does that run at boot, or at login?  I think I need it to run at login.

---

### Post by renato.vitolo on 2009-12-06
By "root directory" I meant the root directory of the user you normally login as (e.g. /home/weddelman/.xsessionrc) and not the root directory of the root user (e.g. /root/.xsessionrc). Which one have you chosen?

---

### Post by Weepleman on 2009-12-06
I pu tit in my home folder eg /home/[me]/

---

### Post by renato.vitolo on 2009-12-06
If it still does not work, you might try

```
ln -s .xsession .xinitrc

```and even

```
chmod u+x .xsessionrc

```

---

### Post by Weepleman on 2009-12-07
No, sorry.  Those do not work either.

---

### Post by Weepleman on 2009-12-08
I don't know if this has anything to do with this, but I cannot shut down or reboot my computer.  All I get is a black screen with a mouse cursor.  Is there any way to fix this and/or are they related?

---

### Post by renato.vitolo on 2009-12-15
Do you get the black screen before or after logging out?

I occasionally got a black screen after logging out. You can try Ctrl-Alt-Del in that case, although I think that it did not always work out for me. This problem is not showing up any longer though.

---

### Post by Weepleman on 2009-12-15
When I log out I just see my by background and a cursor just like when I try to shutdown, but I can see my background. Right now I am just unplugging my computer to turn it off. Will this hurt it?

---

### Post by Weepleman on 2009-12-20
I reinstalled Ubuntu and that fixed my problem.  Thank you for all of your help though.

---

