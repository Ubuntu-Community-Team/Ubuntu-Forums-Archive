---
title: "Startup time"
date: 2006-06-04
forum: General Help
---

### Post by Loffe_ on 2006-06-04
Hello Ubuntuers!

Why is Ubuntu taking so long time to start?
I have to 1 min 40 sec before I can use my machine.

I have Xgl/Compiz which may slow it down a little.

A fresh install is MUCH faster, around 25-30 sec!?

How long do you others have to wait?

My machine:
AMD Athlon62 X2 4200+
2GB RAM
ATI Radeon X800 XL

---

### Post by openmind on 2006-06-04
24 seconds from hitting "enter" in Grub to getting the GDM "Drumbeat".

That was dramatically improved after I installed and tweaked The Boot-Up-Manager, I was surprised by the cr*p that Dapper loads by default!

---

### Post by Loffe_ on 2006-06-04
What did you tweak?

Please show me a screenshot or something

I can't have a WinXp faster then my beloved Ubuntu :-k

---

### Post by openmind on 2006-06-04
I'm at work right now, on a Windows box.:mad:  But once you install BUM, it's reasonably obvious, it's ***very*** user-friendly, even to the point of giving descriptions on what each service does.

Right off the top of my head, I disabled Laptop support (On my home Desktop), and Bluetooth utilities, (I have none at present), a few more that I can't remember right now, but it was ***very*** noticable when I rebooted.

Of course I'm not using Xgl/Compiz either. Good luck, but like I say install BUM and it's all downhill from there.

---

### Post by orpheusblotto on 2006-06-04
startup probs here too. after signing in the screen goes all brown and the toolbar doesn't appear or allow anyprograms to run for 2 minutes or so. any ideas?

---

### Post by squeky on 2006-06-04
And you're restarting why?  J/k, startup times don't bother me because it happens once every couple days.  Fast enough for me.

---

### Post by henriquemaia on 2006-06-04
< 30 sec, coming from hibernation. I love hibernation.

---

### Post by Loffe_ on 2006-06-05
OK, BUM is kind of nice.

I uncecked some boxes (eg. ppp), and when I hit apply they were checked again ?!

Is ppp enabled or not when it is checked? If it is, how do I stop it?

---

### Post by Sutekh on 2006-06-05
Dapper and Openbox, no GNOME/GDM = 18 seconds, 17 if I type my user/pass fast enough

Dapper and Xubuntu = 26 seconds.

These times are so much faster than my boot times for the respective environments in Breezy.

---

### Post by Loffe_ on 2006-06-06
*bump*

---

### Post by t0mc4t on 2006-06-06
[QUOTE=openmind]
Right off the top of my head, I disabled Laptop support (On my home Desktop), and Bluetooth utilities, (I have none at present), a few more that I can't remember right now, but it was ***very*** noticable when I rebooted.
[/QUOTE]

How is the way to disable the bluetooth utilities on startup, and maybe the others utilities?

Thanks..

---

### Post by missmoondog on 2006-06-06
all 4 of my dapper machines start in a minute or less. much faster than breezy was. still have breezy on 1 machine. thinking about installing xubuntu 6.06 on that. it's only a 667mhz celeron.

---

### Post by onesojourner on 2006-06-06
I put dapper on a 266 P2 and its much faster than breezy was.

---

### Post by Melvil on 2006-06-06
[QUOTE=henriquemaia]< 30 sec, coming from hibernation. I love hibernation.[/QUOTE]

Resuming from hibernation is twice as fast on my XP installation. I hope the Ubuntu devs will improve this.

---

### Post by Christmas on 2006-06-06
I never had an issue with the start-up time because I keep my computer started all the time, so restarts are very rare. I didn't measure the exact time for my PC to start-up but I think it's around 40, maybe 50 seconds.

---

### Post by blakegrover on 2006-06-06
After getting rid of lvm, evms, mdadm-raid, mdadm I can get my latop to boot in 29-35 seconds usually.  I have a Inspiron 9300.  I am very happy with my boot time, it is almost the same speed as to hibernate.

---

### Post by cleentrax on 2006-06-06
I haven't booted my Inspiron 8600 in a week. So I'm not sure. But it seems pretty quick, thought it's a distant memory. :)

---

### Post by Rui Pais on 2006-06-06
Hi,
mine normal boot process is less then 30 sec. P4 1G of ram

I now use suspend2, so in fact my boot time with a good splash screen (all colours, instead of brown and brown usplash)  is 10 sec to get from disk and 3-4 sec from ram. ;) I don't remember last time i really reboot (powerdown).

I prefer sysv-rc-conf to bum. 

@ loffe_
[here is a good howto with most of the options very welll explained.]("http://ubuntuforums.org/showthread.php?t=89491")

---

### Post by Pawel Stolowski on 2006-06-06
You can gain 1-2 seconds by tweaking this file (makes sense only if you have linux-restricted-modules installed):
/etc/default/linux-restricted-modules-common

It allows you to specify which restricted modules to *skip* when booting, this may save some time on modprobing for non-existing hardware. For example, since I have
modern nvidia card, I use this:

DISABLED_MODULES="fglrx nvidia_legacy fc"

---

### Post by xtacocorex on 2006-06-06
@blakegrover:
How did you get lvm and evms to not start up on your laptop? I've been trying to figure that out since breezy.
  - Worked perfectly!

