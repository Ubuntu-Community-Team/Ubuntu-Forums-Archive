---
title: "Upgraded from 9.04 to 9.10 and from that to 10.04"
date: 2010-06-19
forum: General Help
---

### Post by Ownager on 2010-06-19
9.04 and 9.10 versions were fine. It allowed me to boot to desktop. I was surprised that 10.04 refuses to let me to boot to desktop. I noticed that Ubuntu splash looks so big to me. It's more like 800 x 600. lol... I really use 1024 x 768. And also it says "Out of frequency range set resolution lower or see monitor users guide" 

I made a guess with a hotkey. I got into terminal. Is there a way to change the resolution? 

I forgot to say my video card is ATI Radeon X850 pro 256 MB

Thanks

---

### Post by davidmohammed on 2010-06-19
have you tried editing your grub and booting with nomodeset?

(press shift after the bios splash screen to display the list of kernels (your grub) and then press e.  Find the line with quiet splash and add nomodeset BEFORE quiet splash.  Then boot.)

---

### Post by Ownager on 2010-06-19
bios splash = Ubuntu splash? And I never try these before. I only know how to edit grub menu. 

gksu gedit /boot/grub/menu.lst

It may not be right for editing.  

I haven't tried nomodeset yet. I am going to give it a try. Be right back

---

### Post by ranch hand on 2010-06-19
You can edit the grub menu entry when your menu comes up on the screen by hitting e .  Just add the nomodeset to the end of the instruction line.

---

### Post by Ownager on 2010-06-19
> **ranch hand said:**
> You can edit the grub menu entry when your menu comes up on the screen by hitting e .  Just add the nomodeset to the end of the instruction line.

Can you please give me an example or a screenshot? I am kinda confused. Thanks

---

### Post by Nr90 on 2010-06-19
When you turn on your computer you'll see something of a bios flash. In my case it shows some dell loading bar. (this is before any OS is booted)
Hold shift and you'll end up in the grub menu where you can select which kernel you wish tot boot.
Select your kernel (top one most likely), press e.
Now add nomodeset (or i915.modeset=0 if you have an intel chipset) just before the quietsplash
Hit ctrl+x to boot (i think)

---

### Post by ranch hand on 2010-06-19
When you boot the box you have a menu appear on your screen.  If not you will need to hit the shift key to get the grub2 menu to show up.

Highlight the OS you want to boot and hit e (for edit).  This works in both the new and old versions of grub.

"nomodeset" would be appended to the end of the "linux" line so that  it would read "ro quiet splash nomodeset".

If you are using the old grub and ext3, I have no idea why you are upgrading.  Seems a waste of time and effort to "upgrade" to a system meant to run on ext4, with a supported version of grub, on a system that is running something else.

A clean install would be the way I would go for this one.

---

### Post by Ownager on 2010-06-19
I already tried a clean install. I got an error at 28% installing. 

It said 

