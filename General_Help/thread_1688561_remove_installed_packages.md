---
title: "remove installed packages"
date: 2011-02-15
forum: General Help
---

### Post by PerfectReign on 2011-02-15
I am installing a minimal ubuntu 10.1 under a virtual machine. I want to remove unneccessary packages such as open office, thunderbird...

How do I go into Synaptic and find what's installed?

I searched and came up with this.

[https://help.ubuntu.com/community/SynapticHowto#Remove%20or%20Uninstall%20Packages](https://help.ubuntu.com/community/SynapticHowto#Remove%20or%20Uninstall%20Packages)

---

### Post by PerfectReign on 2011-02-15
Ahh, nevermind!

I took a leap of faith and went to the Ubuntu Software Center. There's a selection to list all "installed" packages.

---

### Post by TeoBigusGeekus on 2011-02-15
A more thorough way to do this is
```
dpkg -l>~/Desktop/installed_packages.txt
```
to see every single package installed on your system.

---

### Post by PerfectReign on 2011-02-15
/shakes head in frustration...


Yes, that can be done.

HOWEVER - It involves two things 99% of us don't want to do.

1. Using the stupid command line and having to remember arcane commands.

2. Taking the information and then having to somehow use other commands (my guess would apt-get?) to actually DO something.


I like Ubuntu and Linux but cannot get over this '80s command-line mentality.

---

### Post by TeoBigusGeekus on 2011-02-15
Ha, ha... that's what I thought some years ago when I first started with linux.
Once you realize that the command line is EASIER than the gui and, what is more, much more powerful, you'll never go back.

dpkg with the -l option lists the packages installed on your system.
> redirection...
~/Desktop/installed_packages.txt ...to a file named installed_packages.txt located on your desktop, so you can scrutinize it with your favourite text editor and then of course... use apt-get to remove any non wanted package. 

Ignore me if you want, but if you decide to stick with linux, you will remember me sooner or later. ;)

---

### Post by kn0w-b1nary on 2011-02-15
CLI is what make linux amazing, GUI can be helpful on the frontend, making it easy, but CLI lets you know exactly what you're doing.

To help your original problem, you can check out ubuntu tweak to remove unneeded packages not removed with ```
sudo apt-get autoremove
```

---

### Post by PerfectReign on 2011-02-15
I've been using Linux off-and-on since '98 and full-time from '05 until last month. I even spoke at last year's SCALE ([http://www.socallinuxexpo.org](http://www.socallinuxexpo.org)) event about integrating Linux and Windows in the corporate office.

I have now pretty much given up on *nix as a desktop replacement.  Major issues with Ubuntu 10.04 and 10.1 have forbid me from upgrading ([http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)) yet I need to continue doing Android development. 

I went ahead and moved my laptop and main desktops to Windows 7 from Ubuntu 9.1, which I'd  been using.

The command line is so - erm - '80s.  I used it just fine back then but even in '87 I got hold of this cool new computer running a GUI - no command line needed.  In fact I have one of those computers...

[IMG]http://www.perfectreign.com/stuff/2009/darth_mac.jpg[/IMG]


In any case, I plan to use Ubuntu for such things as testing, my home proxy and as a file server.

---

### Post by williamts99 on 2011-02-15
> **TeoBigusGeekus said:**
> Ha, ha... that's what I thought some years ago when I first started with linux.
Once you realize that the command line is EASIER than the gui and, what is more, much more powerful, you'll never go back.

I was the same way until I started supporting people on different versions and editions of Ubuntu.  Where there are 4 different ways to accomplish it through the GUI, or just use the CLI and the same way works on all of them. :)

---

### Post by TeoBigusGeekus on 2011-02-15
> **PerfectReign said:**
> I've been using Linux off-and-on since '98 and full-time from '05 until last month. I even spoke at last year's SCALE ([http://www.socallinuxexpo.org](http://www.socallinuxexpo.org)) event about integrating Linux and Windows in the corporate office.

I have now pretty much given up on *nix as a desktop replacement.  Major issues with Ubuntu 10.04 and 10.1 have forbid me from upgrading ([http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)) yet I need to continue doing Android development. 

I went ahead and moved my laptop and main desktops to Windows 7 from Ubuntu 9.1, which I'd  been using.

The command line is so - erm - '80s.  I used it just fine back then but even in '87 I got hold of this cool new computer running a GUI - no command line needed.  In fact I have one of those computers...

In any case, I plan to use Ubuntu for such things as testing, my home proxy and as a file server.
Sorry mate, I thought you were a new user will a (completely natural) aversion to cli.
I do insist however that cli>gui; don't wanna start a flame war though.
Whatever suits one, is the best in their opinion I guess.

---

### Post by PerfectReign on 2011-02-15
LOL!

No, I'm an OLD user with an aversion to the CLI.  

The CLI was fine on my TRS-80, my Apple II and the VAX I used in the '80s. 

Once I got on Macintosh then Windows 3.1, however, I never looked back.

When I switched my laptop to Mandrake in '98 I would reluctantly use the CLI but gave up until I was forced to go with XP. I made the switch then and suffered through SUSE/openSUSE then Ubuntu for several years.

---

### Post by williamts99 on 2011-02-15
> **PerfectReign said:**
> How do I go into Synaptic and find what's installed?

On the left hand side, midway down, click on 'Status' then 'Installed'

---

### Post by btindie on 2011-02-15
From an Admins point of view using Linux is so much easier as you can automate EVERYTHING with scripts instead of having to ponce about with a GUI. This is especially useful over a slow link.

You can get much more control over how things work by using the command line unlike in windowz which usually means delving into the registry and doing a reboot.

It's much easier giving someone a command to enter than to tell them to click here, here, then here and here, blah blah...

You've got to understand that Linux is NOT windowz and that the it works is not necessarily the best. How long has it taken MS to come out with the 'PowerShell' ?? Would you say they're taking a step forward or backward? The command line environment under windowz is extremely poor to say the least.

I may have taken the same view back in '96 when I first tried Linux, it is a step learning curve and a different concept if that's your background but once you get used to it it does make sense and becomes more powerful.

What's quickest, manually selecting each package individually or typing
```
dpkg -l | cut -b5- | egrep '^(openoffice|evolution|thunder)' | cut -f1 -d\ | xargs apt-get -y remove 
```

---

### Post by PerfectReign on 2011-02-16
I've yet to figure what the power shell has over the normal command prompt. Haven't really used either in a long time.

For a SERVER I can see the point. Say I were running Red Hat or Cent or SLES.   However, for a DESKTOP there's just no need.  I don't remote into desktop machines - other than over VPN - and then I'm usually doing desktop work.

[IMG]http://www.perfectreign.com/stuff/2009/20090920_vnc_lilly.jpg[/IMG]

---