@Loffe_:
If you uncheck them and then hit apply, the program either stops or starts the services. You need to uncheck them and then exit BUM and that will save the config.

EDIT: bootup time is now down to 37 seconds!

---

### Post by .t. on 2006-06-06
I've got a Dell I6k, and I routinely have it boot to the GDM prompt in around 15 seconds, plus around ten after logging in to get a fully working, responsive desktop. I do have a gig of memory, so that may make a difference.

---

### Post by blakegrover on 2006-06-06
In order to remove certain services I ran

```

update-rc.d -f lvm remove

```

It still keeps the script in the /etc/init.d directory so you can manually start them but it removes it from the boot and shutdown screens.  You can replace lvm with other service names.

Blake

---

### Post by .t. on 2006-06-06
[QUOTE=Loffe_]OK, BUM is kind of nice.

I uncecked some boxes (eg. ppp), and when I hit apply they were checked again ?!

Is ppp enabled or not when it is checked? If it is, how do I stop it?[/QUOTE]
I also have this problem. File a bug. If you won't I will; I'll assume you are unless you say otherwise. The solution is to quit, and reload BUM - that way it'll see the changes.

---

### Post by Loffe_ on 2006-06-07
[QUOTE=.t.]I also have this problem. File a bug. If you won't I will; I'll assume you are unless you say otherwise. The solution is to quit, and reload BUM - that way it'll see the changes.[/QUOTE]

Where do I submit a bug. I've never done it before . . . I could be good to know . . .

My guess is at [https://launchpad.net/products/bum](https://launchpad.net/products/bum)
But there's not the right version (2.1.5)

---

### Post by the_maassk on 2006-06-07
28 seconds from hitting Enter in GRUB to GDM login prompt. Another 6 seconds to get a usable desktop after logging in. Am running Dapper 6.06 LTS on Compaq Presario laptop (1.6 Ghz, 1 GB RAM) with Compiz/ AIGLX.

---

### Post by xtacocorex on 2006-06-07
@the_maassk:
What all did you remove from init to speed it up? So far I've gotten rid of:
lvm, evms, mdadm, mdadm-raid, ppp 
Removing those dropped it from 58 seconds to 37 seconds on my machine (from init to GDM).
Dell Smartstep 250N: P4 2.4 GHz & 1 Gb Ram

---

### Post by the_maassk on 2006-06-07
Am not on my laptop right now...will be in a few hours and then will post what all I have disabled. 

I followed a sysv-rc-conf post on these forums somwhere. Try searching if you can find it...otherwise gimme a few hours to post my list.

---

### Post by blakegrover on 2006-06-07
Does anyone know if the initng is faster than the normal init ? If so how much time does it take off?   I am thinking of following a tutorial to install it but I want to make sure it is worth it.

---

### Post by xtacocorex on 2006-06-07
[QUOTE=the_maassk]I followed a sysv-rc-conf post[/QUOTE]

Ah, that post. I have that subscribed, and I forgot about it. Thanks for the reminder.

---

### Post by the_maassk on 2006-06-07
:) Try that and let me know how much could you shave off the boot time. You might do better and then I'd need your advice :wink:

---

### Post by the_maassk on 2006-06-07
[QUOTE=blakegrover]Does anyone know if the initng is faster than the normal init ? If so how much time does it take off?   I am thinking of following a tutorial to install it but I want to make sure it is worth it.[/QUOTE]

As far as I have read on the subject - it might not take off much. IMHO, the trouble involved in configuring it might not justify the benefit. But that is just my opinion! (am chicken to mess up my init right now!)

---

### Post by jeff-- on 2006-06-07
Mine only takes maybe a little under a minute to start.

---

### Post by the_maassk on 2006-06-08
[QUOTE=xtacocorex]@the_maassk:
What all did you remove from init to speed it up? So far I've gotten rid of:
lvm, evms, mdadm, mdadm-raid, ppp 
Removing those dropped it from 58 seconds to 37 seconds on my machine (from init to GDM).
Dell Smartstep 250N: P4 2.4 GHz & 1 Gb Ram[/QUOTE]

Here is the disabled stuff I promised:

alsa-utils
anacron
apmd
atd
bittorrent
bootlogd
cupsys
dns-clean
evms
hplip
ntp-server
ppp
pppd-dns
readahead
rmnologin
rsync
samba
sudo

But this is specific to my configuration of course!

---

### Post by exclipy on 2006-06-08
How are you people measuring the time?  I measure from pressing Enter at Grub, until the hard drive stops grinding on a usable KDE desktop (I have autologin).  It takes 37 seconds to get up to the point of KDE starting, but KDE takes about 25 seconds, putting me in the <2min category.

I think I'll be able to speed up the KDE startup by upgrading to 3.5.3, but I don't think there's anything I can do to speed up the rest of the boot process, other than switching to InitNG - which I think is a bit too untested/unsupported for me at the moment.

---

### Post by xtacocorex on 2006-06-08
@the_masssk:
Thanks for the list. I have most of those removed. I kept readahead and cpusys, sudo wasn't in /etc/init.d on my machine and I need to check up on bittorrent.

@exclipy:
There is a program in the repos called bootchart that keeps track of how much time it takes to get to GDM/KDM. I am confused because it looks like it might actually get into login, but I need to research that more.

---

