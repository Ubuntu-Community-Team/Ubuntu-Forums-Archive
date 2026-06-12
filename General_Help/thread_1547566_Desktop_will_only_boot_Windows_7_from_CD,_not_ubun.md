---
title: "Desktop will only boot Windows 7 from CD, not ubuntu or Windows XP"
date: 2010-08-06
forum: General Help
---

### Post by user1397 on 2010-08-06
So I've got this old dell desktop from like 2005, its got a 2.6 GHz celeron and 1GB ram.

It started getting really slow so I decided to backup all of my data and do a re-install of windows xp home edition (this comp has to have windows xp for family reasons :))

So I found out I lost my windows xp install disc, so I did what any sane being would do and I downloaded it and burned the image to a disc (my product key is legit so I see no reason why I shouldn't do this).

Anyway, I set the BIOS settings to boot from CD first, then I popped the disc in and nothing happens...

So I say hmm...maybe the CD's corrupt or something, so I try my windows 7 install disc and it loads (albeit very slowly).

So I make a second copy of xp, still no go...third copy, still no go...

I've used the same xp install disc in virtualbox on my ubuntu computer, and it worked great.

I even tried loading an ubuntu lucid disc and it wouldnt load, seems like the only thing it likes is windows 7...


WTF

---

### Post by pastalavista on 2010-08-06
Did you extract (install) the iso or did you just copy the iso file?

---

### Post by user1397 on 2010-08-06
> **pastalavista said:**
> Did you extract (install) the iso or did you just copy the iso file?

I burned the image to a blank dvd...just like I would for an ubuntu iso or any other iso.

---

### Post by pastalavista on 2010-08-06
> **ubuntuman001 said:**
> I burned the image to a blank dvd...just like I would for an ubuntu iso or any other iso...

Sorry, I forgot to notice you weren't a noob. It doesn't make sense unless the CD drive or BIOS was altered by the Win7 disk somehow.

---

### Post by user1397 on 2010-08-06
> **pastalavista said:**
> Sorry, I forgot to notice you weren't a noob. It doesn't make sense unless the CD drive or BIOS was altered by the Win7 disk somehow.haha thanks I guess.

But yea it really doesn't make any sense...I even tried updating the BIOS and seeing if the new version had more options or something, but alas, it has no new features as far as I can tell... :(

I am truly lost here, and it's been a while since this has happened to me :popcorn:

---

### Post by pastalavista on 2010-08-06
My first instinct would be to try different CD/DVD drives in different machines. If it still won't work, download/burn new iso with different machines and if it does work in other machines, you need a new drive.

---

### Post by user1397 on 2010-08-06
> **pastalavista said:**
> My first instinct would be to try different CD/DVD drives in different machines. If it still won't work, download/burn new iso with different machines and if it does work in other machines, you need a new drive.
I did try burning the iso on different machines, both an ubuntu one and a windows one.

And the drive clearly works, it just has *selective recognition* or something... :(

---

### Post by wilee-nilee on 2010-08-06
For Ubuntu or XP burn it to a cd-r, use the F-key prompt for choice of boot, it is on the screen momentarily at startup mine is f12.

---

### Post by user1397 on 2010-08-06
> **wilee-nilee said:**
> For Ubuntu or XP burn it to a cd-r, use the F-key prompt for choice of boot, it is on the screen momentarily at startup mine is f12.

o wow, it probably is really that simple...it needs to be a blank cd not a dvd...its just that i didnt have any blank cd's around, I only had dvd's...guess i have to go buy some

---

### Post by user1397 on 2010-08-07
Well apparently it did need to be a cd-r, but that wasn't the only problem.  The cd drive was so old that it was basically dying, so just to reinstall windows I swapped cd drives with my other desktop temporarily, and that did the trick.

Thanks for all suggestions, case closed :)

---

