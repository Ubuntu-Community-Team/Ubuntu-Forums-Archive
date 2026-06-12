---
title: "DVD Decrypter/Shrink for Ubuntu?"
date: 2012-03-15
forum: General Help
---

### Post by johnsmoke on 2012-03-15
[SIZE=2]I was wondering what program out there for Ubuntu can Decrypt as well as shrink DVD's? I'm not illegally copying movies or anything, I am just backing up my entire collection to a recently bought external hard drive. I'd like to have the ability to rip the DVD and decrypt so that I can burn a copy from it in the event that I need to. Basically something that spits out a VIDEO_TS folder that I am able to burn a copy of. Any advice would be appreciated.[/SIZE]

---

### Post by lykeion on 2012-03-15
Check this:
[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

I've only used dvd-rip and it worked for me.

---

### Post by piratebill on 2012-03-15
I can't recommend K9copy enough.  I've also used dvd-rip and its ok.

---

### Post by dave2001 on 2012-03-15
Here's another vote for K9Copy. It's in the Ubuntu repo's (software center) and it works great. You may occasionally run into a DVD with encryption it can't break, but it happens very rarely to me.

It even gives you multiple ways to control the output. You can shrink to any size you want, including DVD-5, or not at all, and end up with a full-quality DVD-DL or iso copy.

It's great for backing up your priceless DVD collection before your irresponsible friends ask to "borrow" them and end up giving you back a useless coaster full of scratches.

---

### Post by johnsmoke on 2012-03-16
> **dave2001 said:**
> Here's another vote for K9Copy. It's in the Ubuntu repo's (software center) and it works great. You may occasionally run into a DVD with encryption it can't break, but it happens very rarely to me.

It even gives you multiple ways to control the output. You can shrink to any size you want, including DVD-5, or not at all, and end up with a full-quality DVD-DL or iso copy.

It's great for backing up your priceless DVD collection before your irresponsible friends ask to "borrow" them and end up giving you back a useless coaster full of scratches.

Tried K9 tonight, seemed great at first, but it seems like on some of my DVD's it rips them but when I play them back, there's no sound! Weird... Does anyone know why this may be or how can fix it? Ripped some great, but a couple it ripped and they have no sound.

---

### Post by swright007 on 2012-03-16
To answer your question:  Install Wine... That is a Window's emulation layer.  Once you get DVD Decrypter and Shrink downloaded right click on th icon and go to the Permissions tab.   at the very bottom is a checkbox that says something like "run as a program" .. check that checkbox.. then click APPLY and OK.  Do that for both program's icons. double click those programs and install them as normal..  :)

---

### Post by dave2001 on 2012-03-16
> **johnsmoke said:**
> Tried K9 tonight, seemed great at first, but it seems like on some of my DVD's it rips them but when I play them back, there's no sound! Weird... Does anyone know why this may be or how can fix it? Ripped some great, but a couple it ripped and they have no sound.

The only time this has ever happened to me is when I'm copying a foreign language DVD and forget to select the appropriate audio tracks. Of course I have k9Copy set up to choose an English audio track by default. I'm not sure if it comes set up this way or not.

After you select your movie in the left window, make sure you go the "selection" tab on the right and tick the box for whatever audio tracks you want. 

Also make sure you have all the extra libraries required for proper dvd decoding: [https://help.ubuntu.com/community/K9Copy](https://help.ubuntu.com/community/K9Copy)

If those things are not the issue, I don't know what to say. I'm not sure what verson of "buntu your using, I've never used K9Copy under Oneiric, but it's always worked great for me in Lucid and Natty

---

### Post by coldraven on 2012-03-16
"DVD Movie Backup" from the Software centre is a one click solution.

---

### Post by Ghost_Mazal on 2012-03-16
> **coldraven said:**
> "DVD Movie Backup" from the Software centre is a one click solution.

I can't find that in the software center at all

---

### Post by johnsmoke on 2012-03-18
> **dave2001 said:**
> The only time this has ever happened to me is when I'm copying a foreign language DVD and forget to select the appropriate audio tracks. Of course I have k9Copy set up to choose an English audio track by default. I'm not sure if it comes set up this way or not.

After you select your movie in the left window, make sure you go the "selection" tab on the right and tick the box for whatever audio tracks you want. 

Also make sure you have all the extra libraries required for proper dvd decoding: [https://help.ubuntu.com/community/K9Copy](https://help.ubuntu.com/community/K9Copy)

If those things are not the issue, I don't know what to say. I'm not sure what verson of "buntu your using, I've never used K9Copy under Oneiric, but it's always worked great for me in Lucid and Natty

Using Ubuntu 11.04   and I did notice that on some DVD's the audio track isn't selected automatically, so that helps! Thanks. I was able to backup the majority of my "official" DVD's, and I'm impressed with K9, only 1 or 2 DVD's still didn't have sound when ripped.... Some unofficial home-made DVD's have issues with dragging the VIDEO_TS folder right onto the desktop directly or copying with K9, but obviously that's an issue with the DVD itself. Anyway, I'm happy with K9, it's very impressive. I love that it can backup a DVD AND shrink it to fit a single sgl layer DVD all in one click (unlike the old days of DVD decrypt, then shrink etc...). Impressive little program.. and it does it all FAST!!! I recommend this program to anyone who wishes to backup their DVD collection.

---

### Post by villalcalde84 on 2012-03-18
I have used K9copy and it works ok to make exact copies of dvds.

@coldraven: there is no package with that name in the ubuntu software centre

---

### Post by nickrout on 2012-03-18
> **villalcalde84 said:**
> I have used K9copy and it works ok to make exact copies of dvds.

@coldraven: there is no package with that name in the ubuntu software centre

k9copy does not make a bit for bit or exact copy. It shinks your files so they will fit on a 4G DVD whereas most commercial DVDs are 9G.

---

### Post by Hylas de Niall on 2012-03-18
> **Ghost_Mazal said:**
> I can't find that in the software center at all

DVD Movie Backup is in the 10.10 repos ;)

---

### Post by dave2001 on 2012-03-18
> **nickrout said:**
> k9copy does not make a bit for bit or exact copy. It shinks your files so they will fit on a 4G DVD whereas most commercial DVDs are 9G.

Sorry Nick, your wrong on that one.  K9Copy shrinks to DVD-5 by default, but it can be changed to any size you want. It's an option in the config window.

---

### Post by nickrout on 2012-03-18
yeah but the point is that it does not make a bit for bit or exact copy, which is what was claimed.

---

### Post by kostkon on 2012-03-18
[Handbrake]("http://handbrake.fr/")... obviously.

---

### Post by nickrout on 2012-03-18
> **kostkon said:**
> [Handbrake]("http://handbrake.fr/")... obviously.

Handbrake is very good, but will not do what the OP wants.

---

### Post by dave2001 on 2012-03-19
> **nickrout said:**
> yeah but the point is that it does not make a bit for bit or exact copy, which is what was claimed.

I don't know if anyone said "bit for bit". 

K9Copy ***will*** make a copy of a DVD, menu's included, at the same video quality and data-size of the original... so that's close enough to an "exact copy" for me.

Who the hell wants a "bit for bit" copy of a commercial DVD anyway? That would include the copy-protection, film-previews, and whatever other nonsense is there.

---

