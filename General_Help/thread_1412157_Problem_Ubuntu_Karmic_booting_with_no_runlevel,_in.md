---
title: "Problem: Ubuntu Karmic booting with no runlevel, including GDM and GNOME"
date: 2010-02-20
forum: General Help
---

### Post by chriv on 2010-02-20
I've been fiddling with the following problems on one PC ever since the day Karmic Koala came out.

BUT I DID FIND the solution, and I am sharing!

1) Ubuntu (since upgrading to Karmic) always boots into gdm (even though I had carefully manipulated my /etc/rc[2-5].d links and default runlevel to prevent gdm from running at startup)
2) Ubuntu was not running many of my initialization scripts, so many services were not running after booting and logging in, and had to be manually started.  **Here are some of the services that would not automatically start**.
    * CUPS
    * SSH
    * SAMBA - (Considering how few Windows machines I have, this one isn't much of an issue...)
    * bind9

**You can imagine my frustration when a PC I am using as a print server and DNS server would not start those services automatically**.  **Especially since SSH wouldn't start automatically** and I could not remote into the PC to start the other services.

**I found part of the cause at first** (but not the root cause):

**Ubuntu had no runlevel**!  None of my initialization scripts in /etc/rc[S2-5].d were running, because a runlevel was never set.

I could not understand what was starting gdm, especially with no init scripts.  But, **wait a minute**, Karmic Koala is using a much heavier reliance on UpStart jobs, and much less on SYS V Init scripts!  What's that folder for UpStart jobs again?  :confused:It changed?  /etc/init !  Ohhhh!

Normally, I would go to the logs, and figure out what was going wrong.  But guess what!  **Upstart jobs don't log anything, and are event triggered**.  Examining almost every script would be necessary, since there is no numbered sequential order to the way the scripts run.

:KSI'll save you the hours of troubleshooting, and give you the next part of the answer:

**/etc/init/gdm.conf** - Starts gdm (and your Xserver in the process)

and

**/etc/init/rc-sysinit.conf** - Sets your initial runlevel

???

So this means that the **gdm** job/service **is running before** the **rc-sysinit** job/service that sets your initial runlevel?  **gdm will run without the system having a runlevel**?  Yes, and Yes.

So now, **WHY** and **HOW**?

:KS**How to find the answer**:

**Look at the defined events that trigger** the **gdm** and **rc-sysinit** jobs/services.

The events that are required to trigger **rc-sysinit** are:
  * **filesystem** must be up
  * virtual network interface **lo** (loopback device) **must be up**
We know this because the start line in /etc/init/rc-sysinit.conf is:
```
  start on filesystem and net-device-up IFACE=lo
```

The events that are required to trigger **gdm** are:
  * **filesystem** must be up
  * the **hal** (hardware abstraction layer) service must be **started**
  * **tty7** must be **up** (tty7 is used for Xorg/X86 Display 0)
  * **either** a **graphics-device** must be **up**, or **udevtrigger** must have **stopped**
We know this because the start lines in /etc/init/gdm.conf are:
```
  start on (filesystem
            and started hal
            and tty-device-added KERNEL=tty7
            and (graphics-device-added or stopped udevtrigger))
```

Wow, it takes a LOT more for gdm to start than rc-sysinit!  **So how is it gdm is starting first**?  An initialization script?  WRONG!  :confused:Remember, the initialization scripts aren't running, because no runlevel is being set!

OK, take a breath.  **BOTH rc-sysinit and gdm require the filesystem to be up**.  So we know that requirement has been met when gdm starts.

:KS**The ONLY requirement that rc-sysinit has that gdm does not (in order to trigger execution) is that the virtual network device *lo* be up and running**.

So this means that hal, tty7, and my graphics card are loading all before the loopback device?  Wow, really?  My other network cards are loading in the initramfs?  The loopback device isn't?  Yep!  Amazing!

**The root cause of the entire problem**:  I had backed up /etc/network/interfaces to /etc/network/interfaces.bak a long, long time ago (before upgrading to Karmic), and left a completely blank /etc/network/interfaces file in it's place.  I had done this, because NetworkManager (or now, network-manager), had been extended to dynamically configure system network devices, even if X isn't running.  So why have a static configuration or ifup and ifdown?  I had moved this responsibility from /etc/init.d/networking to /etc/init.d/network-manager.

It's a good practice, but ONLY for your REAL network cards.  lo is a virtual device.  You'll notice that /etc/init has both a networking.conf and a network-manager.conf .  There are UpStart jobs for both the networking service and the NetworkManager/network-manager service.  Why?
network-manager doesn't handle the lo device, unless it wasn't already present when gdm started.  It was supposed to already be started by networking!

**Don't blank out or delete your /etc/network/interfaces file, even if you are using network-manager to configure all your NICs.**

:KS**Minimum /etc/network/interfaces file below**:
```
auto lo
iface lo inet loopback
```

I made the /etc/network/interfaces file above, rebooted, logged into gdm, and opened **gnome-terminal**.  I typed **runlevel**.  For the first time in months, I saw **N 2** instead of **unknown**.

Wow, what a weird side-effect of migration to network-manager!

:popcorn:**To the Ubuntu Developers**:

I humbly request that the requirements to MANY upstart jobs be adjusted so that they will not be triggered if **runlevel** is **unknown**.  Especially gdm!!!

**I don't know why the loopback device is required to be up to set a runlevel**, (**I'm assuming** this is an artificial method to adjust boot timing so that the runlevel is not set while initrd is still running, but there has got to be a better trigger than this!)  Setting runlevel is more important than having the loopback device up (IMHO)!  **I'm also guessing** that some of the init scripts bomb if there is NO network device (at least a loopback device), and that may be another reason why lo must be up before setting a runlevel.

