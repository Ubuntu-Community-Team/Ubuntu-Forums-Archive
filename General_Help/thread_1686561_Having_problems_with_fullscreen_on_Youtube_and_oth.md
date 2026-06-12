---
title: "Having problems with fullscreen on Youtube and other videos"
date: 2011-02-12
forum: General Help
---

### Post by cblnchat on 2011-02-12
Im just having a small problem with fullscreen on Youtube and other video sites when i go fullscreen, absolutely nothing happens.  It goes fullscreen but everything stops moving and the computer freezes for a few seconds until i take it out of full screen.  Is there anything i can do to fix this.

Thanks

---

### Post by I&#9829;HTML5 on 2011-02-12
I am having the same problem. Most of the time, you can pause the video, go fullscreen, then hit play and it should work fine.

---

### Post by cblnchat on 2011-02-12
> **I&#9829 said:**
> I am having the same problem. Most of the time, you can pause the video, go fullscreen, then hit play and it should work fine.

I tried that and it didnt work.  Ive also tried reloading the page.  Ive tried everything! haha!

---

### Post by Habitual on 2011-02-12
I've heard Sooooooo many tips to 'fix' this.
de-install flash and re-install it being the most common.
Here's what I did without re-installing flash.

```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```

Restart the browser.

Good Luck and HTH

---

### Post by I&#9829;HTML5 on 2011-02-12
That worked for me. Finally I can switch to fullscreen *without* pausing! Thanks!

---

### Post by Habitual on 2011-02-13
Glad it worked out.

---

### Post by excalibas on 2011-02-27
Thanks, also worked for me with Ubuntu 10.04 Lucid

---

### Post by cblnchat on 2011-03-01
> **Habitual said:**
> I've heard Sooooooo many tips to 'fix' this.
de-install flash and re-install it being the most common.
Here's what I did without re-installing flash.

```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```Restart the browser.

Good Luck and HTH

That seems to have worked.
Thanks very much

---

### Post by opiumpoetry on 2011-03-02
> **Habitual said:**
> I've heard Sooooooo many tips to 'fix' this.
de-install flash and re-install it being the most common.
Here's what I did without re-installing flash.

```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```

Restart the browser.

Good Luck and HTH

this worked for me too but first i had to uninstall adobe. thanx 4 yr assistance!

---

### Post by gmolivier on 2011-04-08
> **opiumpoetry said:**
> this worked for me too but first i had to uninstall adobe. thanx 4 yr assistance!
i'm a novice...where do i put the code?

---

### Post by cblnchat on 2011-04-09
> **gmolivier said:**
> i'm a novice...where do i put the code?
 You put it in the Terminal.  Usually in Main Menu>Accessories.  Type or copy the code exactly as they show it.

---

### Post by andyatnimbin on 2011-04-09
> **gmolivier said:**
> i'm a novice...where do i put the code?
Applications>Accessories>Terminal

Right click and paste, you'll be asked for your passowrd

---

### Post by andyatnimbin on 2011-04-09
> **Habitual said:**
> I've heard Sooooooo many tips to 'fix' this.
de-install flash and re-install it being the most common.
Here's what I did without re-installing flash.

```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```

Restart the browser.

Good Luck and HTH

This worked for me thanks,I've had this problem for about a year, great solution!

---

### Post by opiumpoetry on 2011-04-27
> **gmolivier said:**
> i'm a novice...where do i put the code?

open a terminal. Applications>Accessories>Terminal

---

### Post by josiah14 on 2011-06-28
This is a good place to go to learn Linux:
[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224)

---

