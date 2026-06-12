---
title: "Fan is on too high on Ubuntu 11.04 Natty"
date: 2011-05-17
forum: General Help
---

### Post by xxhopingtearsxx on 2011-05-17
Everytime I try to use Ubuntu, I like it. Then I remember what always switches me back to Windows.. my fan. It's so loud. It wasn't high before, but I think an update I did recently messed it up. My fan is on too high, as if I'm running high-CPU programs, but I'm not. I'm jus
t on Google Chrome. I have a Toshiba Satellite L305-S5955 btw.

I've asked this question many times, so I'm going to answer questions people tend to ask so we can get right to solving my problem:

No, my laptop is not dirty.
Yes, I do shut down my computer often.
No, this laptop didn't do this on Windows or Hackintosh.
No, I'm sure nothing is using up my CPU and Memory at the moment.
Yes, it's done it on previous Ubuntu versions.
No, I am pretty sure I do not have to open up my laptop and clean it.



Please help. I'm currently back to using Windows 7 (unfortunately) since I don't want my fan on too high. I like my computer quiet. I'm tempted to reinstall Ubuntu 11.04 and never, ever, ever update.. Because this wasn't doing this before.

---

### Post by xxhopingtearsxx on 2011-05-17
I followed a step online that installing Kubuntu via terminal (sudo apt-get install kubuntu-desktop) would help..

So far, it looks like it works.. like last time. I'll change the status of this thread to SOLVED once I try it out a little more.

You don't have to use Kubuntu btw. Just have it installed.. But you should give it a shot.

---

### Post by Hedgehog1 on 2011-05-17
This works for many laptops to bring the fan under control in Ubuntu:

```
gksudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash **acpi_osi=\\\"Linux\\\""**
```

There are a total of **4 double quotes** in this line (2 side-by-side at the end)

Then do:

```
sudo update-grub
```

**And reboot. The operation of this will keep your computer running cooler.**

In case you are wondering WHY all these slashes, it is because this text string gets processed twice before it is used to boot the kernel:

In /etc/default/grub it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
```

Which gets converted by the update-grub in /boot/grub/grub.cfg as:
```
linux /boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi=\"Linux\"
```

The command is then passed to the kernel when run by grub as:
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi="Linux"
```

See how easy that (isn't) to follow?


***The Hedge***

:KS

---

### Post by xxhopingtearsxx on 2011-05-17
Pftt that isn't hard.
I wonder why would Kubuntu have fixed my fan though. (Not that I regret it or anything, since I missed that light look of it).
At least it worked.

---

### Post by xxhopingtearsxx on 2011-05-17
Kubuntu didn't work. Try that code.
Except change that line he/she said to change to:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\**"**"Linux\\\""

---

### Post by faceonline on 2011-05-17
Hey, well there's [a bug report for this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/748574?comments=all") but its just confirmed at the moment -- I'm gonna try the grub-acpi fix first, but I thought I'd share my 'fix'

1) Put your comp to 'suspend' i.e. suspend to ram
2) Start it up again.

Seems to re-engage the whole variable cpu fan thing, but the trade off is that the fan doesn't ever seem to be fully off on a laptop.

Not much of a workaround, I know, but it might help 'til it gets fixed :)

---

### Post by Hedgehog1 on 2011-05-17
> **xxhopingtearsxx said:**
> Kubuntu didn't work. Try that code.
Except change that line he/she said to change to:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\**"**"Linux\\\""

It's a 'He said'.

The above line is out of balance, you much have an even number of double quotes.

GRUB_CMDLINE_LINUX_DEFAULT=[COLOR="Red"](1)[/COLOR]"quiet splash acpi_osi=\\\[COLOR="red"](2)[/COLOR]"Linux\\\[COLOR="red"](3)[/COLOR]"[COLOR="red"](4)[/COLOR]"

***The Hedge***

:KS

---

### Post by xxhopingtearsxx on 2011-05-18
> **Hedgehog1 said:**
> It's a 'He said'.

The above line is out of balance, you much have an even number of double quotes.

GRUB_CMDLINE_LINUX_DEFAULT=[COLOR="Red"](1)[/COLOR]"quiet splash acpi_osi=\\\[COLOR="red"](2)[/COLOR]"Linux\\\[COLOR="red"](3)[/COLOR]"[COLOR="red"](4)[/COLOR]"