**I also thought the idea was to eliminate /etc/network/interfaces for Ubuntu Desktop users** (relying on the GUI for dynamic configuration), and only Ubuntu Server users were going to be recommended to use /etc/network/interfaces for static configuration of their NICs.  **Should this not include the loopback device?  I was surpised to see that there even was an UpStart job for networking on Ubuntu Desktop in Karmic Koala**.  I guess I know why now! :)

**I guess what I'm saying is that by the same theory that users should be able to launch X without an xorg.conf file** (which is usually not the case, since most of us are using proprietary video drivers for special Intel or nVidia cards), **SYS V Init scripts ought to run without a /etc/network/interfaces file**!  Truer plug-n-play for those who only know how to use a GUI!  Yes, I realize that another goal is to elimiate the SYS V Init scripts (replacing them entirely with UpStart event-triggered jobs and services), and this is an intermediate step.

---

### Post by root75 on 2010-03-03
Thanks for your post
This help me too

---

### Post by emil_manolov on 2010-03-06
Thank you! This worked for me, too! I gave up trying to fix this a long time ago and I just got used to type "sudo telinit 3" after every restart :) My ssh deamon started, although booting with no runlevel.

---

### Post by dnoyeb on 2010-03-17
Great post!

I agree with you on the runlevel being started before scripts that use it are started.  Or maybe there is something I don't understand.

Anyway, its a nice introduction to upstart I suppose.

---

### Post by paddy100 on 2010-03-19
Thanks saved me alot of time

---

### Post by gvoima on 2010-03-23
I'm speechless...
I've had some serious problems a long time with Karmic after a update.
[LIST]Bluetooth wouldn't come up after a reboot, had to manually modprobe btusb.[/LIST]
[LIST]Ondemand governor wouldn't start, had to manually start it from init.d.[/LIST]
[LIST]Vboxdrv wouldn't start up, had to manually start it from init.d.[/LIST]
[LIST]And my nick connected 100Mb instead of 1000Mb.[/LIST]

And a lot of other problems too. And then I stumble upon this thread and try it out of frustration, and surprise surprise after a reboot everything works. My runlevel is back to *N2* instead of *unknown*.
All of my init.d scripts gets correctly started at boot because they now recognize the correct runlevel, my nic is 1Gb again, bluetooth works, ondemand works, everything works.

The question now is, how is this possible? I've been through so many logs and tried to hunt down this, but to no avail. There was nothing that could have lead me to check the interfaces file and reset it to basics.

I'm happy that this works now, but this is just ridiculous..

btw. thanks for sharing this

---

### Post by illusion88 on 2010-05-01
Just something to add to this being as the thread is fairly recent. I spent hours wondering why half my services and init scripts weren't coming up after a clean install of Ubuntu 10.04. I come across this thread and things finally start to make sense.

