---
title: "No sound and no shutdown/restart options"
date: 2010-05-03
forum: General Help
---

### Post by cmat on 2010-05-03
This is a really weird issue. I'm using 10.04 and on occasion when I boot into Ubuntu the sound doesn't work along with losing the ability to shutdown via the menu. When I click shutdown it just logs out. I need to shut down my PC by using the terminal. 

It's strange because the sound and shutdown work as expected most of the time. The issue is seemingly random. Is there any way to solve this problem?

- cmat

---

### Post by TuNeCedeMalis on 2010-05-03
I'm having the same issues. Any help?

---

### Post by Kushal S. Pandya on 2010-05-03
Have you upgraded to Lucid or made clean install?

---

### Post by cmat on 2010-05-03
> **Kushal S. Pandya said:**
> Have you upgraded to Lucid or made clean install?

This is a clean install.

---

### Post by TuNeCedeMalis on 2010-05-03
> **cmat said:**
> This is a clean install.
Same for me

---

### Post by lockjaw$ on 2010-05-03
i have had the same problems till i shut down via:

*sudo shutdown -h now *

i also noticed that my desktop looked slightly different while this error lasted.(the menu of my "ubuntu netbook remix") was smaller than usually.

now, after restaring, everything seems ok again. sound on and shutdown possible.

---

### Post by Vual on 2010-05-03
[I][FONT=Arial Black][SIZE=2][COLOR=Black]I'm also having the same problem, with a 10.4 clean install.
Whats weird is that with my 10.*4 persistence install on my usb it doesn't happen*[/COLOR][/SIZE][/FONT][/I][SIZE=2][I][I][FONT=Arial Black][COLOR=Black].

I'm testing it on a older laptop, --specs--[/COLOR][/FONT][/I]

[/I][/SIZE][FONT=Arial Black][SIZE=2]Pentium M 725 1.60GHz Processor,  2MB L2-Cache[/SIZE][/FONT]
  [FONT=Arial Black][SIZE=2]ATI Mobility RADEON 9000 AGP 4X video graphics at  32MB[/SIZE][/FONT]
  [FONT=Arial Black][SIZE=2]14.1-in SXGA Monitor[/SIZE][/FONT]
  [FONT=Arial Black][SIZE=2]60GB Ultra ATA Hard  Drive, 4200RPM[/SIZE][/FONT]
  [FONT=Arial Black][SIZE=2]512MB, 266MHz RAM[/SIZE][/FONT]

---

### Post by andreibranescu on 2010-05-05
Same problems here with a clean install. 
I checked the sound preferences and it seems that the sound card is not loaded, so no sound device is available. What does this have to do with the shut down problem, I don't know.. but they both happen at the same time.

---

### Post by cmat on 2010-05-05
I would report this to launchpad but I don't have a clue what to report it as.

Any suggestions? I'm going to try some experiments to see if I can reliably duplicate the problem.

---

### Post by fromgi on 2010-05-05
Sound ok, but no shutdown here!

Because my ShutDown disappeared from the menu when installing from the LiveCD, today I did a clean install via the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD").  The Shutdown also disappeared with this fresh installation.  The only way to shutdown my PC is the Shutdown -h now.

---

### Post by cmat on 2010-05-05
Another possible symptom, I can't use "unlock" in configuration applets. Possible issue with policy-kit and device-kit.

---

### Post by TheCat on 2010-05-06
> **cmat said:**
> This is a really weird issue. I'm using 10.04 and on occasion when I boot into Ubuntu the sound doesn't work along with losing the ability to shutdown via the menu. When I click shutdown it just logs out. I need to shut down my PC by using the terminal. 

It's strange because the sound and shutdown work as expected most of the time. The issue is seemingly random. Is there any way to solve this problem?

- cmat

I experienced the same problem exactly after an upgrade.

---

### Post by IvoP123 on 2010-05-06
> **cmat said:**
> This is a really weird issue. I'm using 10.04 and on occasion when I boot into Ubuntu the sound doesn't work along with losing the ability to shutdown via the menu. When I click shutdown it just logs out. I need to shut down my PC by using the terminal. 