***The Hedge***

:KS


I did that and I got..

joey@joey-ubuntu:~$ sudo update-grub
/etc/default/grub: 11: Syntax error: "(" unexpected
joey@joey-ubuntu:~$ 


I was just sitting in my room minding my own business, and suddenly WHOOSH. It's very frustrating. It goes beyond the terminal, I just want my Wednesday to be quiet.

)=

EDIT: Removed the (1)(2) and the extra ".

I have 


joey@joey-ubuntu:~$ sudo update-grub
/etc/default/grub: 35: Syntax error: EOF in backquote substitution


GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""

If it's wrong, could someone give me something to quickly copy and paste? I'm in a rush to catch up with my work by Friday. The other code worked before, but then suddenly today it's on high volume, as if I just started up my computer, but it won't die down. I don't really know if it is because I started up the Livestation program or what.. it's just frustrating.

---

### Post by xxhopingtearsxx on 2011-05-19
It just randomly started doing it again..

I am very..
very sick of this..

I want to use Ubuntu Linux.. but I am finding this very difficult to deal with this.

---

### Post by xxhopingtearsxx on 2011-05-19
BUMP.
I usually have to sign on Ubuntu after turning on my computer..
Use it for a while..
Fan goes high.
Restart.
But that's too time consuming.

---

### Post by tomsa on 2011-05-27
I'm having the same problem on my Toshiba Satellite L305D-s5882.  I tried the above listed kernel fix before.  I thought it worked for about 5 days, then the fan started acting up again.  The suspend trick isn't working for me so far, but that might be because I'm scanning some photos at the moment and this seems to be video card related.

I was thinking about doing a clean install to see if that fixes it, but I do a lot of work recording audio, and this loud fan thing is killing me.  I may try the new version of Mint and see if that fixes it.

---

### Post by linuxinstalledfromhdd on 2011-05-27
I have the same model..   It's always running, there is no idle. You may want to tweak your BIOS to try to change it's behaviour at this point.  There also might be a BIOS update available from Toshiba. I haven't checked since I bought it.

---

### Post by tomsa on 2011-05-27
> **linuxinstalledfromhdd said:**
> I have the same model..   It's always running, there is no idle. You may want to tweak your BIOS to try to change it's behaviour at this point.  There also might be a BIOS update available from Toshiba. I haven't checked since I bought it.
Did you have this problem with any of the versions before Natty?  This is the first time it has happened to me.  I also upgraded to Natty, rather than doing a clean install, which is what I usually do.  I wonder if reinstalling Natty will fix it?  

Another question is, is this a kernel problem, or an Ubuntu problem?  Will going to Mint or Lubuntu or some such derivative fix it?  I'm still on the fence about the unity interface- I'm thinking about trying some other stuff until they get the problems worked out of it, this fan thing may honestly be what pushes me elsewhere.

---

### Post by xxhopingtearsxx on 2011-05-27
> **linuxinstalledfromhdd said:**
> I have the same model..   It's always running, there is no idle. You may want to tweak your BIOS to try to change it's behaviour at this point.  There also might be a BIOS update available from Toshiba. I haven't checked since I bought it.

The thing that makes me not want to do it..

I never had to do anything with the BIOS for Hackintosh or Windows.. but suddenly I have to do it with Ubuntu? So I want to find other solutions before it comes down to that. It's like last time when I was told to open up my computer and clean it.. Windows and Mac had no problem, so I'm thinking it's something with Ubuntu.

To restate my problem a little to whoever, this problem occured in previous versions of Ubuntu on my laptop.. Since Jaunty Jackalope.

---

### Post by huangweiqiu on 2011-05-28
bump,and waiting perfect solution

---

### Post by linuxinstalledfromhdd on 2011-05-28
> **xxhopingtearsxx said:**
> The thing that makes me not want to do it..

I never had to do anything with the BIOS for Hackintosh or Windows.. but suddenly I have to do it with Ubuntu? So I want to find other solutions before it comes down to that. It's like last time when I was told to open up my computer and clean it.. Windows and Mac had no problem, so I'm thinking it's something with Ubuntu.

To restate my problem a little to whoever, this problem occured in previous versions of Ubuntu on my laptop.. Since Jaunty Jackalope.