> The installer encountered an error copying files to the hard disk [Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

That's why I had to upgrade from 9.04 -> 9.10 -> 10.04.

And you were saying that I can add nomodeset before quiet splash.

You meant like this 

message
nomodeset
quiet

Is that right?

---

### Post by ranch hand on 2010-06-19
I do not think I have ever seen "message" in any boot instruction string.  Could be I am senile though.

Below is how it would look in the grub2 menu, it will be slightly different in grub-legacy but the instruction string is the same;
```

linux    /boot/vmlinuz-2.6.35-2-generic root=UUID=c6a2c56c-d4ec-4dc3-a107-f5ef8deb4254 ro   quiet splash

```
You want it to look like;
```

linux    /boot/vmlinuz-2.6.35-2-generic root=UUID=c6a2c56c-d4ec-4dc3-a107-f5ef8deb4254 ro nomodeset  quiet splash

```
I do not know where you burned the CD or where you got the ISO.

You should always check the md5sum on the ISO before burning.  It is a good idea to check the health of the CD before installing.

The crazy way they have the Live CD set up now requires you to hit any key when the purple screen with the 2 cryptic icons at the bottom comes up.  You have about 3 seconds so have your finger ready.  This will get you the menu with the option of checking the CD.

I would down load the ISO again, run the md5sum check, burn the CD at the lowest possible speed (4 or under), the lower the better.

I do not know how your box is set up (single OS, dual boot with some strange OS, multi-boot with several Linux OS') or what your partition table is but a clean install on 2 partitions (/ and /home) will save you a lot of grief down the road.

---

### Post by Ownager on 2010-06-19
> **ranch hand said:**
> I do not think I have ever seen "message" in any boot instruction string.  Could be I am senile though.

Below is how it would look in the grub2 menu, it will be slightly different in grub-legacy but the instruction string is the same;
```

linux    /boot/vmlinuz-2.6.35-2-generic root=UUID=c6a2c56c-d4ec-4dc3-a107-f5ef8deb4254 ro   quiet splash

```
You want it to look like;
```

linux    /boot/vmlinuz-2.6.35-2-generic root=UUID=c6a2c56c-d4ec-4dc3-a107-f5ef8deb4254 ro nomodeset  quiet splash

```
I do not know where you burned the CD or where you got the ISO.

You should always check the md5sum on the ISO before burning.  It is a good idea to check the health of the CD before installing.

The crazy way they have the Live CD set up now requires you to hit any key when the purple screen with the 2 cryptic icons at the bottom comes up.  You have about 3 seconds so have your finger ready.  This will get you the menu with the option of checking the CD.

I would down load the ISO again, run the md5sum check, burn the CD at the lowest possible speed (4 or under), the lower the better.

I do not know how your box is set up (single OS, dual boot with some strange OS, multi-boot with several Linux OS') or what your partition table is but a clean install on 2 partitions (/ and /home) will save you a lot of grief down the road.

I had to say message because I don't remember what it said. lol 

I didn't see "ro"

You were saying 

linux    /boot/vmlinuz-2.6.35-2-generic root=UUID=c6a2c56c-d4ec-4dc3-a107-f5ef8deb4254 ro nomodeset  quiet splash

You meant this 

linux    /boot/vmlinuz-2.6.35-2-generic root=UUID=c6a2c56c-d4ec-4dc3-a107-f5ef8deb4254 

ro nomodeset  

quiet splash

right? 

Mine doesn't say ro and splash. It shows like this 

linux    /boot/vmlinuz-2.6.35-2-generic root=UUID=c6a2c56c-d4ec-4dc3-a107-f5ef8deb4254 

quiet

---

### Post by Ownager on 2010-06-19
sorry about double post. I found ro. I added nomodeset before quiet splash. And I click on b after it's added. It still doesn't work.

---

### Post by ranch hand on 2010-06-19
I do not think the placement in that string is critical but you may want  to put it before the "quiet" just in case.  They should, however, really be in one line.  If you are using grub2 they have to be in one line.  If grub legacy they don't need to be (I think) but really should be.

If you are using grub-legacy you will need to use the space bar instead of the shift key to bring up your menu.  I wouldn't have a hidden menu if all I ran was one OS, I want the controls were I can see them.

I take it that you do not get a splash screen with your menu entry (default for 9.10 is ghastly used toilet paper brown like the default login screen).  

The "ro" really should be in there (read only).

I do not have splash in the custom menu entries that I use for 10.04 or 10.10-testing as plymouth does not get along with my box at all and not having the "splash" instruction makes it possible to boot.  I would not worry about it.  If your boot works as it should (does for most) you will not see the splash screen for more than a couple of seconds anyway before the login screen is up.  My sons box goes from hitting enter on the menu to usable desktop in 15 seconds (we won't talk about mine).

---

### Post by ranch hand on 2010-06-19
> **Ownager said:**
> sorry about double post. I found ro. I added nomodeset before quiet splash. And I click on b after it's added. It still doesn't work.
What does happen?

---

### Post by Ownager on 2010-06-19
I did like this 

linux /boot/vmlinuz-2.6.35-2-generic root=UUID=c6a2c56c-d4ec-4dc3-a107-f5ef8deb4254 ro nomodeset quiet splash

And then I clicked on b for booting. It still shows you the same bad result. It should be fixed. It still says out of frequency range set resolution lower or see monitor users guide after it loaded Ubuntu splash.

---

### Post by ranch hand on 2010-06-19
Are you doing auto login?  If so I am not sure how you get out of that in a command line.  If you get the normal login screen there are options on the bottom panel for what type of session you are logging into.

Default is gnome.  There is also "xterm" and "failsafe-gnome".  I would try the failsafe-gnome and see if that will get you in.

If you auto login you should at least have it timed so the login screen comes up.  You are missing a lot of options.

If you are running that way, have you tried booting recovery mode?  This may work in spite of the graphics problem.  If so let it run untill you hit the menu and just take the first option (return to normal boot).  This should give you a text login.  Enter user name and on the next prompt password.

When you get the next prompt type  startx .  This should, if it is possible, put you on the desktop.  If not it should give you some interesting messages.

I think that this is pretty strange as the support for ATI is definitely better in 10.04.  I do not use the ATI driver as it is not as good with my card as the OSS driver.  If you can't get to the desktop through recovery I would reboot through recovery again.

When you get to the menu choose the last option (terminal with networking).  This will put you into a root terminal so no sudo is needed.  I would try the ATI driver;
```

apt-get update

```
and then
```

apt-get install fglrx

```
I do not know that that is all you need to do to put that in place but I think it is.  If not we can try another version (newer, not yet released) of the OSS driver.

---

### Post by Ownager on 2010-06-19
I tried these too. It doesn't fix at all. I am gonna try to install it from jump drive. I wish it works good.

---

### Post by ranch hand on 2010-06-19
You may want to look into this ppa;

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

If you are speaking of installing on a usb flash memory device that is fine, I haven't ever done that but many have and did during the testing cycle too.

I am not sure how that all works but I highly recommend, if you can, to use password login so you have all the options you can have.  When installed go to /etc/default/grub and comment this line;
```

#GRUB_HIDDEN_TIMEOUT=0

```
so that is looks just like that.  This will give you a visible menu if you do not have one.

If you dual boot and are asked where to install grub, do not install it anywhere but on the drive (not on any partitions).  If asked, there is a suggestion that "if in doubt install it every where".  Do NOT do this.  It is a bug and a bad mistake.

If you have an MS OS on board it will eat your boot sector if you install it everywhere.  If you don't (good for you) it is still a bad idea.

---

### Post by Ownager on 2010-06-19
I want to run Ubuntu alone. And I plan to burn cd again too. I tried to follow this instruction from ubuntu page. It said lowest possible speed for burning. I opened properities. It says I have maximum speed and 40.0x (cd) only. I don't think it has lower than that.

---

### Post by ranch hand on 2010-06-19
That is no good at all.  Does your Live CD boot?  If so do it there.  You can do just about anything on the live CD, including adding programs (they go on the ram and are gone when you reboot) it is just slower.

I am sure that it would burn slower than that.  On my box the CDrom will burn at 4 and the DVDrom will burn at 2.5.

You do have the directions for the md5sum check?

---

### Post by Ownager on 2010-06-19
I created Ubuntu 10.04 installation into usb. It worked the best! Now it's installed without an error. :D I think it's better than burning a cd. lol Thank you guys for a help through.

---

### Post by ranch hand on 2010-06-19
That is great.  You probably had at least a bad burn at those kinds of speeds.  You do need to learn to check the md5sum before doing anything with the ISO.  Doesn't happen very often but if that is not right nothing will be right.

Have a great time on a very nice OS.  You can change your Login screen background by editing any image to match the size and resolution of /usr/share/backgrounds/warty-final-ubuntu.png and replacing that image with the one you like.  That is the file Ubuntu looks to for the login and, I believe, the default wallpaper.

---

