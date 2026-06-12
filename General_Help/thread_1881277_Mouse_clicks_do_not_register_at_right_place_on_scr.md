---
title: "Mouse clicks do not register at right place on screen"
date: 2011-11-15
forum: General Help
---

### Post by Vy0m on 2011-11-15
Hello everyone. I installed Linux for the first time yesterday.

Since I had a Pen 3 system with me, I decided to give it a breather with Lubuntu 11.10.
But I am facing a strange problem. Mouse clicks are not registering at right place on the screen. I have to click a few inches to the left to press any corresponding button.

I have **[uploaded a video too]("http://www.youtube.com/watch?v=P98fy21KxiU")**, to explain what exactly is happening. It's a short (1:39) vid.


Expecting that this problem can be solved. Or I would have to try another distro.

Thanks in advance.

---

### Post by MG&amp;TL on 2011-11-15
No doubt it can be solved. The question is how long it will take.

What sort of mouse and video card are you using?

---

### Post by Vy0m on 2011-11-15
> **MG&TL said:**
> No doubt it can be solved. The question is how long it will take.

What sort of mouse and video card are you using?

I am using HP USB mouse, and following is the output of lspci command on my terminal.

```

vineet@vineet-OptiPlex:~$ lspci
 
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 11)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 11)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 11)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 11)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 11)
01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
vineet@vineet-OptiPlex:~$

```

