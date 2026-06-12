---
title: "black screen with blinking white cursor top left"
date: 2010-07-09
forum: General Help
---

### Post by Nikolai D. on 2010-07-09
Hi guys,

I have here two old identical compaq pc's with 64mb ram.
I want to copy drive/os from one machine to other. So i do a drive to drive clone (witn both hd's deing connected to another machine). And it says its done and okay. But the second (cloned) machine doesnt boot. And have the black screen with the blinking white cursor in top left corner. I have already tried to do fdisk /mbr and also copying partition table from original to destination disk. Because i think it is logical that with a drive to drive clone it sould be copied. But i have a doubt in that somehow. Because why would it not boot if it was copied then.

Does anyone have any suggestions?

Thank you!
Nikolai

---

### Post by Leppie on 2010-07-09
what os is installed on the drives? and which boot loader is it using?

---

### Post by Nikolai D. on 2010-07-12
Hi Leppie,

Its win98.

:)

---

### Post by lordskid on 2010-07-12
do you have any linux box around?

its a matter of dd

e.g.
```

dd if=/dev/sda1 of=/dev/sda2

```
where if parameter is input and of parameter is output.

---

### Post by t0p on 2010-07-12
Black screen with white cursor flashing top left, huh?  Sounds like the first computer I ever used, the TRS80.  Pretty intimidating when you're like 11 or something.

Whoops!  I thought this was one of those memory lane threads in the Cafe.  Do what lordskid said and use dd.

---

### Post by Nikolai D. on 2010-07-13
isnt it
dd if=/dev/sda of=/dev/sdb ?

---

### Post by Leppie on 2010-07-13
> **Nikolai D. said:**
> isnt it
dd if=/dev/sda of=/dev/sdb ?
if you are cloning the entire drive, yes.
you actually may want to use it like this:
```
sudo dd if=/dev/sda of=/dev/sdb conv=notrunc,noerror
```
(do not truncate files, do not stop on read errors)

---

### Post by Nikolai D. on 2010-07-13
dd did the trick,
i wonder why SpotmaulPowerSuite, Ghost, Clonezilla, Acronis, DriveImageXLM etc didnt do that?..

---

### Post by Nikolai D. on 2010-07-14
And by the way first computer i was actually highly using was Dendy. Its a Russian HW clone of old Nintendo. 
[http://en.wikipedia.org/wiki/Dendy_(console](http://en.wikipedia.org/wiki/Dendy_(console))
Its actually a computer to. Not quite a PC but anyway. I remember soldering the broken off power adapter ports of my friends Dendys. That was my first geek helpdesk-like experience i think. :)

The funny thing, i have just realized that old times console 'war' is replaced by todays OS 'war'. Atleast for me. Isnt it? I think on this forum (dedicated to some special OS) there will be others who will kind of agree with that.

p.s.
Maybe this thread can also actually be moved to Cafe now if you wish. :)

---

### Post by lordskid on 2010-07-14
and you were right it should be sda and sdb coz its between 2 disks.

---

### Post by Leppie on 2010-07-20
> **Nikolai D. said:**
> dd did the trick,
i wonder why SpotmaulPowerSuite, Ghost, Clonezilla, Acronis, DriveImageXLM etc didnt do that?..
because dd copies in raw mode and other applications probably analyse everything first...

---

### Post by linuxcss on 2010-08-21
i installed lucid from 10.04 cd, on first boot I see and subsequent boots I still get only
[B]black screen with blinking white cursor top left

this is on acer AOD250 netbook.

need help on this one.
[/B]

---

