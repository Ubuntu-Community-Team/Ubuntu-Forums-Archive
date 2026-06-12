---
title: "Need help burning a DVD"
date: 2010-04-09
forum: General Help
---

### Post by sincerelyydavid on 2010-04-09
so i have an iso i want to burn on dvd, and have my laptop boot into it when it first starts up. how can i burn this on ubuntu? what burners can i use? i tried searching for nero in software center, but couldn't find it.

---

### Post by drewsus on 2010-04-09
I use GnomeBaker

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gnomebaker
```

And what is this an .iso of? Ubuntu Live CD? Because you could save a DVD/CD and use the USB Start Up Disk Creator and just boot from that USB.

---

### Post by sincerelyydavid on 2010-04-09
yeah, i'm trying to burn ubuntu.
i have brasero pre-installed. can this work too? i just drag the .iso on there, and it'll be able to boot from startup, right, or do i need to make it bootable somehow...?

---

### Post by drewsus on 2010-04-09
Yup, that will work fine and it will be bootable. I just prefer GnomeBaker :)
Like I said, you can try doing it on a USB stick if you like too. Your computer just has to be able to boot from USB. 
But I think you are good to go now!

Drew

---

### Post by gordintoronto on 2010-04-09
> **sincerelyydavid said:**
> yeah, i'm trying to burn ubuntu.
i have brasero pre-installed. can this work too? i just drag the .iso on there, and it'll be able to boot from startup, right, or do i need to make it bootable somehow...?

I don't know if that will work.

Here's how I do it: I insert the empty CDR, and when the popup appears I cancel it!

Then I start Brasero from the Sound & Video menu, and select "Burn Image". It prompts, "click here to select an image," I do that and click on "burn." So far, it works every time.

---

### Post by RedRat on 2010-04-09
Of course I am running 8.04 LTS but I have found Brasero to be a royal pain. With GnomeBaker I have had no problems, I highly recommend it. I have also used K3b on occasion and also like it too (this is a kubuntu app).

---

### Post by drewsus on 2010-04-09
@RedHat
yeah I find Brasero to be a pain too. Def still recommend GnomeBaker

---

### Post by intrader on 2010-04-25
I am having problems with Brasero on ubuntu 9.10 (which has a lot of problems with sluggish UI).
Well when I click on Burn Image, it pops up a 'Image Burning Setup' screen asking for 'Click here to select image' when I select the iso, Brasero shutds down without any error message.
JUNK

---

### Post by RedRat on 2010-04-25
> **intrader said:**
> I am having problems with Brasero on ubuntu 9.10 (which has a lot of problems with sluggish UI).
Well when I click on Burn Image, it pops up a 'Image Burning Setup' screen asking for 'Click here to select image' when I select the iso, Brasero shutds down without any error message.
JUNK
Besides GnomeBaker I have also installed k3b, a Kubuntu app, and I like it. It is in Synaptic, at least for 8.04. Brasero is a pain.

---

### Post by intrader on 2010-04-25
> **drewsus said:**
> @RedHat
yeah I find Brasero to be a pain too. Def still recommend GnomeBaker

I have installed GnomeBaker as described above and burned an image without problem.

From drewsus:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gnomebaker

Thanks for the information.

---

### Post by RedRat on 2010-04-25
> **intrader said:**
> I have installed GnomeBaker as described above and burned an image without problem.

From drewsus:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gnomebaker

Thanks for the information.
Great! You might also want to give k3b a shot too. I know its a kde app but runs quite nicely in Gnome.

---

