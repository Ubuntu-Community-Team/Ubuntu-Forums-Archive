---
title: "Firefox profileon a usb stick?"
date: 2009-11-29
forum: General Help
---

### Post by Garnett on 2009-11-29
I use a few ubuntu machines and it would be really useful to be able to use a USB stick to ferry my bookmarks and extensions etc between machines.

Is this possible?

---

### Post by Sin@Sin-Sacrifice on 2009-11-29
Yeah... they're all in the ~/.mozilla folder.

---

### Post by tars_ac on 2009-11-29
If you're only using the computer when you have the usb stick, then you can make the .mozilla a softlink to a directory on the stick, and it will work transparently (although firefox likes to write a lot to its profile, so it could impact performance some).  Otherwise, you can just copy it back and forth when you switch.

---

### Post by Garnett on 2009-11-30
Other people use all the machines. I wanted to be able to plug in my pendrive and have firefox look like, and function like it does when I'm at home, but only when the usb stick is used, otherwise it needs to use the profile set up on each machine.

---

### Post by Garnett on 2009-12-01
Sorry. I've tried googling solutions and can't find how to do this. Anyone?

---

### Post by Sin@Sin-Sacrifice on 2009-12-01
You may be able to do this with the firefox extension Febe. Not sure how you would make it so it won't keep the profile unless you delete the profile at the end of every session though.

---

### Post by blueridgedog on 2009-12-01
It could be as simple as:

When you sit down at a computer:

```
cp -r /media/usbdrive/.mozilla ~/.mozilla
```

When you leave, if you have added bookmarks:

```
cp -r ~/.mozilla /media/usbdrive/.mozilla
```

It would probably be cleaner with rsync:

```
rsync -av /media/usbdrive/.mozilla ~/.mozilla --delete
```

then

```
rsync -av ~/.mozilla /media/usbdrive/.mozilla --delete
```

In the above, you need to change /media/usbdrive to the actual path given to the mounted USB flash drive.

I would test and verify any of these ideas as they are more or less brainstorming.

---

### Post by Garnett on 2009-12-02
Hey I like the sound of that.

Two questions:

Why is rsync better? I would like to add to your original idea so that when I plug in the usb stick, the script backs up the "machine" profile on the computer to a backup directory on the usb stick first, then replaces it with "Garnett's" profile stored on the usb stick.

Then on leaving, another script backs up Garnett's profile by overwriting the version on the usb stick with the version on the PC (so as to save any changes), and then puts back the "machine" profile.

Second question: Is there a way to dress these scripts so that they have nice GUI? Say, two buttons - "Log In" and "Log Out"

---

### Post by Garnett on 2009-12-02
On plugging in the USB:

cp -r ~/.mozilla /media/usbdrive/firefoxbackup/.mozilla
cp -r /media/usbdrive/.mozilla ~/.mozilla

And before removing it:

cp -r ~/.mozilla /media/usbdrive/.mozilla
cp -r /media/usbdrive/firefoxbackup/.mozilla ~/.mozilla

I'm basing this on your brainstorming, blueridgedog, and know next to nothing about linux, so any advice very gratefully received.

---

### Post by Garnett on 2009-12-02
By way of showing my working...

I've now found this tutorial:

[Have something happen when you plug in a USB device]("https://help.ubuntu.com/community/UsbDriveDoSomethingHowto")

And thinking some more about it...

I would like to set up the scripts so that the machine's firefox profile is backed up to a temporary deirectory on the machine in such a way that if the USB stick is removed, a script is run to restore the machine profile and then delete the temporary directory.

That way, if I forget to run the proper "exit" script before just pulling out the usb drive, at least the machine profile is safely restored, and all that is lost is any updates I've made that session to "Garnett's" profile.

---

### Post by blueridgedog on 2009-12-02
You are on the right track...just test the "to" portion really well before you risk overwriting your profile (a backup or two will be essential).

---