([http://pastebin.com/ZAHyDyCR](http://pastebin.com/ZAHyDyCR))

---

### Post by amjjawad on 2011-11-15
> **Vy0m said:**
> I am using [COLOR=Red]**HP USB mouse**[/COLOR], and following is the output of **[COLOR=Red]lspci[/COLOR]** command on my terminal.

```

vineet@vineet-OptiPlex:~$ lspci
 
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 11)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 11)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 11)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 11)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 11)
01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
vineet@vineet-OptiPlex:~$

```([http://pastebin.com/ZAHyDyCR](http://pastebin.com/ZAHyDyCR))


Hello and Welcome!

The correct command is: **lsusb**

```
Bus 004 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
```

---

### Post by amjjawad on 2011-11-15
> **Vy0m said:**
> Expecting that this problem can be solved. Or I would have to try another distro.

Number of **[active distributions]("http://distrowatch.com/search.php?status=Active")** in the database: **314**
[http://distrowatch.com/weekly.php?issue=20111114](http://distrowatch.com/weekly.php?issue=20111114)

All these distributions share the same core which is the Kernel which is Linux. The Desktop Environment is different. Default Programs are different. Names are different. Philosophies are different. IMHO, one needs to use whatever works for him/her. However, NO OS is perfect, period.

Having that said, please do not lose hope, you just started :)

As my friend said previously, everything has a solution but it's a matter of how long that will take. Please be patient :)

---

### Post by MG&amp;TL on 2011-11-15
> **amjjawad said:**
> Number of **[active distributions]("http://distrowatch.com/search.php?status=Active")** in the database: **314**
[http://distrowatch.com/weekly.php?issue=20111114](http://distrowatch.com/weekly.php?issue=20111114)

All these distributions share the same core which is the Kernel which is Linux. ... NO OS is perfect, period.



mmmm....I have a feeling this is something to do with X, as that's what manages stuff like that. Anybody know anything about X? My point with the quote being that X is common to most linux distributions too.

---

### Post by amjjawad on 2011-11-15
> **MG&TL said:**
> mmmm....I have a feeling this is something to do with X, as that's what manages stuff like that. Anybody know anything about X? My point with the quote being that X is common to most linux distributions too.

[http://www.x.org/wiki/](http://www.x.org/wiki/)
[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

---

### Post by Vy0m on 2011-11-18
> **amjjawad said:**
> Hello and Welcome!

The correct command is: **lsusb**

```
Bus 004 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
```

Well, using lsusb command, the output is:

```
Bus 001 Device 002: ID 0461:4d0f Primax Electronics, Ltd
```

But I don't think the problem is with the mouse. Since the problem persist even when I use a PS/2 Mouse.

---

### Post by Vy0m on 2011-11-19
Anyone? :(

---

### Post by Vy0m on 2011-11-23
Still no one? Should I ditch lubuntu for my pen 3 then? :(

---

### Post by Rodney9 on 2011-11-24
> **Vy0m said:**
> Still no one? Should I ditch lubuntu for my pen 3 then? :(

Have you tried a re-install ?

Did you check the media, [mdsum]("https://help.ubuntu.com/community/HowToMD5SUM")

Try a different mouse.

You could try a different distro like puppy and see if the same problem exists.

Here is a list of other lightweights - [http://tuxradar.com/content/whats-best-lightweight-linux-distro](http://tuxradar.com/content/whats-best-lightweight-linux-distro)

Rodney

---

### Post by amjjawad on 2011-11-27
Few questions that will help us to help you:


[LIST=1]
[*]How did you install Lubuntu?
[*]Have you tried it from the LiveCD or LiveUSB before installing it?
[*]Have you checked MD5SUM right after downloading and before burning the LiveCD or creating the LiveUSB?
[*]What software you used to create the Live Media (CD or USB)?
[*]Is it happening all the time or randomly?
[*]Is this a Desktop PC or Laptop?
[*]Are you sure all your hardware working correctly? is it just the mouse?
[*]Have you tried another mouse?
[/LIST]


Thank you!

---

### Post by amjjawad on 2011-11-27
> **Vy0m said:**
> Still no one?
Sorry for not showing up. I didn't login for quite sometime but I'm trying to login from time to time. 

> Should I ditch lubuntu for my pen 3 then? :(
Please do NOT give up UNLESS you try everything. I still hope we can fix that so please have a look at the previous post of mine and answer the questions if you don't mind :)

Thanks!

---

### Post by Vy0m on 2012-03-29
I apologize for not showing up in previous months.
The thing is that the PC (where this problem occur) was my secondary PC. And since then I moved on to XP for that pen 3.

But I am using Ubuntu 11.10 on my Primary PC now. (Pen 4, 2.4 GHz). Where I am again facing some problem in not getting the Native Resolution on my 1440 x 900 res monitor.
My friends said, it's because of crappy Intel drivers. So I am guessing I will have to live with non-native (low) resolution on Ubuntu too.
Also discussing that here, won't serve the purpose of this thread.

Thanks anyway for your replies. If ever I try to use Lubuntu again on the pen 3, I would bump this thread again. And then maybe we could find the solution to the problem! ;)

---

### Post by amjjawad on 2012-04-01
> **Vy0m said:**
> I apologize for not showing up in previous months.
The thing is that the PC (where this problem occur) was my secondary PC. And since then I moved on to XP for that pen 3.

But I am using Ubuntu 11.10 on my Primary PC now. (Pen 4, 2.4 GHz). Where I am again facing some problem in not getting the Native Resolution on my 1440 x 900 res monitor.
My friends said, it's because of crappy Intel drivers. So I am guessing I will have to live with non-native (low) resolution on Ubuntu too.
Also discussing that here, won't serve the purpose of this thread.

Thanks anyway for your replies. If ever I try to use Lubuntu again on the pen 3, I would bump this thread again. And then maybe we could find the solution to the problem! ;)

Sorry for not replying, I've been so busy lately with lots of stuff :)

If you still want to give it a go, I will gladly go through your thread again and guide you to how to fix this once and for all.

Fact is, I'm so much focusing on Lubuntu 12.04 right now but that doesn't mean I can't help someone who needs help.
Don't give up so easily and if you would like to help Lubuntu, we will be very glad if you could test Lubuntu 12.04 beta 2 and see if the same issue will happen again or not :)

Let me know and I'm here if you need anything!

---

### Post by marinara on 2012-04-01
IMHO it's the bad drivers.  Not sure if you have an alternative

---

