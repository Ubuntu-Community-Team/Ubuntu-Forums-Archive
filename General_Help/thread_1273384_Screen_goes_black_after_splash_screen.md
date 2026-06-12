---
title: "Screen goes black after splash screen"
date: 2009-09-23
forum: General Help
---

### Post by harecanada on 2009-09-23
After spalsh screen does it's thing, my monitor goes black and I can't do anything. I have been all over the net trying to get this figured out with no luck. I have tried a lot of things to get it resolved but no luck. Can anyone give me a hand? I am able to run the Live CD for 9.04 but I don't know where to go from here. Anyone up for helping me debug this? I thought it was my monitor but I eliminated that idea. I then thought it was my graphics card and I'm still not sure about that yet. Any help is appreciated.
harecanada

---

### Post by SteveDee on 2009-09-23
You may have a boot problem covered by this post: [http://ubuntuforums.org/showthread.php?t=1203368](http://ubuntuforums.org/showthread.php?t=1203368)

---

### Post by harecanada on 2009-09-23
SteveDee:  This sounds promising, but I don't have the skill to know how to apply these steps. I'm too much of a noob to proceed. Is there a more of a step by step somewhere?
harecanada

Thanks by the way

---

### Post by IsmailBhai on 2009-09-23
> **harecanada said:**
> SteveDee:  This sounds promising, but I don't have the skill to know how to apply these steps. I'm too much of a noob to proceed. Is there a more of a step by step somewhere?
harecanada

Thanks by the way

I think you migt have an X problem.  If you don't feel comfortable reinstalling xorg, I would just reinstall Ubuntu with the live CD, make sure you make a backup of everything using the live CD.

---

### Post by SteveDee on 2009-09-23
Yeah, without knowing what happened just before this became an issue, it is a bit difficult to advise. As you can apparently run Ubuntu from the LiveCD it looks like your hardware (including monitor & graphic card) is probably OK.

If you can identify all your files it may be easiest to run from the LiveCD and save all your files to a memory stick, then reinstall Ubuntu.

Did you make any changes to your computer just before things went bad?

---

### Post by harecanada on 2009-09-23
Thanks for the help.
How do I make backups using the Live CD?
I wouldn't mind attempting to repair or reinstall xorg. I just don't want to lose my data if possible. 
This whole problem started out of the blue. I turned my monitor of one night and the next day the power light(on the monitor) was blinking and I couldn't turn it off or on and the screen was black. I thought it was the monitor but it worked fine in another computer. Then I thought it was the graphics card but the Live CD works fine so that's what has led to the confusion. 
harecanada

---

### Post by SteveDee on 2009-09-24
To back up your files you could boot from the LiveCD and connect an external memory device (e.g. USB drive, memory stick) large enough to save your files. Then go to Places > Computer and select the computers internal hard drive. Navigate to the /home/{yourname} folder on the internal hard drive and copy the contents to your external memory device.

However, you could try 2 other options with your xorg.conf file;

1). Using LiveCD go to your internal hard drive and navigate to /etc/X11 and copy the xorg.conf file. Then post it here and see if anyone can work out what is wrong with it.

2) Again using the LiveCD, rename the xorg.conf file on your hard drive at /etc/X11 to something like "xorg.conf.bad" then copy the xorg.conf from the LiveCD (i.e. from LiveCD desktop go direct to Places > File System and navigate to /etc/X11). Put this file in the hard drive's /etc/X11 folder, then remove LiveCD and reboot.

Good luck!

---

### Post by harecanada on 2009-09-24
Hey SteveDee,
I want to try these options but I'm confused. There are 8 different xorg files in X11. Which one do I use?
harecanada

---

### Post by SteveDee on 2009-09-25
> **harecanada said:**
> Hey SteveDee,
I want to try these options but I'm confused. There are 8 different xorg files in X11. Which one do I use?
harecanada

There should only be one "xorg.conf" file in /etc/X11 but on your computers hard disk you may also have config files that have been saved with modified names as your computer has been updated. Examples on my hard drive include:-
xorg.conf.dist-upgrade-200811080741
xorg.conf.dist-upgrade-200904271957