It's strange because the sound and shutdown work as expected most of the time. The issue is seemingly random. Is there any way to solve this problem?

- cmat

I also have this problem and it drives me crazy...

---

### Post by cmat on 2010-05-06
I filed the bug report, please sign into launchpad and click the icon beside "Does this bug affect you?" to indicate it does.

[https://bugs.launchpad.net/ubuntu/+bug/576235](https://bugs.launchpad.net/ubuntu/+bug/576235)

I have absolutely no idea what's causing it since I can't duplicate the issue reliably.

---

### Post by Fisaulerod on 2010-05-22
Same problem.

---

### Post by Sepero on 2010-05-24
[https://bugs.launchpad.net/ubuntu/+bug/576235](https://bugs.launchpad.net/ubuntu/+bug/576235)

Compaq Presario CQ60-215DX
Microprocessor	2.00 GHz AMD Athlon X2 QL-62 Dual-Core Processor
Microprocessor Cache	1MB L2 Cache
Memory	2048MB
Video Graphics	NVIDIA GeForce 8200M

I have the same problem.

Please post the specs of your computer. Also, I have GoogleChrome installed, which does not come from the Ubuntu repositories.

---

### Post by Fisaulerod on 2010-06-04
There isn't any solution yet¿

---

### Post by Sepero on 2010-06-10
I am independently attempting to figure out what is causing this problem. I created a script that outputs information about my system, like 'runlevel', 'uname -a', 'groups', 'lsmod', 'ps aux'.

I output the script to a file, then reboot the machine to proper status and output to another file. Then compare the two files.

So far I have determined that when this occurs, the runlevel is 'undefined', when it should be '2'. So it appears that there is a problem occurring very early in boot process.

I have just included 'dmesg' in the script, but have yet to have a chance for the problem to happen again.


I will keep you guys up to date on my progress. Any further ideas on what system info to collect is welcome.

---

### Post by Fisaulerod on 2010-06-15
> **Sepero said:**
> I am independently attempting to figure out what is causing this problem. I created a script that outputs information about my system, like 'runlevel', 'uname -a', 'groups', 'lsmod', 'ps aux'.

I output the script to a file, then reboot the machine to proper status and output to another file. Then compare the two files.

So far I have determined that when this occurs, the runlevel is 'undefined', when it should be '2'. So it appears that there is a problem occurring very early in boot process.

I have just included 'dmesg' in the script, but have yet to have a chance for the problem to happen again.


I will keep you guys up to date on my progress. Any further ideas on what system info to collect is welcome.

Thanks

---

### Post by Sepero on 2010-06-18
SOLUTION
SOLUTION
SOLUTION
SOLUTION
SOLUTION
SOLUTION
SOLUTION


Ok, this problem seems to be listed as a bug here:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)

The solution for this bug is listed on that page in post #81.

==========
First, comment out all instances of "console output in /etc/init/*.conf files. This can easily be done in the command line terminal with these instructions:
```

sudo su -
for file in /etc/init/*.conf; do sed -i 's/^console output/\#console output/' $file; done
exit

```


==========
Next, edit the file /etc/init/rc-sysinit.conf
1. sudo nano /etc/init/rc-sysinit.conf
2. Change this
"start on filesystem and net-device-up IFACE=lo"

To this
"start on filesystem and started rsyslog and net-device-up IFACE=lo"


==========
Last (this may not be mandatory, but worked for me), completely purge and reinstall ifupdown.
```

sudo apt-get install ifupdown --reinstall --purge

```




Let us know how it works out for you.


UPDATE:
Bug changed to this location:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/554172](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/554172)
It has been almost a month now since I made these changes to my computer, and I have not had the problem reoccur even once.

---

### Post by BiGViC340 on 2010-06-19
My symptoms were no sound, no shutdown/restart, no unlock, and I couldn't edit users and groups on random boots. After shutting down with terminal everything would work fine sometimes like I said very random. Being my second week on Linux/Ubuntu I had no idea what was going on I first noticed the audio. I later realized after reading a bit it has something to do with permissions like your account doesn't boot up right or something. 

