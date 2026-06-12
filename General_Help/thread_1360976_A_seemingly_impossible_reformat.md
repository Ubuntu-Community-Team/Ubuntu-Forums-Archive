---
title: "A seemingly impossible reformat"
date: 2009-12-21
forum: General Help
---

### Post by Vilkata on 2009-12-21
To begin with, I have installed Ubuntu and most of it's variants many times. However, this one has me stumped.

Recently, my mother got an old computer, ie 6 gig HD, 128 mb ram. A Dinosaur. It is currently running Windows XP, so needless to say, it lags. Alot.

So, i decided to install Xubuntu, and possibly just install Fluxbox. Seems easy enough. Here is the list of obstacles I have hit:


[LIST=1]
[*]Does not boot from USB. I am not shocked by this, given the age of the computer.
[*]Does not boot from CD. I have placed an Ubuntu Alternate Install CD, and it simply doesn't boot from it, though once in XP it sees the CD, and Wubi starts as it should. Which leads to my next point.
[*]Wubi won't install at all, giving an error and saying permission denied.
[*]Wubi offers the option to change the boot menu so it will boot from CD. This gives the same error.
[*]The computer seems to not allow any way to access the BIOS to check/change the boot order.
[/LIST]
So now, I am at a complete loss. Any help/ideas would be great. Thanks in advance.

---

### Post by HappyFeet on 2009-12-21
You may need to use a boot floppy disc to get it to boot to CD.

At boot up, hit F1, F2, F10, F12, and Del to see if any of those will give you access to the BIOS. You could also reset the CMOS by pulling the battery off the motherboard and reseating it.

As far as the specs on that computer, I would not recommend xubuntu. 128mb of ram is really pushing it. Puppy, Slitaz, or DSL would be a much better choice.

---

### Post by Extract_Here on 2009-12-21
Xubuntu is too much

---

### Post by Trapper on 2009-12-21
> Does not boot from CD. Go into your bios at bootup and see if there's a boot up option to boot from cd. Make it the "first" bootable device if your dino does support booting from cd.

If not, you're going to have to do an intial boot up from a boot floppy (same procedure applies in the bios) , as stated above.

You failed to mention your processor speed, etc. Can the machine accept more RAM?

I'm not sure your Mom is going to be excited about this machine and will probably think linux is the problem. ???

A much better older machine can be found for peanuts. Actually a new machine can be found for dirt cheap these days. It may not have bells and whistles but it will be substantial probably and she won't be turned off or frustrated.

---

### Post by stu644 on 2009-12-21
try booting windows  and going to my computer, then right click the hard disk and go to the security tab and allow everyone all permissions on the hard disk, also if you stop all of the anti-virus and firewall processes it should allow you to run the wubi program and successfully install ubuntu.  if you are going to disable the anti-virus and firewall i would recomend disconecting your internet connection so as to avoid the risk of a virus/hacker.

---

### Post by HappyFeet on 2009-12-21
> **Trapper said:**
> Go into your bios at bootup and see if there's a boot up option to boot from cd. Make it the "first" bootable device if your dino does support booting from cd.


The OP said he can not get into the BIOS.

---

### Post by snowpine on 2009-12-21
Christmas is right around the corner... :)

---

### Post by Trapper on 2009-12-21
> **HappyFeet said:**
> The OP said he can not get into the BIOS.

Yes, I know but I also noted that you gave him some tips considering what to try. If that won't do it he could always surf the net for whatever motherboard he has and eventually track down the manual on it. Even most dinos still have one available somewhere. 

Is there such a thing as an inaccessible bios? I'm not sure. I had old 286's- 386's and was never shut out of any of them. I am not sure about my old dual soft floppy XT. :)

---