...hey, in fact you could try using the most recent version of one of these files.

So what you would do is rename the current xorg.conf in /etc/X11 on your hard disk to "xorg.conf.bad". Then copy your most recent file (e.g. xorg.conf.dist-upgrade-200904271957 in my case) to your desktop, rename it "xorg.conf", then copy it back to /etc/X11 on your hard drive.

That way you will still have copies of all your xorg.conf files.

I hope that makes sense.

---

### Post by rreese6 on 2009-09-25
The copy and replace idea is very good, but I think he may need step by step..

I will attempt this

fist open up terminal
at the prompt type:
```
cd /etc/X11
ls -l xorg* 
```
the last command will show you the various xorg files you have.
the one we are interested in is called xorg.conf, so
```
sudo mv xorg.conf xorg.conf.bad
```
You will need to type in your password to make the command complete. the password is the same as the one you log-in with.
This will move (copy and delete old file) your current Xorg Configuration to a file named "xorg.conf.bad" (always good to backup stuff before modifying)

Looking at the list of files you got when you did "ls -l xorg*"
you will see different dates for the files. pick the one that is around a date when everything worked right. 
Lets assume for this demonstration that the file is called "xorg.conf.backup" and it;s timestamp (date etc) is older than the date of xorg.conf..
Now we will copy that file to make a "new" xorg.conf:
```
sudo cp xorg.conf.backup xorg.conf
then
ls -l xorg*
```

Make sure that xorg.conf is listed. once that is done
```
sudo reboot
```

Hope that helps...

---

### Post by harecanada on 2009-09-25
rreese6 Thanks for the idea. I'm using the Live CD though and when I use this command 
cd /etc/X11
ls -l xorg*
I get the xorg list from the cd

ubuntu@ubuntu:/etc/X11$ ls -l xorg*
-rw-r--r-- 1 root root 1037 2009-09-25 21:09 xorg.conf
-rw-r--r-- 1 root root    0 2009-09-25 21:09 xorg.conf.20090925210936

How would I do that from the hard drive?
harecanada

---

### Post by harecanada on 2009-09-25
SteveDee
 I tried to do the replacement and I can copy to the Desktop but I can't copy back to the X11 file. I get an error. The error is " opening media/etc/X!! file Permission Denied" something close to that. That must mean I have to go through the terminal as sudo but I don't know how to do that.
harecanada

---

### Post by SteveDee on 2009-09-26
> **harecanada said:**
> SteveDee
 I tried to do the replacement and I can copy to the Desktop but I can't copy back to the X11 file. I get an error. The error is " opening media/etc/X!! file Permission Denied" something close to that. That must mean I have to go through the terminal as sudo but I don't know how to do that.
harecanada

I'm not sure if you got the "permission denied" type message while trying to rename your xorg.conf.{whatever} file to xorg.conf, or when you tried to copy it back to /etc/X11. But either way you can get around these problems using sudo. I'm lazy, so will always try to use a GUI interface where possible, even if it means launching it from a terminal.

Using the LiveCD you can open a terminal and type:-
sudo nautilus
..you won't be asked for a password, so your file manager (nautilus) should now open.

***Now be very careful!*** Your file manager is now even more dangerous than the MS Windows file manager, as you can delete just about anything!

Navigate to the xorg file on the LiveCD desktop, rename it if necessary to xorg.conf, now copy it back to the hard disk /etc/X11 directory.

Close nautilus (and wipe the mouse to remove your finger prints! :))

Now see if your machine will reboot from the hard drive.

---

### Post by harecanada on 2009-09-26
Hi SteveDee,
I finally got the guy that got me into Linux a number of years ago to come by and he said your idea of replacing the xorg file was what he would have done. I wanted him to check out my video card and see if it was causing a problem also and sure enough it was. Ever since I got this computer, there was a constant noise of a fan starting and stopping every few minutes. It turned out that that card (Radeon 2600) was faulty. However, I have an onboard nvidia 6500se. So we pulled the Radeon and used the onboard and it's perfect. I couldn't have done it without your help so thanks again. I starting an online business and needed my computer to work flawlessly and it does now. Actually, removing that card made it boot faster and cleaner too.
harecanada

---

