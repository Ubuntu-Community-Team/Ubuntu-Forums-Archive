---
title: "Cant boot up ubuntu"
date: 2009-11-04
forum: General Help
---

### Post by Richardarkless on 2009-11-04
Hi I tried to unmount a device and it failed to unmount so I unplugged it and it was still showing up as connected so I tried to unmount it again and it successfully unmounted, thing was when I plugged it back in it wasnt picking it up.

I tried to shutdown and it froze there and wouldnt power off, all that was showing was a blinking cursor in the top left of the screen so I held the power button down, now when I boot up all that comes up is that blinking cursor after the usplash screen went.

I tried booting in recovery mode and nothing comes up just a black screen, please help me fix this problem as I dont fancy reinstalling everything

---

### Post by P4man on 2009-11-04
First of all, memorise one of these:
Raising Elephants Is So Utterly Boring 
or
Reboot Even If System Utterly Broken.

Im not joking. If you type that slowly while holding down alt+printscreen your system will do a save reboot, even when its non responsive. (if you want shut down instead of reboot replace the last B with an O). More info here:
[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

But thats for future reference, to avoid filesystem errors if you have to force a shut down or reboot.

As for your problem now, its very worrysome a recovery console wouldnt show anything, not even an error? Have you tried booting from a live CD to see if you can still mount the harddrive?

---

### Post by Richardarkless on 2009-11-04
Ok that fixes the problem with shutting down but what about when I start it up, when it starts up first the usplash screen comes up and then nothing just a white flashing cursor in the top left.

And when I try the recovery option in grub, after I hit enter nothing comes up just a black screen

Sorry if I sound angry in any way, im just desperate to get back into ubuntu.

---

### Post by P4man on 2009-11-04
What do you mean by "recovery option in grub?" You mean selecting Ubuntu kernel balablabla (recovery mode) ? Or grubs recovery? i mean the first, in the list of operating systems and kernels, selecting ubuntu recovery mode. 

The second option in this screen:
[http://images.howtoforge.com/images/unetbootin_windows_linux/big/36.png](http://images.howtoforge.com/images/unetbootin_windows_linux/big/36.png)

If that brings up a black screen and nothing else, you need a live cd and find out if your drive is still accessible and readable.

---

### Post by Richardarkless on 2009-11-04
yes I mean ubuntu kernel etc, I selected that in grub then nothing just a black screen

What should I do?

it is still readable as I am dual booting with windows vista and im using it right now

---

### Post by P4man on 2009-11-04
Like I said already.. you need a liveCD and boot from it. And prepare yourself mentally for the worst. Once in the liveCD session see if you can mount the harddrive, check it for errors. Check your log files.

---

### Post by P4man on 2009-11-04
> **Richardarkless said:**
> 
it is still readable as I am dual booting with windows vista and im using it right now

You can read your linux partition from vista? Is this a wubi install? Or are you using some Ext driver.. please help us  help you and be a bit more verbose.

---

### Post by Richardarkless on 2009-11-04
yea I got that ext driver that allows me to read the partition but I cant write to it. Its always been like that so I know it aint the problem

---

### Post by P4man on 2009-11-04
well like I already suggested, check your log files
/var/log/messages
it might shed some light.

I would also strongly recommend a filesystem check, but you'll need a live cd for that, as I cant imagine dong that from windows.

---

### Post by Richardarkless on 2009-11-04
> **P4man said:**
> well like I already suggested, check your log files
/var/log/messages
it might shed some light.

I would also strongly recommend a filesystem check, but you'll need a live cd for that, as I cant imagine dong that from windows.

below is the /var/log/messages file, hope you can see what is wrong, um i did a file system check under disk utility and it said it aint clean, how do I clean it

I had a look under gparted and there is a check option, will this check the partition and fix any problems or will it do something else

EDIT: i checked the file system under gparted and it repaired some stuff now it boots :D.

Bit slow but im sure after a few reboots it will go back to its normal self

Thanks P4man for all your help

---

