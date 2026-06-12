---
title: "Making a NAS box."
date: 2009-09-03
forum: General Help
---

### Post by dchurch24 on 2009-09-03
Hi all,

I have a 1tb NAS (WD Worldbook) that I bought some time ago, and to be honest it's been working excellently.

However, I've run out of space once again and now think the time might be right to try and build a scaleable NAS box.

Obviously, I want to use Ubuntu, simply because I know it and trust it.

My question is, though:

I have another 1tb (2x500) USB drive that I was thinking of using as well as a few 250-500gb Sata drives laying around.

Is there a configuration where I would be able to see all the drives as one big drive, or would I have to mount each one and share appropriately?

Also, I seem to remember having trouble sharing the USB drive once mounted (I haven't used it in a while) - would it be possible to use the 1tb USB drive as part of my NAS?

---

### Post by P4man on 2009-09-03
I think you can all do that with LVM's

However, Id consider using a specialized NAS distro, rather than a full blown ubuntu. have a look at this:

[http://www.freenas.org/index.php?option=com_frontpage&Itemid=22](http://www.freenas.org/index.php?option=com_frontpage&Itemid=22)

Probably easier to setup, use and maintain.

---

### Post by dchurch24 on 2009-09-03
Hi, thanks for the reply.

I had found freenas whilst googling around, thank you.

I think that's what I will probably go with - nice easy looking interface.

---

### Post by Mighty_Joe on 2009-09-03
One advantage to using Ubuntu is that you get a lot more flexibility over FreeNAS. I built an "appliance" out of a cheap VIA c3 board, 512Mb memory and a 500Gb hard drive, installed 8.04 Server and set it up to do lots of stuff: download torrents, web server, share drives via Samba and SSH, and so on.  I've even fooled around with running security cameras through it. It uses a fraction of the power of the PC I used to leave running 24/7 for the same tasks.
Don't get me wrong, FreeNAS is great if all you want to do is build a NAS.  But an Ubuntu appliance can be much, much more.

---

### Post by dchurch24 on 2009-09-03
That was kind of my feeling too.

I already have a MythTV server running, that also doubles as a database for my home automation stuff, I was thinking that I could use that, but it only has IDE on board.

I suppose I could just buy another WD Worldbook, but like you say, I sort of wanted a 'all things to all men' type box.

---

### Post by Nostalos on 2009-09-03
You would only need LVM to make some virtual disks. Which is handy if you want to be able to modify/resize on the fly.   If you are just wanting to make a single large drive you don't need anything more than dmaid.

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)  covers some of this.

---

### Post by dchurch24 on 2009-09-03
Fantastic - this looks like the ticket.

---

