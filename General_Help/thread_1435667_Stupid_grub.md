---
title: "Stupid grub"
date: 2010-03-21
forum: General Help
---

### Post by JigglyWiggly_ on 2010-03-21
Ok so I installed XP after partioning Ubuntu... (shrank it)


Then this is a 9.04 to 9.10 upgraded install, so it has grub1


I have never recovered a grub1 install, only grub2...

Anyway . Type "grub"

I did grub in the terminal(I instlaled the old grub on the live cd and removed grub-pc)

Then I did
root(hd2,0) < That is where it located it
setup (hd2)

And it said success, I reboot, it's not there! It goes into to stupid Windows... 


I would even try installing grub2 from it, but it doesn't work...?

I don't remember the error but when I did

sudo grub-install /dev/sdc it yanks out stupid errors... saying something about use modules explicitly and something about /boot/grub


EDIT: here is what happens after grub-install /dev/sdc 

grub-probe: error: cannot find a device for /boot/grub.

No path or device is speicifed.
Try ''grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specifify the module with the option '--modules' explicitly.

This is trying to install grub2.

---

### Post by darolu on 2010-03-21
Did you run?:
```
grub>find /boot/grub/stage1
```
You have to make sure you are installing it in the right partition.
Also (and considering grub is installed in hd2,0) change the items:
```
grub>root(hd2,0)
grub>setup (hd2)
```
to
```
grub>root (hd2,0)
grub>setup (hd2,0)
```
Note the space between **root** and **(hd2,0)**

If you want to install GRUB2, please post what exactly the "stupid errors" are.

---

### Post by JigglyWiggly_ on 2010-03-21
For anyone else who has problems
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


You know where it says this?
```
sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda

```

Well do that, except don't do it by default on ubuntu 9.10

first do apt-get remove grub-pc
and then do apt-get install grub

Then run that command, otherwise you will be sent to a shell prompt at start...

Glad to have got it working myself :P

---

### Post by JigglyWiggly_ on 2010-03-21
> **darolu said:**
> Did you run?:
```
grub>find /boot/grub/stage1
```
You have to make sure you are installing it in the right partition.
Also (and considering grub is installed in hd2,0) change the items:
```
grub>root(hd2,0)
grub>setup (hd2)
```
to
```
grub>root (hd2,0)
grub>setup (hd2,0)
```
Note the space between **root** and **(hd2,0)**

If you want to install GRUB2, please post what exactly the "stupid errors" are.

I did post the error in the EDIT, but thanks for the reply. Didn't get to test it out.

---

### Post by JigglyWiggly_ on 2010-03-21
Actually my grub is still screwd up, when I purged grub2, and then I reinstalled it, there was something in the options that said quiet boot I unmarked that now when I start up it's full of spam. And then I removed grub2 again and just put the old grub, but I can't get to the select screen, it never pops up. And that jargon still pops up on screen.

Also when I do update-grub it doesn't find Windows... any ideas? (grub1 or grub2)

---

### Post by JigglyWiggly_ on 2010-03-21
Moar confusion, ok what is going on...

I did apt-get remove grub-pc
and apt-get remove grub2

I hold shift when it's booting, it loaded grub 1.97, that's grub2... I have installed grub1, why is it loading grub2, and not 1?

---

### Post by JigglyWiggly_ on 2010-03-21
Ok I decided to do something dumb, I deleted the grub folder backed it up... then I decided to do grub-configure it generated some files, I reboot and I get put to a grub rescue shell


...
Seriously, why is this so hard to just get the boot loader working normally???

---

### Post by lidex on 2010-03-21
> **JigglyWiggly_ said:**
> Ok I decided to do something dumb, I deleted the grub folder backed it up... then I decided to do grub-configure it generated some files, I reboot and I get put to a grub rescue shell


...
Seriously, why is this so hard to just get the boot loader working normally???

Because you keep switching it around. If you want grub legacy go to this section: "Uninstalling GRUB 2/Reverting to GRUB Legacy" of this page;
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by JigglyWiggly_ on 2010-03-21
What I was trying to do was have either grub or grub2, whatever worked.

Well I just reformatted, and I wanted to shoot the pc again after it didn't see my main hd. I then realized I had this problem before and I could just go to another older version of Ubuntu to see it, but I saw some helpful lads found dmraid to be the problem, uninstalled works great(uninstalled on the livecd before commencing the install).

Grub2 sees both windows and Linux... finally.

---

