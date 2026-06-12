---
title: "Ubuntu LiveCd Help"
date: 2011-05-10
forum: General Help
---

### Post by WMUK on 2011-05-10
When booting from the LiveCd it starts to load but never loads! All it does is flash a _ icon and then becomes black! Help!

---

### Post by WMUK on 2011-05-10
Please Help!

---

### Post by Ghost|BTFH on 2011-05-10
And your screen turns off?

And you're running an older nVidia graphics card?

And you didn't start the CD using F6 and selecting nomodeset?

Just FYI, after installing, you HAVE to reboot with the LiveCD and edit your /boot/grub/grub.cfg.

You'll have to remove the **quiet splash** and insert **nomodeset** in its place.  This will allow you to boot up with graphics...after that, install the restricted drivers and reboot.

From that point on, update at will and you should be fine.

This is the mother of all assumptions - if this is not your setup, please let us know what you're running for hardware.

Cheers,
Ghost|BTFH

---

### Post by WMUK on 2011-05-10
I have never even gotten to that part yet! I press F12 and click boot from CD drive!

---

### Post by Ghost|BTFH on 2011-05-10
Boot from CD drive, spam F6 until the options screen pops up.

Hopefully this will resolve your issue.

Cheers,
Ghost|BTFH

PS: You didn't answer my question on your hardware... :)

---

### Post by WMUK on 2011-05-11
I don't have grub.cfg!!!!!

---

### Post by Ghost|BTFH on 2011-05-11
Sorry, that was completely my bad.

You must mount your / partition while you have the LiveCD running.  It will be mounted under /media with the UUID of the drive...

So the correct location would be /media/(whatever the uuid designation is)/boot/grub/grub.cfg

The easiest way to edit it (in my opinion) is to ```
gksudo gedit /location/of/file/goes/here
```

Cheers,
Ghost|BTFH

---

### Post by WMUK on 2011-05-12
Huh? I don't understand. I'm new to this kind of stuff. Will you give me some steps, please?

---

### Post by Ghost|BTFH on 2011-05-12
Hmmm...I thought I did.

1) Insert Ubuntu LiveCD
2) Try Ubuntu (Not Install) - I'd suggest using 10.10 - easier to access the parts you'll need.
3) If you click on Places in the upper left-hand area, you should see 1 or more drives (depending on how your actual hard drive is partitioned) and you will need to mount the boot partition (generally referred to as / or "root directory") which can be done by simply clicking on it.
4) After it has mounted, open a terminal (found under Applications - > Accessories) and type in:

```
cd /media/(hit tab and it should fill in the newly mounted drive's UUID here)/boot/grub/
``` and hit enter.

5) Next, you'll need to edit the grub.cfg that is found in said directory (that you should now be inside of) which you can do easily by typing:

```
gksudo gedit grub.cfg
```

6) You will have to search through the code to find a section near the end of one of the lines that says **quiet splash** and you will need to remove those two words and then insert ```
nomodeset
``` in their place.

7) Save the file.

8) Shut down the system and restart without the LiveCD.

9) ???

10) Profit!

---

### Post by WMUK on 2011-05-13
Step #2 won't pop up!!

---

### Post by Ghost|BTFH on 2011-05-13
You gotta use the steps I said earlier to get Ubuntu to boot.  ie, the spamming the F6 key, hit F6 and select the nomodeset option for boot...

You also have to then read what it says which is to hit CTRL+X to boot with the options.

~Ghost

---

