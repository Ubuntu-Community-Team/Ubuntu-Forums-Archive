---
title: "UDEVD eating 50% of my cpu!"
date: 2009-12-15
forum: General Help
---

### Post by FreezWay on 2009-12-15
UDEVD is eating my cpu cycles. i have quad core and it eats 50% of that! how do i tame the daemon (pun intended)

---

### Post by jerome schatten on 2009-12-16
Does this happen immediately after booting the gui or do you have to run some stuff to make it happen? 

sudo killall udevd

does that bring down the cpu usage to a few percent?

jerome

---

### Post by ceadbanka on 2009-12-16
I am new to this forum and to Ubuntu, this is my first post.
After installation of 9.10 no problem.
Applied all updates and after that same problem, cpu ~ 50% and it stays that way.
killall udevd brings cpu back to normal level again.

---

### Post by jerome schatten on 2009-12-16
Well, sounds like two choices: 1.find the offending update(s) and get rid of them (not easy) or 2. find an acceptable work-around (not easy).

#2. first: in my case I did find a more or less work around. I found there are several things that sets off udevd to go haywire. The main one was the 'ant with searchlight' screensaver. I now use a blank screen screensaver. That leaves the other thing I found and that is highly compute intensive tasks like doing gigabyte file transfers across my lan. 

I installed the temp. sensing applet that allows me to monitor cpu temperature. The high cpu usage causes in most instances a high cpu temperature. The real problem with udevd is that it doesn't want to return to normal usage by itself. Thus, after the file transfers I use **sudo killall udevd**. There's a 10-12C temperature rise on my dual core system when things go wrong, so it's a real problems we're looking at.

Some experimenting will most likely show what's setting off your high cpu usage.

#1. The name of all packaages  you've installed with either the package manager (updates or intentional addidtions' appears in **/var/cache/apt/archives**
If you do** ls -la** in that directory, you will also see the date of the install for a particular package. That may give you all the info you need to remove things one by one and see if the problem goes away.

Look at **man apt-get **for information on how to do this.

If you google on **ubuntu high cpu usage **you'll find more than one thread on this issue and some other interesting fixes.

Hope this helps a bit & good luck!
jerome

> **ceadbanka said:**
> I am new to this forum and to Ubuntu, this is my first post.
After installation of 9.10 no problem.
Applied all updates and after that same problem, cpu ~ 50% and it stays that way.
killall udevd brings cpu back to normal level again.

---

### Post by jerome schatten on 2009-12-16
Sorry... in my last reply, I was wrong... the date shown for the packages are not the date of the install on your system, but seem to be the package release date. Probably syslog would show the date of the install.
jerome

---

### Post by FreezWay on 2009-12-19
it might be my kernel, i custom built one. is there a way i can check to see if that is causing it?

---

### Post by falconindy on 2009-12-19
I've heard of this happening before. This is going to sound strange, but disable/unplug your CD-ROM drive and boot without it. While that isn't a feasible solution, it may lead to a real one.

---

### Post by FreezWay on 2009-12-19
i'm gunna try that tomorrow. It starts eating my cpu at random times, sometimes within a few min, sometimes within a few hrs. i dont think its my kernel b/c i booted 2.6.31.w/e and it still eats it up.

---

### Post by peepingtom on 2009-12-19
Do you have the backports modules package installed?

---

### Post by FreezWay on 2009-12-19
what's that?
also update: not my kernel, boot old one and it still ate my cpu

---

### Post by FreezWay on 2009-12-23
anyone? its not my kernel, and i dont know what backport modules are.

---

### Post by popinet on 2010-02-04
I have a similar problem here. A fresh install of Ubuntu 9.10 on a quad core system, kernel is:

Linux popinet 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

Here is what shows up with top:

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  494 root      16  -4 26968  10m  296 S   70  0.3 468:20.09 udevd              
  626 root      18  -2 17316 1168  296 S   22  0.0 110:14.83 udevd              
    1 root      20   0 19452 1812 1196 R    8  0.0  40:16.68 init               
  492 root      20   0 12772  840  560 S    6  0.0  41:36.12 upstart-udev-br    
 1902 root      20   0  186m  33m  10m R    4  0.9   1:07.89 Xorg               
 5867 popinet   20   0  201m 4988 3448 S    3  0.1   0:39.69 pulseaudio      

it looks like 

upstart-udev-bridge --daemon

is part of the problem....

Obviously, this is a serious problem....

Any help much appreciated

Stephane

---

### Post by popinet on 2010-02-04
/var/log/messages shows this:

Feb  5 09:23:21 popinet kernel: [31073.337392] i2c-adapter i2c-1: unable to read
 EDID block.
Feb  5 09:23:21 popinet kernel: [31073.337396] i915 0000:00:02.0: HDMI Type A-1:
 no EDID data

could that explain the problem?

cheers

Stephane

---

### Post by popinet on 2010-02-04
Googling on the above, the following page turned up:

[https://bugzilla.redhat.com/show_bug.cgi?id=541184](https://bugzilla.redhat.com/show_bug.cgi?id=541184)

Looks like the same bug...

Doing:

% udevadm monitor

I get a flood of messages:

...
KERNEL[1265317007.270484] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
UDEV  [1265317007.271296] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
UDEV  [1265317007.273653] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
UDEV  [1265317007.276143] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
...

OK, I found out that the bug is in launchpad, see:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440411](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440411)

There is a solution but it involves patching the kernel...

Hopefully there will be a fix and update soon.

hope this helps

Stephane

---

### Post by popinet on 2010-02-04
A quick workaround is to disable udev entirely. Just do:

% sudo service udev stop

(note that you will need to reissue this command after a reboot).

---