Before you update your BIOS you would need to check to see if available update to your BIOS would impact your fan issue (if there is a bios update available naturally). You would need to find out from your computer manufacture if a BIOS flash update is needed. Start a trouble ticket and ask them if there was a BIOS update that had anything to do with your fan.  If not, then don't worry about BIOS.

---

### Post by xxhopingtearsxx on 2011-06-06
Well I decided not to do anything to the BIOS.
I never had to do it for Windows Vista, Windows 7, or Hackintosh..
So the fact that I have to do it on Ubuntu makes me think it's a horrible problem with Ubuntu Linux that will never be fixed.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **xxhopingtearsxx said:**
> Well I decided not to do anything to the BIOS.
I never had to do it for Windows Vista, Windows 7, or Hackintosh..
So the fact that I have to do it on Ubuntu makes me think it's a horrible problem with Ubuntu Linux that will never be fixed.

I'm not asking you to change anything. I'm asking to research it and see if your MB had a warning from the company. Most users update their BIOS. You are the exception to the rule, and could be the reason why simply installing Ubuntu doesn't resolve your MB issue.  If you think updating your bios is a bad thing, or cleaning out your computer is a bad thing, maybe you need to hire someone? Maybe you shouldn't be fooling around with it at all? I don't want to steer you the wrong way or anything, but it's not going to fix itself. Windows may have a native driver that was made to access your BIOS directly to adjust the fan, that is properiary, and did not port over to Linux yet? I don't know. If you see a BIOS issue with your laptop from the company, that could be one reason out of many others I can think of too. Like most commercial laptops, they really didn't have Ubuntu in mind when they designed the drivers for these systems. :)

---

### Post by sammiev on 2011-06-06
Have you installed or check your temp of your unit. You may have a software problem causing your system to heat up. GL :)

---

### Post by nrundy on 2011-06-06
> **xxhopingtearsxx said:**
> Everytime I try to use Ubuntu, I like it. Then I remember what always switches me back to Windows.. my fan. It's so loud. It wasn't high before, but I think an update I did recently messed it up. My fan is on too high, as if I'm running high-CPU programs, but I'm not. I'm jus
t on Google Chrome. I have a Toshiba Satellite L305-S5955 btw.

I've asked this question many times, so I'm going to answer questions people tend to ask so we can get right to solving my problem:

No, my laptop is not dirty.
Yes, I do shut down my computer often.
No, this laptop didn't do this on Windows or Hackintosh.
No, I'm sure nothing is using up my CPU and Memory at the moment.
Yes, it's done it on previous Ubuntu versions.
No, I am pretty sure I do not have to open up my laptop and clean it.



Please help. I'm currently back to using Windows 7 (unfortunately) since I don't want my fan on too high. I like my computer quiet. I'm tempted to reinstall Ubuntu 11.04 and never, ever, ever update.. Because this wasn't doing this before.

I have the same problem. 

I came to the conclusion that the best option for now is to just use Windows 7 until the Developers make Linux stop running so hot. There is a current kernel bug that may be heavily contributing to this. But personally I think in general a lot more needs to be done in Linux to make it run a lot cooler than it does.

This is a major issue for me. I've stopped recommending ubuntu to friends for now because of this issue. I'm afraid of them having a bad experience with laptop overheating etc. I'm hoping 11.10 and 12.04 will fix the heat issues and Uubntu will run as quietly and as cool as Windows 7.

---

### Post by linuxinstalledfromhdd on 2011-06-06
Did you do a flash update on your BIOS to the latest recommended update from the company? It could be that. They should support you for the llfe of the product.  There is nothing really difficult about upgrading your BIOS if there is an update available.  You can always start a trouble ticket with them and they can probably walk you through the whole process, if need be.

---

### Post by xxhopingtearsxx on 2011-06-12
I'm not going to update my BIOS. I'm just going to use Windows for now, and I'll try to find a solution  or update my BIOS at another time.

---

### Post by tomsa on 2011-10-05
I also just decided to try using KDE on my Linux Mint 11 install just for kicks.

I don't know why, but I have no fan problems now.

I'll try Unity again when 11.10 comes out, because there are some things I like about it- but I like a lot of things about KDE now too, after tinkering with it for a few days.  Maybe it will be Kubuntu for me after all.

---

### Post by trash on 2011-10-07
All of a sudden after the last update my toshiba satellite fan runs constantly. I'm using kde on lucid lts.. hopefully the next update will fix it.

---