The difference being my /etc/network/interfaces file already has the loop back adapter defined (and I'm on Lucid 10.04), yet I'm still seeing 'unknown' when I check the run level.

I found a solution by searching Google which suggested changing /etc/init/rc-sysinit.conf:

"start on filesystem and net-device-up **IFACE=lo**" -> **IFACE=eth0**

This doesn't strike me as a clean way of fixing this problem and by no means does it make sense if the OP is anything to go by (eth0 **isn't **defined in /etc/network/interfaces, lo **is**) yet changing this option fixed it.

Maybe this will help someone else who doesn't get round the issue by adding the loop back adapter to the interfaces file. 

Good luck.

---

### Post by recken on 2010-05-06
Thanks chriv, Your post saved me hours of frustration

I eventually managed to get my server to boot up in **runlevel 2** by creating a old style** /etc/inittab **file and entering the line **id:2:initdefault**

---

### Post by monquixote on 2010-05-13
I had the same problem as illusion88

Noticed Apache wasn't starting when I rebooted and then noticed I had no run level.

Made the fix suggested by illusion88 and it works fine now.

No idea why it happens as my machine believes it has a loop back device.

---

### Post by MBianchi on 2010-06-08
Please do the following experiment.

        Boot
        Open an Xterm or equivalent.
        Issue the command
                runlevel

If you get back "unknown" you have an unreliable boot.
        See   [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)

In particular, some/many things in  /etc/init.d/rc2.d  and  /etc/init/*.conf
are unlikely to have run.

As you will see from the bug report, "unreliable" means it
        seldom / sometimes / often / almost-always   fails
In my experience, different random hacks have different random results.

The one almost reliable fix is to comment out the line
                console output
in
        /etc/init/mountall.conf
        /etc/init/rc.conf
        /etc/init/rc-sysinit.conf
        /etc/init/ufw.conf

((
        NOTE there are directories  /etc/init  _AND_  /etc/init.d ,  both
        associated with getting the system booted, but _totally_ different in
        structure, architecture, functionality .........
          Both need to work for a reliable boot.
))


See also my comments #54 and #73 in the bug report.
And see my Bug report  [https://bugs.launchpad.net/null/+bug/581291](https://bugs.launchpad.net/null/+bug/581291) .

---

### Post by maddox on 2010-06-09
> **illusion88 said:**
> Just something to add to this being as the thread is fairly recent. I spent hours wondering why half my services and init scripts weren't coming up after a clean install of Ubuntu 10.04. I come across this thread and things finally start to make sense.

The difference being my /etc/network/interfaces file already has the loop back adapter defined (and I'm on Lucid 10.04), yet I'm still seeing 'unknown' when I check the run level.

I found a solution by searching Google which suggested changing /etc/init/rc-sysinit.conf:

"start on filesystem and net-device-up **IFACE=lo**" -> **IFACE=eth0**

This doesn't strike me as a clean way of fixing this problem and by no means does it make sense if the OP is anything to go by (eth0 **isn't **defined in /etc/network/interfaces, lo **is**) yet changing this option fixed it.

Maybe this will help someone else who doesn't get round the issue by adding the loop back adapter to the interfaces file. 

Good luck.


THAAAAAAAANKS A LOT!!!!

For the first time in a couple of months i got the **runlevel** set at startup (and all the startup scripts at /etc/init.d/)without typing "** sudo telinit 2**"

I had this problem since one of the last Karmic updates and now on a fresh install of Lucid!


by the way, my **/etc/network/interfaces** file is configured to static ip as this:

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.254


Again, thanks for your post

---

### Post by hellslinger on 2010-10-14
> **illusion88 said:**
> Just something to add to this being as the thread is fairly recent. I spent hours wondering why half my services and init scripts weren't coming up after a clean install of Ubuntu 10.04. I come across this thread and things finally start to make sense.

The difference being my /etc/network/interfaces file already has the loop back adapter defined (and I'm on Lucid 10.04), yet I'm still seeing 'unknown' when I check the run level.

I found a solution by searching Google which suggested changing /etc/init/rc-sysinit.conf:

"start on filesystem and net-device-up **IFACE=lo**" -> **IFACE=eth0**

This doesn't strike me as a clean way of fixing this problem and by no means does it make sense if the OP is anything to go by (eth0 **isn't **defined in /etc/network/interfaces, lo **is**) yet changing this option fixed it.

Maybe this will help someone else who doesn't get round the issue by adding the loop back adapter to the interfaces file. 

Good luck.

This worked for me too. Thank you immensely. Why does this fix things? How did anyone ever discover that this was the solution? I'm actually interested in knowing...

Thanks again.

---

