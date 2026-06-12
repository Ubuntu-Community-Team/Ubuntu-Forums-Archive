---
title: "How big should I make my tmp partition?"
date: 2009-11-10
forum: General Help
---

### Post by Cuddles McKitten on 2009-11-10
I'm playing around with new partition schemes, and the one I'm trying now requires that /tmp be on its own partition.  How big do I need to make it?  Right now, my /tmp folder is only using about 50 MB, but I'd like to be sure that I don't make it too small and end up with some obnoxious difficulties later.

---

### Post by hal8000 on 2009-11-10
Don't set a /tmp partition if too small and /tmp data is created you either corrupt your filesystem, instead stick to /  /home  and /swap  and /boot if you plan on multibooting, though only / and /home and /swap are essential.

---

### Post by Giblet5 on 2009-11-10
This is one of those 'depends on what you're doing and how many of you are doing it' situations...

I've had 48GB of /tmp space in use before.

You have 50MB in use.

If you do a lot of compiling, 8GB should be more than adequate.

If you are manipulating huge images or 3D CAD models, you'll need more than that.

I simply set aside 200GB for a / partition and don't bother with a separate /tmp filesystem.

---

### Post by Cuddles McKitten on 2009-11-10
Alternate question: is there some way to mount /home and /tmp from the same partition?  I want to play with LUKS since I handle some sensitive financial information, but I don't want to encrypt the root directory since it seems to involve a lot of extra hassle.

---

### Post by Giblet5 on 2009-11-10
> **Cuddles McKitten said:**
> Alternate question: is there some way to mount /home and /tmp from the same partition?  I want to play with LUKS since I handle some sensitive financial information, but I don't want to encrypt the root directory since it seems to involve a lot of extra hassle.

You could but you should not.

A standard cleanup process is to roast everything in /tmp...which is also /home in your scenario...

Disk is $80/TB. That's $0.08 per gig... A small cup of yesterday's gas station coffee costs three times as much.

One thing you *could* do...

```
sudo mkdir /home/tmp
sudo chmod 777 /home/tmp
sudo mount -o bind /home/tmp /tmp
```

---

### Post by alien8tive on 2010-05-18
Thanks Giblet5!!

---

### Post by efflandt on 2010-05-18
I was using tmpfs for /tmp until I was going to do something that needed much more space than the 1 GB RAM I had at the time.  While /tmp is normally small temporary files, if you do anything like modifying iso files or copying CD's or DVD's, that can require a significant amount of tmp space.

---

### Post by Sef on 2010-05-18
>  ...and /boot if you plan on multibooting....

That is not needed if you are multibooting.  GRUB will pick up any extra oses.

---

### Post by DanneUK on 2011-10-28
> **Giblet5 said:**
> 
One thing you *could* do...

```
sudo mkdir /home/tmp
sudo chmod 777 /home/tmp
sudo mount -o bind /home/tmp /tmp
```



grabbing you by the beard and giving you a great big kiss!
Cheers matey!

---

