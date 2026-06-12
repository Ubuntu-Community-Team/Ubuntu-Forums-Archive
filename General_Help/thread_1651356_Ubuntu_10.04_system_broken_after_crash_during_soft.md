---
title: "Ubuntu 10.04 system broken after crash during software upgrade"
date: 2010-12-23
forum: General Help
---

### Post by ehsanul_g3 on 2010-12-23
I did a ```
sudo apt-get upgrade
``` and went to bed after it started. I awoke to my laptop stuck, with the caps lock/num lock LEDs blinking. It's not clear whether the upgrade was finished before this crash.

Note that this type of crash has happened a couple times before in the last few days, but restarting the laptop did the trick then. But, perhaps because this time was in the middle of an upgrade, something has gone really wrong with Ubuntu:


[LIST=1]
[*]First of all, it will not accept input from the keyboard/touchpad/mouse. However, when I unplug the USB mouse and plug it back in, it does suddenly work (if that's a clue). It seems like the keyboard/touchpad may not even be recognized, along with the wifi card (the network connections applet had no options related to wifi, as it usually does).
[*]I can log in by enabling the on-screen keyboard. However, this doesn't play well with gksudo, so when I try to run Synaptic or any other system administration utilities, I can't go past the password dialog. The on-screen keyboard just doesn't work then.
[*]It seems the default window manager that comes with Gnome is gone. I got a message to that effect, when I tried using my "Show Desktop" button. So when my terminal covered up the on-screen keyboard, in it's default position, I'm left helpless to run any commands. Just realized I could try opening the on-screen keyboard after, so it's on top. Will give that a shot next.
[*]Something's wrong with my nVidia driver too, not sure if that was being upgraded, but I would think not. I'm guessing a lot of other things are also messed up.
[*]Using the recovery option before the kernel boots up just leaves the system stuck after the fsck.
[/LIST]
I have no idea how I can recover this system. I haven't got a backup of it. I do have another Ubuntu installation on the same laptop which is working fine, so I can manipulate the filesystem of my other installation from here.

Ubuntu Version: 10.04
Kernel Version: 2.6.28-19-generic
What other information could be useful here?

---

### Post by akand074 on 2010-12-23
I don't know if you have a separate "/home" partition but I recommend it because if you do, you can do a clean install and be back up and running like you were the night before in a matter of as little as 20 minutes. Finding the reasons for that many issues, and then figuring out how to fix all of them would likely take longer than even doing a full backup a full clean install and reconfiguring your system to your own settings. That's just what I would have done, unless I'm feeling curious and adventurous.

---

### Post by garvinrick4 on 2010-12-23
If you can give me your linux install sda# I will give you some code to
try to get install back in shape: this will give you sda#'s
```
sudo fdisk -l
``` (lower case L)
Can do it from your other install as you stated.

---

### Post by ehsanul_g3 on 2010-12-23
> **akand074 said:**
> I don't know if you have a separate "/home" partition but I recommend it because if you do, you can do a clean install and be back up and running like you were the night before in a matter of as little as 20 minutes. Finding the reasons for that many issues, and then figuring out how to fix all of them would likely take longer than even doing a full backup a full clean install and reconfiguring your system to your own settings. That's just what I would have done, unless I'm feeling curious and adventurous.

That's definitely an idea, but what I'm really looking for is saving all the work I've done on the installed system itself. I've had it for more than a couple years, and I program a lot so I've got so much stuff installed and configured and all working. The task of doing all that again, and even finding all the resources to tackle all the sorts of problems you can come up against seems pretty huge itself. So yeah, I was just hoping to avoid that, even if it means some equally tedious work with recovery.

> **garvinrick4 said:**
> If you can give me your linux install sda# I will give you some code to
try to get install back in shape: this will give you sda#'s
```
sudo fdisk -l
``` (lower case L)
Can do it from your other install as you stated.

Sure, it's sda1. You can just assume I can fill in minor details like that, since I do some (basic) sysadmin stuff at work and am familiar with things like that. But I'm obviously no expert. :)

---

### Post by garvinrick4 on 2010-12-23
In live cd with internet connection:
```

[CODE]sudo mount /dev/sda1 /mnt
```
```
sudo mount -o bind /dev /mnt/dev
```
```
sudo mount -o bind /dev/pts /mnt/dev/pts
```
```
sudo mount -o bind /proc /mnt/proc
```
```
sudo mount -o bind /sys /mnt/sys
```
```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```
```
sudo chroot /mnt
```
```
dpkg --configure -a
```
```
apt-get install aptitude
```
```
aptitude update && aptitude safe-upgrade
```
```
dpkg --configure -a
```
```
update-grub
```
```
exit
```
```
sudo umount /mnt/dev/pts
```
```
sudo umount /mnt/dev
```
```
sudo umount /mnt/proc
```
```
sudo umount /mnt/sys
```
```
sudo umount /mnt
```
```
sudo reboot
```
[/code]

