---
title: "Ubuntu Hangs on Startup"
date: 2010-03-28
forum: General Help
---

### Post by mrmeee17 on 2010-03-28
If I manually press enter when grub loads, Ubuntu boots up fine.

But if I let it automatically time out, Ubuntu hangs on the black screen with the logo in the middle and I have to power my computer off.

I dual boot with Windows 7 on another partition.

Any ideas? Thank you.

(Am very new to Linux btw.)

---

### Post by sgosnell on 2010-03-28
What version of Ubuntu?  What kind of computer, what video card, etc?  Hard to give any advice without more information.

---

### Post by mrmeee17 on 2010-03-28
9.10. I run on an MSI P55-CD53 motherboard with i7-860 processor and ATI Radeon 5850 video card.

Any more information you need? Thank you.

I also recently installed the ATI Catalyst&#8482; 10.3 Proprietary Linux x86 Display Driver from AMD's website and I think that is what might have caused it. However it is necessary that I leave it installed or my screen displays a weird assortment of colours which makes it impossible to see anything clearly.

---

### Post by mrmeee17 on 2010-03-28
Ok further testing has revealed that it is actually my restart button which is bugged.

If I press 'shut down' and boot manually, everything works as expected.

But if I press 'restart', it hangs on start up.

Perhaps the problem lies with the code for 'restart'?

My install for Ubuntu is very new btw. Just installed it yesterday and apart from updating stuff, very little has been done to it.

---

### Post by sgosnell on 2010-03-28
I'm guessing, but it sounds like something in your restart script is the problem.  You might try a reinstall and see if that helps.  I'm far from an expert on grub and startup/shutdown scripts.  Maybe someone with more experience there will be along.

---

### Post by mrmeee17 on 2010-03-29
Yes I am actually guessing the same, I'm pretty sure grub is the problem.

Can someone teach me how to do a *clean* reinstall of grub? I tried various ways but I think I ended up screwing everything up with versions of grub-legacy and grub2 etc. I just want a clean reinstall of grub2.

---

### Post by mrmeee17 on 2010-03-29
No one knows how to do a real clean reinstall of grub2?

---

### Post by Gemnoc on 2010-03-29
Have you looked at the doc?

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

See point #11.

---

### Post by mrmeee17 on 2010-03-30
> **Gemnoc said:**
> Have you looked at the doc?

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

See point #11.

Tried doing that but it appears there is actually nothing wrong with grub.

And after even further testing I have found out that my earlier conjecture was false - it seems to happen totally randomly. Sometimes I can boot and sometimes it just hangs on the black screen with the logo in the middle.

I have no idea what causes it or how to fix it and it is doing my head in :(

---

### Post by theozzlives on 2010-03-30
You mention GRUB2, so I assume you're using Karmic or Lucid Beta 1?

---

### Post by mrmeee17 on 2010-03-30
> **theozzlives said:**
> You mention GRUB2, so I assume you're using Karmic or Lucid Beta 1?

Using Karmic Koala.

---

### Post by theozzlives on 2010-03-30
> **mrmeee17 said:**
> Using Karmic Koala.

Karmic's a bit buggy at times. Since it's a new install, why don't you try Lucid Lynx. Anyhow, use the live CD, gparted and post a screenshot of sda (shift+prtscr).

---

### Post by NiGhtMarEs0nWax on 2010-03-30
grub that comes shipped with 9.10 is still in beta. i have had problems with it in the past, where the timer would disappear.

maybe you can try reinstalling grub. make a backup of the config file first though.

---

### Post by bcbc on 2010-03-30
> **theozzlives said:**
> why don't you try Lucid Lynx

It's not a good idea to try Lucid as it's still in beta development - unless you are prepared for crashes and potential loss of data.

---

### Post by theozzlives on 2010-03-30
> **NiGhtMarEs0nWax said:**
> grub that comes shipped with 9.10 is still in beta. i have had problems with it in the past, where the timer would disappear.

maybe you can try reinstalling grub. make a backup of the config file first though.

If your getting a screen with the Circle of Friends (Ubuntu logo), your getting past GRUB and going into X. I suspect a driver. Hold down shift when it boots and choose recovery from the menu. Let's see where it stops.

---

### Post by mrmeee17 on 2010-03-30
> **theozzlives said:**
> Karmic's a bit buggy at times. Since it's a new install, why don't you try Lucid Lynx. Anyhow, use the live CD, gparted and post a screenshot of sda (shift+prtscr).

[http://img338.imageshack.us/img338/8108/25584844.png](http://img338.imageshack.us/img338/8108/25584844.png)

sda1 is where my Windows 7 installation is located.

> **theozzlives said:**
> If your getting a screen with the Circle of Friends (Ubuntu logo), your getting past GRUB and going into X. I suspect a driver. Hold down shift when it boots and choose recovery from the menu. Let's see where it stops.

[http://img709.imageshack.us/img709/51/10096357.jpg](http://img709.imageshack.us/img709/51/10096357.jpg)

The most annoying thing is that it's not like it always fails to boot - sometimes it boots up fine but other times it doesn't, so I am totally lost as to what causes it. Anyhow, I did what you suggested twice and both times it stopped there.

---

### Post by mrmeee17 on 2010-04-01
Anyone?

---

### Post by john newbuntu on 2010-04-01
At your own risk try:
sudo grub-editenv unset recordfail
OR 
Remove /boot/grub/grubenv file.

Prior to this, read through: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