I fixed the audio by sudo users-admin>Advance Settings>User Privileges>Check Use Audio Devices. 

Everything else got fixed when I did this 
sudo gedit /etc/default/grub
change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to : GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"
sudo update-grub

I had to remove the splash it worked perfect for me. Doesn't work for everyone as some are saying it didn't work for them :(. Let me know how it goes for you guys

Make sure to update Ubuntu also.

---

### Post by Sepero on 2010-06-20
BiGViC340,
Did you have this problem with Every boot, or only occasionally?

For myself, I had this problem only about 1 out of 5 boots.

---

### Post by BiGViC340 on 2010-06-20
I had this problem occasionally but more often than 1 out of 5 that's for sure closer to 50/50 really or worst on the favor of a bad boot. 

NEW UPDATE: Updating the grub didn't really worked booted up this mourning same thing restarted and it still doesn't work normally I guess have to reboot a couple of times to get it to work... :( Very discouraging as this is my first time trying Linux and this is my second week on Ubuntu...

---

### Post by Sepero on 2010-06-20
Ah, I see. Perhaps you could try the solution from post #20 at let us know if that helps you. Regards.

---

### Post by BiGViC340 on 2010-06-21
Thanks Sepero but I think I'm just going to head back to Windows XP. For me Windows XP just worked. I gave Ubuntu two weeks tried just didn't workout for me :(. Three BIG issues I have is the bug I'm encountering now. Which is a really big bug and I'm surprise to find it in the most popular Linux Distro especially in a LTS release :S. Flash support is bad. I know is not Ubuntu's fault but unfortunately Flash is everywhere can't wait till HTML 5. Last simple scrolling on Firefox on some pages is extremely slow off a fresh install. I suspect is because of my video drivers. I have an ATI Radeon 9800 Pro 128mb and there proprietary drivers do not support Ubuntu 10.04, so I use the default ones that came with Ubuntu its my only option. 

I use to me a PC gamer but now I got my 360 for that. I'm in the group of mainstream Internet/Social Networking users now. So is not me expecting too much as for the most "hardcore" thing on do on my PC nowadays is watch FMA in 720p of the H.264 codec. That's about it which I got working in Ubuntu. I figure Ubuntu would be great, stable(well it was stable not one crash is just didn't work right for me), and fast. For me it didn't work to well. Good luck to all others. 

Will come back when I get an Nvidia card and the bug is fixed :)

System Specs (just in case it helps with the bug)
Intel Celeron D CPU 3.2ghz
512mb ram
Ati Radeon 9800 Pro

---

### Post by BiGViC340 on 2010-06-22
Before I went back I wanted to try your solution Sepero but I'm a little confuse by the instruction what I'm a suppose to enter in step 2 in the terminal after making my self a super user?

---

### Post by Sepero on 2010-06-27
You enter the entire line in the terminal, be sure there are no typo's.
```

for file in /etc/init/*.conf; do sed -i 's/^console output/\#console output/' $file; done

```

---

### Post by Fisaulerod on 2010-06-27
I installed the Linux Mint based on Lucid Lynx and It doesn't have the problem.

---

### Post by cmat on 2010-07-10
The problem is in console-kit.

[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/544139](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/544139)

This problem really needs to be fixed soon. There really is no work around.

---

### Post by Sepero on 2010-07-10
I don't have the problem any more since I did what I posted here:
[http://ubuntuforums.org/showpost.php?p=9480172&postcount=20](http://ubuntuforums.org/showpost.php?p=9480172&postcount=20)

Thanks cmat, for the update on the Bug though. After looking in my old log files, I do see the errors that are posted in the bug report you linked to. I'll post a link on that Thread to here. Hopefully this fix will help them.

---

### Post by cmat on 2010-07-11
I applied the fix, I really hope it works since this bug is crippling my system.

---

