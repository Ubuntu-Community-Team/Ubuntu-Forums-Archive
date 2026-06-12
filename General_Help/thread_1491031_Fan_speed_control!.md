---
title: "Fan speed control!"
date: 2010-05-23
forum: General Help
---

### Post by jinba.ittai on 2010-05-23
Ive searched, and searched. Found a few posts, but none relating to 10.04, and im not to handy with the Terminal. IS there a simple app for fan speed control?

---

### Post by Jakiejake on 2010-05-23
Search "thinkfan" in the ubuntu software (if you are in 10.04) or in the package manager (if you are in 9.10 or lower)

---

### Post by Jakiejake on 2010-05-24
> **Jakiejake said:**
> Search "thinkfan" in the ubuntu software (if you are in 10.04) or in the package manager (if you are in 9.10 or lower)

Did it work?

---

### Post by jinba.ittai on 2010-05-24
> **Jakiejake said:**
> Did it work?

Sorry for the late reply, didnt have internet for a few days. I downloaded it, but have no clue how to use it or where to find it lol

<<<<----- THis guys is an ubernoob!

---

### Post by Jakiejake on 2010-05-25
Google Is your friend
I'll look into it tomorrow till then as I said before
Google Is your friend
Also try searching the Ubuntu Software Center and the Package/Software Manager For "fan control"
Good Luck

---

### Post by inameiname on 2010-05-25
Here you go. I found the latest deb file of it, which you can just double click and install just like that. The file I'm guessing you downloaded was a tar file, which could be a tad tricky for newer folks to install.

[http://packages.debian.org/sid/i386/thinkfan/download](http://packages.debian.org/sid/i386/thinkfan/download)

Sadly, it seems the terminal is required, but it doesn't look too hard.

To get a list of possible commands:

thinkfan -h

Usage: thinkfan [-hnqzD [-b BIAS] [-c CONFIG] [-s SECONDS] [-p [SECONDS]]]
 -h  This help message
 -s  Maximum cycle time in seconds (Integer. Default: 5)
 -b  Floating point number (0 ~ 20) to control rising edge
     temperature biasing strength (see README). Default: 5.0
 -c  Load different configuration file (default: /etc/thinkfan.conf)
 -n  Do not become a daemon and log to terminal & syslog
 -q  Be quiet (no status info on terminal)
 -z  Assume we don't have to worry about resuming when using the sysfs
     interface (see README!)
 -p  Use the pulsing-fan workaround (for older Thinkpads). Takes an optional
     floating-point argument (0 ~ 10s) as depulsing duration. Default 0.5s.
 -D  DANGEROUS mode: Disable all sanity checks. May damage your hardware!!

---

### Post by 3rdalbum on 2010-05-25
Your BIOS should have the option to control your fans. I'd recommend using that; it'll work better and more reliably than any extra software. And it'll work more efficiently and faster than if you manually set the fan speed.

---

### Post by jinba.ittai on 2010-05-25
> **3rdalbum said:**
> Your BIOS should have the option to control your fans. I'd recommend using that; it'll work better and more reliably than any extra software. And it'll work more efficiently and faster than if you manually set the fan speed.

Unfortunately you cant access the bios while on an operating system =[

Like the accessibility of being about to control them while on ubuntu.

---

### Post by jinba.ittai on 2010-05-25
> **inameiname said:**
> Here you go. I found the latest deb file of it, which you can just double click and install just like that. The file I'm guessing you downloaded was a tar file, which could be a tad tricky for newer folks to install.

!


I just installed the one from the ubuntu software, but thanks for the commands! Gona save that in a text file and see what i can do!

---

### Post by Jakiejake on 2010-05-26
> **Sandy V Jina said:**
> Unfortunately you cant access the bios while on an operating system =[

Like the accessibility of being about to control them while on ubuntu.

Yes Thats Why You Reboot :P
But I understand at certain times you need to change it without rebooting

---

### Post by Jakiejake on 2010-05-26
> **3rdalbum said:**
> Your BIOS should have the option to control your fans. I'd recommend using that; it'll work better and more reliably than any extra software. And it'll work more efficiently and faster than if you manually set the fan speed.

Agreed :guitar:

---

### Post by Jakiejake on 2010-05-26
> **Sandy V Jina said:**
> I just installed the one from the ubuntu software, but thanks for the commands! Gona save that in a text file and see what i can do!

Good Luck!

---

### Post by inameiname on 2010-05-26
Yeah, there are times when you it may be worthwhile without a restart, but that's never been an issue for me. Hopefully that application will work for you. :)

---

### Post by jinba.ittai on 2010-05-26
> **inameiname said:**
> Yeah, there are times when you it may be worthwhile without a restart, but that's never been an issue for me. Hopefully that application will work for you. :)

Yep, everything works fine!! Thanks guys!

---

### Post by Jakiejake on 2010-05-27
> **Sandy V Jina said:**
> Yep, everything works fine!! Thanks guys!

Awesome
Please Mark As Solved, Have A Good Day And Enjoy Ubuntu!

---

### Post by ola on 2010-05-29
Did thinkfan work for you?

I installed it and started it but my fans are still loud even though my temps looks ok.

```

$ acpi -t
Thermal 0: ok, 37.0 degrees C

```

Any ideas?

---

### Post by xMohd on 2011-05-27
Hello, am using ubuntu 11.04 32bits. Installed thinkfan using Synaptic. am kinda new to ubuntu. I ran the thinkfan -h but have no idea what to do to control the noise level & speed of fans. My BIOS settings have "Super Quiet" set for fans, & when I reboot into windows, no noise. Rebooting into Ubuntu, is a problem, sounds like a plane taking off :) HELP please.

---