---

### Post by ehsanul_g3 on 2010-12-23
Thanks garvinrick4! I'll try this as soon as I can get a LiveCD burned.

I suppose I can't really do this from my other system without potentially causing some issues?

---

### Post by garvinrick4 on 2010-12-23
> **ehsanul_g3 said:**
> Thanks garvinrick4! I'll try this as soon as I can get a LiveCD burned.

I suppose I can't really do this from my other system without potentially causing some issues?
If you want to use the other linux install will not harm anything at all. Leave out the'
update-grub command and do it after booting and all is fine. I update and upgrade
my installs with chroot command all the time from one install, saves rebooting all the time.
The update-grub would make a new grub-config file for that install is all, you use the other
linux install to boot with anyway. The dpkg --configure -a resolves unsettled dependencies 
and if upgrade stopped in middle would maybe get it going in right direction again. The 
/etc/resolv.conf line just copies the internet to the your /mnt install so it can get online.
I like aptitude safe-upgrade and the rest just unmounts all the things /dev /dev/pts /proc and /sys
that we mounted to go with /dev/sda1 /mnt  Give it a go partner. Have a Merry Christmas
Let me no how she did.

---

### Post by chirojoseph on 2010-12-25
JHEEEELPPP

just had the exact same problem folks.
Im completely newb...but i HAD LUBUNTU working perfectly on a new eeepc  1018 pem...PERFECTLY..

and then I did the recommended upgrades which id been putting off cause i didnt want to "rock the boat" and sure enough we download upwards of 70 files...begin updating...she freezes up...I reboot..now it gives the option screen of "recovery mode boot, normal boot, and memory tests"

and if we choose RECOVERY boot it freezes up after showing the line-text "skipping EDID probe due to cached edid"

and i have to hard reboot again...if we choose Normal Lubuntu bootup the desktop comes up but KEYBOARD AND TOUCHPAD COMPLETELY DISABLED...

only the function keys for display brightness seem to work. CntrlAlt F1 does NOT get me a terminal..i cannot get terminal. nothing works.

GOD I was just getting comfy with the damn thing...i was WORRIED about the horror stories of alowing synaptic to upgrade...WTF?? Now what? Do I have to reload ubuntu on my usb drive and try to boot from the USB to be able to get into my system_? I

Is it most likely that it didnt load allthe dependencies it needed and just the drivers are blocked or has this totally fobbed everything? looks like this may be happening to alot of people with hte recent upgrades...just in time for new years party..arrgghhh..im supposed to be DJ WITH THIS netbook in a few dayz..

hopefully i can get a little help PUUULeease...i dont know where to start if I cant even move cursor!

---

### Post by chirojoseph on 2010-12-27
ALL fixed using external USB keyboard and mouse. Luckily they were both recognized. I was desperately trying to see if the virtual keyboard was already installed with the LUBUNTU 10.10 so i could type my damn password to to the PARTIAL upgrade since the problem originated with the recomended upgrades freezing up in process.

STILL kept hanging up until i realized that one of the stupid fe$·(%RKING upgrades was for microsoft FONTS...which had the whole disclaimer 5 gpages long legal gibberish PROBASBLY followed by an ¨I accept¨button which I could never see...could never scroll down that far for some reason...so the update just hung up there forever. Just to show you no matter how far you run microsoft problems are always lurking right around the corner!

anyway, the kernel finally couuld update 100% and I have my mousepad, keyboard, sound adn video and wifi back....pheww!!!

moral of the story?? what is it...hmm...

well, even if you ahve a back up made with ¨back in time¨ it wont do you much good if your keyboard and mousepad go down..

nobody helped me here but it was xmas so i understand...thanx anyway for reading and smiling at my frustration.

SOLVED

---

### Post by ehsanul_g3 on 2010-12-29
> **garvinrick4 said:**
> Give it a go partner. Have a Merry Christmas
Let me no how she did.

Hey, it worked beautifully \\:D/. Thanks so much, gotta love this community!

Oh, and hope you had a Merry Christmas yourself.

---

### Post by nuwave on 2011-06-09
Hello I unfortunately am suffering from the same problem. I found a similar post[http://ubuntuforums.org/showthread.php?t=422523]("http://ubuntuforums.org/showthread.php?t=422523") and followed much of the same commands and got the system to boot properly(10.04) but keyboard and touchpad are not working(HP mini 1000). I think my problem is I have no internet connection in the liveUSB(no ethernet or wireless). Anyone one have any clues to get this working without an internet connection or a workaround. I am sure these commands will fix my problem being that I got the log in screen when I couldn't even get that before I tried some of these commands. Your help will greatly appreciated.

Thanks,
Nuwave

---

