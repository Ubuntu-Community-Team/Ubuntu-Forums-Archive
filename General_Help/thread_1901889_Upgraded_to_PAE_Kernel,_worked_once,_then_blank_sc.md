---
title: "Upgraded to PAE Kernel, worked once, then blank screen on boot"
date: 2011-12-29
forum: General Help
---

### Post by Hovercat on 2011-12-29
I've been using the 2.6.38-13-generic kernel, but then I realized I was only getting 2.6GB of RAM (due to integrated graphics) of my available 8GB, so I installed 2.6.38-13-generic-pae kernel. It worked for the first time no problem, and then when I later had to restart my computer, it shows up as a blank screen until I re-install the kernel from 2.6.38-13-generic. Recovery mode does not work either.

How can I fix this?

---

### Post by BC59 on 2011-12-29
What type of architecture is using your computer? Is it a 32bit?

---

### Post by Hovercat on 2011-12-29
> **BC59 said:**
> What type of architecture is using your computer? Is it a 32bit?

I'm on the 32-bit OS, but it's a 64-bit CPU. I only went with the 32-bit installation because it said 32-bit was recommended on [www.ubuntu.com](www.ubuntu.com)

---

### Post by BC59 on 2011-12-29
PAE kernel supports well the 4GB RAM but after that the remainder is slower. I don't know if your problem is connected to this. 
The recommendation for 32bit is old. The issue connected to this is solved and the use of 64bit is highly recommended.

---

### Post by Hovercat on 2011-12-29
> **BC59 said:**
> PAE kernel supports well the 4GB RAM but after that the remainder is slower. I don't know if your problem is connected to this. 
The recommendation for 32bit is old. The issue connected to this is solved and the use of 64bit is highly recommended.

Is there any way to upgrade to 64-bit without losing my installed applications, themes, etc?

If needed, I will update to 11.10 (I was planning to do so anyway at some point).

---

### Post by BC59 on 2011-12-29
There is a way, but is really complicated, so I suggest you to do a fresh 11.10 64bit install.

---

### Post by Hovercat on 2011-12-29
> **BC59 said:**
> There is a way, but is really complicated, so I suggest you to do a fresh 11.10 64bit install.

So the really only way would be to backup my package list and copies of other config files?

And how complicated is it? Is there a tutorial I could look at?

---

### Post by BC59 on 2011-12-29
Well...there is no much you could do. 11.10 is enough different than 11.04 and much more different than the previous versions.
You could make a list with your applications installed, to download them again in 11.10 from the Ubuntu Software Center.

---

### Post by BC59 on 2011-12-29
About 11.10 installation
A very good guide is here, to solve problems with drivers etc.
[http://ubuntuguide.org/wiki/Ubuntu:Oneiric](http://ubuntuguide.org/wiki/Ubuntu:Oneiric)
And a do list after installation is here:
[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by Hovercat on 2011-12-29
> **BC59 said:**
> About 11.10 installation
A very good guide is here, to solve problems with drivers etc.
[http://ubuntuguide.org/wiki/Ubuntu:Oneiric](http://ubuntuguide.org/wiki/Ubuntu:Oneiric)
And a do list after installation is here:
[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

Alright, thanks for your help.

---

