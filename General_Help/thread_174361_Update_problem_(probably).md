---
title: "Update problem (probably)"
date: 2006-05-11
forum: General Help
---

### Post by yooden on 2006-05-11
Hi there,

I have a somewhat complicated problem, and I would be grateful for any pointers you can give me to sort it out.

Here's the story: I talked a friend into trying Linux, and since I heard that Ubuntu is particularly beginner-friendly, I suggested Breezy Badger. I did the installation, installed Automatix to get MP3 support and everything worked fine. He used the system for a few weeks and started to recommend it to others.

Yesterday he called me to tell me that he did "this update thingy", clicked a few buttons, got a few strange looking message, tried to cancel the whole thing, with the result that Ubuntu would no longer boot. He is not sure about the exact error message during the update, but I got the impression it was about Lilo.

I took a look, the last message told that the kernel could not mount the root file system. ("Cannot open root device 306"). Googling leads me to believe that the kernel no longer knows about IDE devices.

So now I have a number of problems:
- I don't have error messages. Once this is solved I intend to give him a few pointers about saving error messages, but this won't help this time.
- I haven't used Lilo for years now. I jumped on Grub as soon as it was usable. The configuration looks ok though.
- This might have something to do with initrd. I never worked on initrd before.
- I approached the basic install plus Automatix pretty naive, just clicked through the dialogs as fast as possible.


So, this is it. I would really like to help him, since I'm the one coaxing him into using Linux. If you have any idea how to approach the problem we would be really grateful. Any pointers are appreciated.

Personally, this was my first experience with Ubuntu, so please don't assume that I know any specifics. On my own systems I use Debian for a few years now, so you can assume basic familiarity with that.


Thanks in advance,
Thorsten

---

### Post by drpepper on 2006-05-11
i'm not too sure but maybe u shud try to reinstall LILO? or install GRUB form the ubuntu cd rescue mode. maybe something changed in boot record and thats why it wont boot. sorry i havnt got more advice!

---

### Post by sinkxdie on 2006-05-11
Does he have Windows too?
He can always "insert XP recovery CD, Recovery Console, and type "fixmbr" "
then install Grub or Lilo again from Windows

But that is only possible if you have Windows
If not, ingore all that

---

