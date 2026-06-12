---
title: "why UBUNTU 10.10 did not support my computer ?"
date: 2011-07-06
forum: General Help
---

### Post by vikash_chandola on 2011-07-06
Hello!! 

I want to taste Linux. Ubuntu is best for beginners like me. some months ago i download Ubuntu 10.10 I make it's boot able CD and boot from that. In starting everything was fine A screen appear asking what you want to do **try Ubuntu** & **install Ubuntu** i click try Ubuntu just after that problem appear it does not run in GUI it was in terminal(a text mode screen). I try many times but every time same thing occur. I thought it will run in GUI after install so i install that till install it was running in GUI and everything can be done with mouse but after installation when i reboot it was in terminal(a text mode screen). I don't know why this error is happening with me. why i am so unlucky. My system is capable to run windows 7 then why not Ubuntu. It has 1 GB RAM, 2.67 GHz Intel Pentium 4 processor. enough to run any Linux distro. This error may be due to [color=red]graphic card[/color] I have integrated graphic card.As i have already mentioned it can run windows 7 which has minimum graphic requirement of 128 MB. 
Some information about my system is here.
system model **z945c010**
display device card name: **Intel(R) 82945G Express Chipset Family (Microsoft Corporation - WDDM 1.0)**
32 bit machine (I download 32 bit version)
**Intel(R) Pentium(R) 4 CPU 2.66GHz 2.67 GHz**

Need more information ask i will try to provide.

I will really thankful to those who helps

---

### Post by snowpine on 2011-07-06
Give Xubuntu a try... it does not use desktkop effects and might have better support for your graphics card. :)

You might also try the current 11.04 release. It is possible you're experiencing a bug that has been fixed in the last 6 months.

---

### Post by vikash_chandola on 2011-07-06
One information i want ot ad with my question is that Linux mint 10 also show similar error. Open suse 11.3 gmome run but only for some minutes after soem minutes it hags and all input devices keyboard , mouse stopped working i don't know is it working internally or not.
> **snowpine said:**
> Give Xubuntu a try... it does not use desktkop effects and might have better support for your graphics card. :)

You might also try the current 11.04 release. It is possible you're experiencing a bug that has been fixed in the last 6 months.
**What is difference in these different versions of Ubuntu?**
Does Xubuntu has minimum requirement of all the versions what about Lubuntu it uses lxde which requires minimal graphic memory. I am searching for minimal system requirement version because i don't want to waste time in downloading. 
Recently i tried Fedora 15 Gnome 3 that does not able to load Gnome 3 else that run fine but i did not like many of that's thing so i remove that.

---

### Post by Wim Sturkenboom on 2011-07-06
The downloads will be more or less the same size; no relationship with lightweight in this case.

---

### Post by vikash_chandola on 2011-07-06
> **Wim Sturkenboom said:**
> The downloads will be more or less the same size; no relationship with lightweight in this case.
I am downloading XUbuntu 11.04 I want to know **xubuntu-11.04-desktop-i386.iso ** is 32 bit or 64 bit OS. most probably it should 32 bit.

---

### Post by dino99 on 2011-07-06
[http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=de&tl=en&u=https%3A%2F%2Fstephanaltmann.wordpress.com%2F2010%2F12%2F01%2Fubuntu-lucidmaverick-und-intel-82945ggz%2F](http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=de&tl=en&u=https%3A%2F%2Fstephanaltmann.wordpress.com%2F2010%2F12%2F01%2Fubuntu-lucidmaverick-und-intel-82945ggz%2F)

sudo apt-get install xserver-xorg-video-intel

---

### Post by dFlyer on 2011-07-06
What makes you believe that Ubuntu 10.10 doesn't support your computer?

---

### Post by snowpine on 2011-07-06
> **vikash_chandola said:**
> One information i want ot ad with my question is that Linux mint 10 also show similar error. Open suse 11.3 gmome run but only for some minutes after soem minutes it hags and all input devices keyboard , mouse stopped working i don't know is it working internally or not.

**What is difference in these different versions of Ubuntu?**
Does Xubuntu has minimum requirement of all the versions what about Lubuntu it uses lxde which requires minimal graphic memory. I am searching for minimal system requirement version because i don't want to waste time in downloading. 
Recently i tried Fedora 15 Gnome 3 that does not able to load Gnome 3 else that run fine but i did not like many of that's thing so i remove that.

Ubuntu uses the Gnome desktop and Compiz Desktop Effects, which don't work well with Intel 945G graphics (in my experience).

Xubuntu uses the Xfce destkop, which has no desktop effects and (I hope) will not give your Intel 945G any problems.

Good luck! :)

---

