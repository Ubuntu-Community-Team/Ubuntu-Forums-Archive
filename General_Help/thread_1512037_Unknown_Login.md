---
title: "Unknown Login"
date: 2010-06-17
forum: General Help
---

### Post by Michaelvoice on 2010-06-17
I, before having recieved an old Imac from a friend, have never before heard of Ubuntu. The imac happens to have Ubuntu already installed. My problem is that /I haveno clue what the login is. neither do I know what a grub prompt is. I would like to keep ubuntu, I have downloaded a new copy and made both a CD as well as a usb pendrive, neither of which worked. The CD is now stuck in thedrive. any one have any suggestions before i try a sledge boot?

---

### Post by sisco311 on 2010-06-17
You can reset the password from the *Recovery Mode*, just follow this instructions:

[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by gadolinio on 2010-06-17
> **Michaelvoice said:**
> I, before having recieved an old Imac from a friend, have never before heard of Ubuntu. The imac happens to have Ubuntu already installed. My problem is that /I haveno clue what the login is. neither do I know what a grub prompt is. I would like to keep ubuntu, I have downloaded a new copy and made both a CD as well as a usb pendrive, neither of which worked. The CD is now stuck in thedrive. any one have any suggestions before i try a sledge boot?

First of all, ask your friend for the login and password! :P
If that's not successful...

What happens with the CD and USB, exactly?
In order to use a liveCD/USB your computer has to be set to boot from the CD drive/removable media <before the hard disk drive>. Don't know how to do that with a Mac. Generally pressing a key such as F1, F, F8, F12, ESC, etc takes you to the BIOS settings, where you can set the boot order. But Apple might have a different approach for that.
And I think you have to download a special image file for PPC Macs; if yours has an Intel microprocessor, I think the same one will work ok.

---

### Post by Paddy Landau on 2010-06-18
If your friend didn't install the latest Ubuntu, I'd recommend that you simply overwrite his installation of Ubuntu with the newest version. But be sure to back up any important data first!

The newest version is Lucid 10.04, and it's significantly better than the older versions.

---

### Post by warfacegod on 2010-06-18
> **Paddy Landau said:**
> The newest version is Lucid 10.04, and it's significantly better than the older versions.

I know *allot* of people, myself included, that would totally disagree with that statement.

---

### Post by Paddy Landau on 2010-06-18
> **warfacegod said:**
> I know *allot* of people, myself included, that would totally disagree with that statement.
Oh, OK. I find it better because I find it faster and the drivers seem to have been updated. But, well, different strokes for different folks!

---

### Post by warfacegod on 2010-06-18
> **Paddy Landau said:**
> Oh, OK. I find it better because I find it faster and the drivers seem to have been updated. But, well, different strokes for different folks!

Perhaps in that area it is better. My hardware drivers have been running perfectly since 8.10. In customizing, however, it is an abysmal failure. Try playing with the panel in 10.04 UNE, for example, and you'll know what I mean.

Hundreds of tiny, little changes that individually don't mean much but minor irritation, collectively add up to sheer idiocy.

For example; what possible reason could there be for changing "update-grub" into "grub-mkconfig"?

The entire OS "feels" wrong! When I use it, I get the same greasy feeling in my stomach that I get on the rare occasions I have to Windows. Especially Vista.

---

### Post by wojox on 2010-06-18
> **Michaelvoice said:**
> I, before having recieved an old Imac from a friend, have never before heard of Ubuntu. The imac happens to have Ubuntu already installed. My problem is that /I haveno clue what the login is. neither do I know what a grub prompt is. I would like to keep ubuntu, I have downloaded a new copy and made both a CD as well as a usb pendrive, neither of which worked. The CD is now stuck in thedrive. any one have any suggestions before i try a sledge boot?

Download Puppy Linux and burn it to a USB Drive and boot off of it. Once it's loaded open a terminal and issue **eject**

---

### Post by Paddy Landau on 2010-06-18
> **warfacegod said:**
> When I use it, I get the same greasy feeling in my stomach that I get on the rare occasions I have to Windows. Especially Vista.
Yeuch! My queasy feelings came from the all-too-frequent crashes and sitting tapping my fingers waiting for a response when on Windows. Although Ubuntu isn't perfect by any means, at least the longest I have to wait is two minutes for a full reboot.

> **wojox said:**
> Download Puppy Linux and burn it to a USB Drive and boot off of it. Once it's loaded open a terminal and issue **eject**
Alternatively, the drives often come with a pinhole to manually release them. Check the manual (off the Internet, perhaps, if your friend didn't give you one).

---

### Post by wojox on 2010-06-18
> **Paddy Landau said:**
> 
Alternatively, the drives often come with a pinhole to manually release them. Check the manual (off the Internet, perhaps, if your friend didn't give you one).

I thought it was a laptop. :confused:

As you can see I'm not to familiar with Macs.

---

### Post by warfacegod on 2010-06-18
> As you can see I'm not to familiar with Macs.

Nobody is. That's the way Mac likes it!:p

---

### Post by warfacegod on 2010-06-18
Michealvoice, I agree with sisco311. The link posted in #2 is the first place to start. Assuming, of course, that you can't get the password from your friend.

---

### Post by Michaelvoice on 2010-06-18
ok recapp
 
I have an old IMAC, some one else installed Ubuntu, for all intents and purposes this person no longer exists. When the computer is turned on I hear a chime, see an off white screen flash and then a command line prompt asking me to type l for linux or c for CD boot.  
 
 
if you pick c--- the screen jumps for a moment clears and resets (CD is iso image of ubuntu downloaded on a PC) return to original screen
 
if you pick l or nothing ubuntu loads
 
Nothing different occurs when USB drive is present
holding esc, space, shift or F1 through boot process has no discernable effect. 
 
I get that ultimately I need to get to recovery mode, but nothing as of yet has allowed me to make that choice.

---

### Post by Michaelvoice on 2010-06-18
I neglected to mention this earlier, it alsays welcome to yaboot

---

### Post by Paddy Landau on 2010-06-18
> **wojox said:**
> I thought it was a laptop.
My laptop's DVD drive has a pinhole to manually release it. I believe that this is standard these days.

---

### Post by t0p on 2010-06-18
> **Paddy Landau said:**
> My laptop's DVD drive has a pinhole to manually release it. I believe that this is standard these days.

On my (not very new) Viglen desktop machine, the NEC DVD-ROM/CD-RW drive has a little hole just under the drawer.  I never noticed it before, but I guess it's the manual release you're talking about.  I'm reluctant to try it just to see; but I shall certainly bear its existence in mind in case I ever need it.

---

### Post by gadolinio on 2010-06-19
> **warfacegod said:**
> Nobody is. That's the way Mac likes it!:p

Hahahahahahah! Good point...

---

### Post by warfacegod on 2010-06-19
> (CD is iso image of ubuntu downloaded on a PC)

When you made the CD, did you burn it as an .iso or simply burn the file onto the disc? There is a *huge* difference, in this case.

---

