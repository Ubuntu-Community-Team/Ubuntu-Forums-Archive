---
title: "How can I get my original 10.04 splash screen back?"
date: 2010-05-28
forum: General Help
---

### Post by tahitiwibble on 2010-05-28
Hi all,

I wanted to change the resolution of the splash screen because it looked too big for the screen's area. I installed Start-up Manager, which I don't like any more because of this issue, and changed the resolution. The result was a garbled screen and so I reset to the original settings and re-booted. Now I have another garbled screen with 2 side-by-side very fuzzy/unreadable "Ubuntu" images.

Please would someone be good enough to help me get back to the original splash screen.

---

### Post by tahitiwibble on 2010-05-31
Any ideas?

---

### Post by tahitiwibble on 2010-06-03
:icon_frown:

---

### Post by tahitiwibble on 2010-06-05
Does any of the weekend crew have an idea? :)

---

### Post by Jakiejake on 2010-06-05
> gksudo gedit /etc/default/grub
In the line that says > GRUB_CMDLINE_LINUX="799" remove the 799

---

### Post by luigi_mb on 2010-06-05
Or replace "799" with "nomodset"

/luigi

---

### Post by tahitiwibble on 2010-06-05
I'm really grateful to you two guys for helping out :)

This is what the file you suggest modifying looks like;

> GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=15
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=769"

Should I just go ahead and change "769" ?

---

### Post by tahitiwibble on 2010-06-05
Bingo! I finally jumped in and did it and it worked. Here's exactly how:

**Step 1**
```
dad@dad-desktop:~$ gksudo gedit /etc/default/grub
```

**Step 2** 
Changed > GRUB_CMDLINE_LINUX=" vga=769"
to 
> GRUB_CMDLINE_LINUX="nomodset"

**Step 3**
```
dad@dad-desktop:~$ sudo update-grub
```

Thanks to jake & luigi :)

---

### Post by Jakiejake on 2010-06-05
> **tahitiwibble said:**
> Bingo! I finally jumped in and did it and it worked. Here's exactly how:

**Step 1**
```
dad@dad-desktop:~$ gksudo gedit /etc/default/grub
```

**Step 2** 
Changed 
to 


**Step 3**
```
dad@dad-desktop:~$ sudo update-grub
```

Thanks to jake & luigi :)

Awesome!
Glad I could help :)

---

### Post by diablo75 on 2010-06-06
OP, glad to see you got this solved.  I'm experiencing the same issue and I was wondering if you could tell me what kind of video card you have.  I'd like to try what you did when I get home.

---

### Post by tahitiwibble on 2010-06-07
> **diablo75 said:**
> OP, glad to see you got this solved.  I'm experiencing the same issue and I was wondering if you could tell me what kind of video card you have.  I'd like to try what you did when I get home.

Good morning Canada,

I have this graphics card. [http://www.nvidia.com/object/product_geforce_9500gt_us.html]("http://www.nvidia.com/object/product_geforce_9500gt_us.html")  It's a little bit of an overkill for what I do but it sure works well.

Have a good one :)

---

