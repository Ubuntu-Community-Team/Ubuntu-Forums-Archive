---
title: "Ubuntu Checking Battery State and Freezes"
date: 2010-06-08
forum: General Help
---

### Post by rikdegraaff on 2010-06-08
Hi All,

I've searched the forums and i found some threads about this issue, but nothing seems to help.

I just bought a secondhand Dell Optiplex GX60 Series.
I've installed a fresh install of Ubuntu 10.04.

Now comes the problem.
If the pc is on, and I use it for about 15-40 minutes, the it freezes up with the following screen:

"* Checking battery state     [OK]"

Then there are flashing bars through the screen, and the message: "Checking Battery State       [OK]" comes back.

This keeps flashing through the screen until I shut the PC down with the power button.

The specifications of my PC:

Processor : Pentium 4 -- 2.4 GHz.
RAM       : 512 MB
Video Card: Intel Corporation 82845 G/GL [Brookdale G]/GE Chipset Integrated Graphics Device (rev 01)

This is a Desktop PC, so there's no battery...

Sounds weird, huh?

I hope someone can help me, because on the Dutch Ubuntu Forums, they can help me now.

With Friendly Regards,

Rik de Graaff
Holland.

---

### Post by slasherfilmmaniac on 2010-06-12
I am having the same problem. My computer is a used Dell Dimension 4500s.

---

### Post by MapleAwesome12 on 2010-06-16
The same. Unfortunately nobody seems to be replying. I've bumped my thread 4 times, hoping to get a reply. This seems to be common for old Intel chipsets and processors, as well as users with dual Nvidea-64 cards. Of course, users with Nvidea have it easy, since the newer systems are more supported nowadays... ACPI isn't available on these aged Dell machines. Why does Ubuntu assume you're on a laptop? Is the filename of the iso not meaning "desktop" like it should? I'm lost. I can't get support here, or on the IRC... I don't know anymore.

---

### Post by MrFairladyz on 2010-06-24
I also have this problem on my HP Pavillion 752n (also uses a P4 processor).

One thing I've noticed is this happened usually always when I'm using a lot of RAM (of the 512mb I have installed). A few programs will run then it will totally die and display the Checking Batter State screen...

We all have a Pentium 4 processor and an Intel 845 GL chipset.

EDIT: Also, this always happens whenever installing new software.

---

### Post by sanjaydas7 on 2010-07-06
i just installed the 10.04 LTS desktop version and i get the same problem 15-20 mins after booting. can anyone help?!?

---

### Post by MrFairladyz on 2010-07-09
I installed Xubuntu 10.04, and that worked much better, but I got the same problem on the second day of use. No new developments so far... :/

---

### Post by guigarfr on 2010-07-12
same here

---

### Post by shaunk on 2010-07-13
I'm having the same problem here.  I recently installed Ubuntu on an older Dell Inspiron 1100 laptop with a pretty much dead battery; however it's been working fine for years as long as it's constantly plugged in.

I had 9.10 installed and I didn't notice this problem until I upgraded to 10.4 today.  I thought maybe the upgrade didn't work so well so I did a fresh 10.4 install but I'm still seeing this problem.

---

### Post by MapleAwesome12 on 2010-07-18
I don't think the admins are caring one bit about us. It'd be good if they at least gave us PROOF that they either are or aren't working on our situation. I've gone for 4 weeks with this crap, and I'm getting sick of the Ubuntu community. It's like they're trolling us without using a single word, telling us "BUY A NEW COMPUTER" or some stupid ****. I'm tired of bottling up the language. If we don't have the money, how the hell do we get a new computer? They aren't ****ing free. I'm raging for ALL of the users who are being tortured just because they are using Ubuntu on an Intel computer. It seems Dell is the most common company this problem occurs with. GIVE US A DAMN SIGN, UBUNTU ADMINS AND DEVELOPERS! WE WANT OUR PROBLEM TO BE HEARD AND FIXED!

---

### Post by djinnkeeper on 2010-07-26
Add one more to the list.  My mother is trying Xubuntu 10.04 and is getting the "Checking Battery State" problem.  Dell Dimension 2400 .. p4 blah blah.. Personally, I don't really care, in the long run, because this is a temporary solution until I can order some parts for a new system.  Just HAD to get XP off of it ASAP and she needs it to check email and crap.  (Windows and Firefox were somehow hijacked.. didn't even want to try to figure out what happened.. just wiped it and changed passwords)

All of that said, it is still pretty frustrating to find out that no one appears to be giving this the usual attention such a weird problem tends to garner.

I know this is not a solution, but for people content with P4 performance, I would suggest saving for an Atom-based board/system/laptop.. they perform slightly better than the average P4, are super-duper low power, very quiet and very cheap.

Hopefully the problem will be fixed by the time I kill this old beast.

---

### Post by tophatandy on 2010-07-27
I am having the exact same issue. 

As for a permanent fix, I am lacking one. Sorry. 

I do however have a temporary fix. Press Ctrl+Alt+F1 it should now prompt you to log in. I would recommend logging in to your profile to prevent any serious 'oops' moments, but you can log in as root here. Now we should get our normal terminal, where type:
```

sudo /etc/init.d/gdm restart

```

This is what is allowing me to use my machine for now. Let me know if it works for you guys.

I got my error after messing around with switching from GNOME (ubuntu-desktop) to KDE (kubuntu-desktop) then back to GNOME (ubuntu-desktop).

Good luck!

---

### Post by tophatandy on 2010-07-27
For now, I made a script to help me with boot up. You can do it all from the shell that I described how to get to in my previous post. basically what we do is:
```

nano

```

This will launch a in terminal text editor. Now for the script:
```

#!/bin/bash
#
#Starting GDM
sudo /etc/init.d/gdm restart

```

From here, you should save the script by pressing Ctrl+O. You should now be prompted for a filename, just save it something like 'boot.sh' (just make sure that the filename has .sh at the end and you are saving this script in your home directory.Leave the text editor with Ctrl+ X. Now to make it executable we use the command 
```

sudo chmod 755 boot.sh

```

Obviously, if you didn't save your script as 'boot.sh' swap that out for whatever you saved it as. We can now run that script so long as it is in our directory with 
```

./boot.sh

```

Now you have made an awesome script that should boot your GDM.

---

### Post by tophatandy on 2010-07-27
Seems somewhere in there I got confused about the issue. I am getting this on boot up. It might work for those who are getting this issue on boot up. 

For the others, have any of you filed a bug report yet? If not, I will see to it that there is a bug report filed.

---

### Post by redstarmachineworks on 2010-08-01
Same problem here at boot. It's a generic build with an Intel mobo and some socket 775 CPU. Ran the online update from 9.04 to 10.4 and it wouldn't reboot.

The above workaround doesn't work for me. When I try to run /etc/init.d/gdm restart, I get a message telling me to run "service gdm restart" instead, and that doesn't work either. It seems that the GDM isn't starting and can't be started.

---

### Post by tophatandy on 2010-08-05
sounds to me like gdm got fouled up somewhere along the way and might not be there (?)

I would recommend trying 
```

sudo apt-get install ubuntu-desktop

```

let me know how this goes.

---

### Post by ithkimdmb on 2010-08-24
I don't know if this is a fix yet, but I went into synaptic and found that a power manager for when running on battery was installed. So I just did a complete removal. pm-utils-powersave-policy 0.3.1 is the program. I'm running an old HP desktop.

---

### Post by ithkimdmb on 2010-08-26
Sorry it didn't work.
;)

---

### Post by e.m.fields on 2010-09-06
Having same bug. Ubuntu Maverick 10.10 Alpha 3.
Was working fine, suddenly it's now hanging at boot, with error message "Checking battery state..."

I cannot "sudo /etc/init.d/gdm restart" because I'm getting error message something about "gdm is now preferred to be started as a service, e.g. service gdm start" or something similar.

I cannot restart GDM after this hang in Maverick, or don't know how. Anyone know?

---

### Post by marcio123 on 2010-10-01
Same bug here ... just installed 10.10 RC 

Asus UL50V

---

### Post by Ubangi on 2010-10-11
and here!

---

### Post by nutznboltz on 2010-10-11
> **slasherfilmmaniac said:**
> I am having the same problem. My computer is a used Dell Dimension 4500s.

I just got an unbootable DELL Dimension 4500S to work.

Can you please test and report if this works?

memory_corruption_check_size=128K

in the boot options.

The default is

memory_corruption_check_size=64K

but it seems that's not enough for some systems.

Thanks

If you don't know how to set BootOptions read

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Also this thread is very important to anyone looking at this bug

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-07/msg04621.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-07/msg04621.html)

---

### Post by Ubangi on 2010-10-12
no it doesn't help - any other ideas?
I am using AMD64

---

### Post by prodigy2050 on 2010-10-13
same thing is happening to me too! i have a compaq C506TU and was upgrading from 10.04 to 10.10 when this happened. i googled a little and found that this happens due to problems with the graphic driver. i have a intel 945GM chipset. what do i do now? :mad:

---

### Post by francisco tovar on 2010-10-15
Im having the same issue here. Asus K50I. Ubuntu Karmic Koala was working fine, but upgraded to Maveric and on battery, system freezes...
any help welcome
cheerios

---

### Post by ssamdani on 2010-10-17
Same issue here. Upgraded from Ubuntu 10.04 to 10.10 last night and have not been able to get past this message "Checking Battery Status"

Using a Dell Latitude D400 with an on board Intel Card

---

### Post by PollekePol on 2010-10-18
Same problem here. Updated my HP laptop from 10.04 LTS -> 10.10  yesterday. When booting I just see this black screen with a blinking  cursor in the top left. When doing CTRL+ALT+F7 I see it hangs at the  message 'Checking Battery Status'. Of course (?!) this has nothing to do  with the fact whether your system has a battery. Guess it's because it  f*d up the configuration for the graphics card, is not able to start X  anymore? My laptop has an onboard Intel card. I see many threads with  the same issue. But nowhere a solution yet.

---

### Post by marcio123 on 2010-10-18
When I reinstalled ubuntu without internet connection (no automatic updates), on ac/dc power it started working

---

### Post by alekkova on 2010-10-19
I have the similar problem.
My Aspire 5725 freezes menu time after restart when battery is inserted.
When battery is not inserted in computer it works without problem.
I use Maverick Meerkat x64.

Best regards.

---

### Post by alekkova on 2010-10-19
I work with clean install on Aspire 5735.
If I wont to start my computer (when its freeze) I must disconnect battery and power and press and hold power button 5 or more seconds.
After that (connected battery and power) computer work but not too long.
If computer get slow work (form time to time it freeze pictures) I now it will be a problem with restart.
I test with old windows XP my computer (with inserted battery) and it works very well (menu ours without any problems).

---

### Post by pwabrahams on 2010-11-04
I had 10.10 Meerkat running fine, except for sound problems, on my Asus K60I. After installing last night's recommended update (0100 EDT, 11/4), I also get stuck on "checking battery state".  From what I read, it seems that the problem is related to the video software and has nothing to do with the battery.  But because I'm working with a crippled system, I don't even have access to any tools for fixing the problem (if I knew what's wrong).

I'm puzzled as to why more people haven't reported the problem with this update.

---

### Post by Ubuntiac on 2010-11-04
I just got this today and figured it out.

There seems to be a packaging / update problem with the KDE 4.5.3 packages and the system (Kubuntu Maverick) doesn't pull in all the new packages it needs. Here's what fixed it for me:

1. When the system gets to the point it just stops (Plymouth splash / Checking Battery State message) push ctrl + alt +f1

2. Log in and update your packages by typing in:
```
sudo apt-get update && sudo apt-get upgrade
```

3. Pull in the missing packages with:
```
Sudo apt-get install -f
```

4. Just to make sure, configure any uninstalled packages lying around with:
```
sudo dpkg --configure -a
```

If step 3 or 4 pull anything new in, repeat them once more just to be sure.

5. Restart

---

### Post by pwabrahams on 2010-11-04
Just out of curiosity, why did you combine the update and upgrade into a single (conditional) command but leave the others independent?

---

### Post by pwabrahams on 2010-11-04
I followed the suggested procedure and updated/upgraded my system.  Indeed, the process brought in a plethora of new or replacement packages and apparently installed them without any problems.  But I'm still stuck on the battery message.

I get the impression that the battery message has absolutely nothing to do with the battery.  It's just that the boot process hangs on the step following the battery check -- and I think that step has to do with starting the graphical environment.  But knowing that is not helping me figure out what to do about it.

---

### Post by pwabrahams on 2010-11-04
Following the suggestion in another thread, I did **apt-get install xorg gdm**.  That got me going -- but in the gnome environment rather than in the KDE environment that I wanted.  I thought that **apt-get-install kdm** would solve that problem, and indeed the installation procedure gave me a choice between kdm and gdm.  But having chosen kdm, I got gdm anyway.  That's where I am now.

So how can I go back to kdm?

---

### Post by Ubuntiac on 2010-11-05
> **pwabrahams said:**
> Just out of curiosity, why did you combine the update and upgrade into a single (conditional) command but leave the others independent?

I think I did from memory. I may have done them all separately though.

This was on a desktop (and thus no battery). I wonder what you'd get if you uninstalled gdm?

---

### Post by r7000 on 2010-11-05
> **Ubuntiac said:**
> I just got this today and figured it out.

There seems to be a packaging / update problem with the KDE 4.5.3 packages and the system (Kubuntu Maverick) doesn't pull in all the new packages it needs. Here's what fixed it for me:


These steps worked for me fixing an upgrade to Lucid Lynx 10.04 with this issue on VMware.

I had to go back and reinstall held back packages with sudo apt-get safe-upgrade as not everything was upgraded first time around.

Thanks Ubuntiac!

---

### Post by pwabrahams on 2010-11-08
**apt-get safe-upgrade** doesn't work -- **safe-upgrade** is not accepted by apt-get:```
pwa@Asus-laptop:~$ sudo apt-get safe-upgrade
E: Invalid operation safe-upgrade

```  But **aptitude safe-upgrade** works just fine.

---

### Post by mngsailing on 2010-11-14
I think I can help a little.
I have a situation in which some process is filling up my / partition.  I suspect it is sbackup which backs up /var/ and puts the result in /var/.  Anyway it does not put the backup where I want it on an external USB drive. 

After '/' has no space left, any process that needs disk space can crash. Checking Battery State saves battery statistics so that is one.  Starting the GDM display is another. 

I found a Backup directory and a file of 7.5GB in /var and removed it.  This freed 7 GB and helped me start. But it didn;t last, because the fillup process has resumed.  Now I am looking for snother process gone wild.  This time it is not in /var.

---

### Post by pwabrahams on 2010-11-15
As I understand it, the freeze on "Checking battery state" has nothing to do with the battery -- people get it even on desktops.  I think it's the step following the battery check that's hanging up -- most likely starting the graphical interface.

---

### Post by tdapower on 2010-11-17
[SIZE=3]This is not a very good solution for your problem, But I also had the same problem as you and after I found this method to solve that, This works fine without stuck or freeze.
goto 

[COLOR=Red]http://tdapower.wordpress.com/2010/09/02/to-avoid-stuck-ubuntu/[/COLOR]

and see.[/SIZE]\\:D/

---

### Post by pwabrahams on 2010-11-17
The battery check hang probably has nothing to do with the battery. In fact, people have seen it on desktops where there is no battery. It's the action after the battery check that's hanging, I believe.  In most cases that would be the startup of the X graphical environment.

I posted this to another thread but it might also be useful here.

---

### Post by devanalias on 2010-11-20
I had this prolem and I found a solution that helped me.
That is not a battery (or acpi) problem because it says "checking battery status.... **OK**"
It hangs later, is a library problem.
Try typing xinit after shell logging
Then, if doesn't work I can't help you.
If xinit works try gedit or any similar gtk programm.
I think you'll get a undefined symbol g_malloc_n ... or something about libgdk-x11....
If thats your case go here: [http://bugs.launchpad.net/ubuntu/+bug/301601/comments/7](http://bugs.launchpad.net/ubuntu/+bug/301601/comments/7)

good luck!

---

### Post by icone on 2010-11-25
sudo nano /etc/X11/default-display-manager

There shouldn't be anything else than this on Ubuntu 10.10 Gnome:
/usr/sbin/gdm


That solved the problem for me.



Cheers.

---

### Post by settface on 2010-11-25
I got this issue with Maverick after attempting to install CDM([Console Display Manager]("https://wiki.archlinux.org/index.php/CDM")). It pretty much broke everything, and after an hour or two trying to revert everything back, i came across the hanging after Battery State check issue.

after manually trying to find the problem in pretty much every x-server, gdm and init.d script, i opted for this:

1. Reinstall x-server and gdm, hoping they will autoconfigure themselves(baffle me when it didn't work, but it might for others):
```

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install --reinstall gdm xorg

```

2. ensure that gdm is the default display manager, as icone mentioned. **/etc/X11/default-display-manager** should contain */usr/sbin/gdm* as the only uncommented line.

3. try devanalias' fix(turns out i didn't have the same problem):[http://bugs.launchpad.net/ubuntu/+bug/301601/comments/7]("http://bugs.launchpad.net/ubuntu/+bug/301601/comments/7").

4. restart the gdm service
```
sudo /etc/init.d/gdm restart
```

trying 4 actually worked, which leads me to believe that somehow its entry as a service was removed from one of the startup scripts and i missed it during my first perusal. any ideas of where gdm is launched from in terms of scripts would be useful information. restarting the service manually probably triggered a script that adds gdm to start-up again.

---

### Post by a-user on 2010-11-25
i am still observing this quite huge delay after the "checking battery ..." message. the funny thing is when this message appears 1 sec later i see a tty console log in. i see it for about 8 or 10 sec than i see the bootmessages again for 1 or 2 sec where checking battery state says "ok".

then x / gdm starts.

i really would like to know what causes this long delay. anybody an idea where to look?

p.s. i did not had this after a fresh install. i think it came after installing the propritiary nvidia drivers.

---

### Post by ubscott on 2010-11-27
add me to the list.  here's my thread on this subject:
[http://ubuntuforums.org/showthread.php?t=1627798](http://ubuntuforums.org/showthread.php?t=1627798)
 
what's frustrating is the Live CD of 10.04 boots into Linux just fine.  however, the 10.04 that's on my Dell machine can't get past the 'checking battery state' part.
 
i wish the Ubuntu team would come up with a fix.  there's a lot of old Dell desktops out there.

---

### Post by ubscott on 2010-11-27
hi,
 
i'm pleased to say that my problem has been solved:
[http://ubuntuforums.org/showthread.php?t=1627798](http://ubuntuforums.org/showthread.php?t=1627798)
 
thanks,

---

### Post by lithla on 2010-12-15
Hi All,

I got the same problem after the restart, during ubuntu 10.10 installation.
Then I tried the following as advised Ubuntiac: 


> **Ubuntiac said:**
> 
```
sudo apt-get update && sudo apt-get upgrade
```

```
Sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

If step 3 or 4 pull anything new in, repeat them once more just to be sure.


A lot of packages have been installed, but I still got the problem.
Then I've installed kdm as pwabrahams did
> **pwabrahams said:**
> Following the suggestion in another thread, I did **apt-get install xorg gdm**.  That got me going -- but in the gnome environment rather than in the KDE environment that I wanted.  I thought that **apt-get-install kdm** would solve that problem, and indeed the installation procedure gave me a choice between kdm and gdm.  

It runs with the following message:"Ubuntu is running in low-graphics mode..." and that I need to change graphic settings manually.
I could choose with kdm to start the system with low graphic mode for this session only. So do I
And now I'm looking how to set the correct graphics options manually...

---

### Post by ibrabeicker on 2011-02-23
I had the same problem after removing my ati vga and switching to the intel on-board, I couldn't pass checking battery state then I entered the recovery mode in grub and then "failsafe X". There it said that my video card/display/driver could not be detected, so I chose "use default configuration" and then I was in my gnome desktop again, but the problem persisted on the next boot so I did the same thing and followed one of the posts and did 

```
sudo apt-get install --reinstall gdm xorg
```

and done!

---

### Post by ericxoff on 2011-02-24
this may help...
I was on a virtualbox with this error, so it was a nightmare trying to get networking up.
I was able to attach the .iso image of Ubuntu and boot successfully with that by clicking try Ubuntu. Once booted up I was able to mount my original virtual hard drive to the current "try Ubuntu" os, then I copied the entire /usr/lib from the .iso to my mounted hard drive.
It fixed it... but I still have some work to do to get back to where I was before the lib error.

---

### Post by AjitJor on 2011-02-28
Hi All.

I am running Lenovo T400 and I have encountered the same problem.
Essentially the boot would halt at 'checking battery ....'

I have found this at launchpad: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/619008/comments/11](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/619008/comments/11)

And ... it solved my issue !

It needs to be added (to the solution above) that on my BIOS I not only _had to change the graphics card mode to 'Discrete'_ I also had to disable the 'os switching' option that presumably allows the OS (and I guess the OS is MS-windows) to freely switch from 'Integrated' to 'Discrete' graphics. Therefore I am now using only the 'Discrete' graphics mode (took me some time to figure out why I select 'Discrete' but when my system halts the BIOS seems to have had returned to selecting 'Integrated' graphics)

---

### Post by Scucci on 2011-02-28
I was just having this issue on a Fujitsu LifeBook (B6110D). I was try'ng to get the touch screen to work, created the xorg.conf file (since there wasn't one in /etc/X11/ to begin with...) When I rebooted to check my work, got stuck at that screen.

ALT+CTRL+F1, logged in and removed xorg.conf (renaming would probably work the same). SU'd and rebooted and she was good to go.

---

### Post by Beowolf64 on 2011-03-03
My HP Pavilion dv5 having the same problem. It makes a strange click sound and freezes. Tried every suggestion from this thread. Nothing worked so far. OS is Maverick 64 bit.

---

### Post by pwabrahams on 2011-03-03
> **Beowolf64 said:**
> My HP Pavilion dv5 having the same problem. It makes a strange click sound and freezes. Tried every suggestion from this thread. Nothing worked so far. OS is Maverick 64 bit.

Try typing Alt-Ctl-F2, which will bring you to a separate text console.  If you can work from there, you've probably got an xorg/gdm/kdm problem.

Not an answer, of course, but a way of getting more information.

---

### Post by cordor on 2011-03-11
NO, i don't think it has anything to do with GDM, it is sexy and beauty, and almost you can't break it. most likely restart gdm solve the problem because that reset a timestamp somewhere. 

try this:

sudo service acpid stop
sudo service acpi-support stop

if your computer doesn't turnoff/freeze/reboot itself anymore, then there is error in the power management settings. Go fix it. If you couldn't fix it, just disable those services so they won't autostart on system boot up.

sudo update-rc.d -f acpid remove
sudp update-rc.d -f acpi-support remove

But then your computer will not do power management such as power down monitor while idle ...

---

### Post by tilator on 2011-04-26
Hi Ubuntuforum

For me the answer was quite simple: nvidia-xconfig did leave one row from xorg.conf **uncommented**.

This is what prevented X from starting for me.

The row needed to be commented (set #-mark in front of the row) started with "generated from initial ..."

---

### Post by korchiondo on 2011-06-06
I pushed alt+ctrl+f1, then login and password, after - sudo dpkg --configure -a  ..now i can use Ubuntu again. Hope it will help

---

### Post by nidhinmd on 2011-07-28
Hi all

Logged in to shell and go  to /etc/X11 check backup of xorg.conf(eg : xorg.conf-backup-11281011) is created. If present, rename that file to xorg.conf and restart.  This fixes my issue.

---

### Post by aquarius18 on 2011-07-30
I have been trying to set up an older IBM ThinkCenter for my wife. The machine has Win7 installed. Re-partitioned the 250Gb HDD and allocated 150Gb for Win7, 100Gb for the proposed 11.04 install. Everytime I am trying to load Natty the same old "Checking Battery State" message comes up and the system hangs. Did most of the recommendations in this thread to no avail - such as:

> **korchiondo said:**
> I pushed alt+ctrl+f1, then login and password, after - sudo dpkg --configure -a ..now i can use Ubuntu again. Hope it will help

> **nidhinmd said:**
> Hi all

Logged in to shell and go to /etc/X11 check backup of xorg.conf(eg : xorg.conf-backup-11281011) is created. If present, rename that file to xorg.conf and restart. This fixes my issue.

By 2am I had enough. ](*,) ](*,)

This thread covers many different versions of Ubuntu - going back a few years now - but nobody has come up with a fix.

There has to be a definitive solution to this!

Any takers please??

---

### Post by johns996 on 2011-09-09
I don't know if people are still having problems with this or not, but I got the same error today after trying to set up a second monitor on 10.10.  I was using the nVidia X Server Settings option to set up the monitor and something about it hosed my system.  The only way I got it back up was by doing the following.

[LIST]
[*]alt control f1
[*]log in
[*]sudo rm /etc/X11/xorg.conf
[*]sudo shutdown -r now
[/LIST]

After this everything booted up just fine, I only had a single monitor but that was expected.

---

### Post by mrdragon333 on 2011-09-19
+1
I am also facing this problem

---

### Post by s9032g@comcast.net on 2011-09-20
If your problem is false messages about a low battery, followed by shutdown, the here is your answer:
SOLVED. It is related to the Ralink wireless card. To fix, just do: 

Code:
cd /etc/pm/power.d 
sudo touch pcie_aspm
sudo touch wireless
Last edited by darincb77; 2 Weeks Ago at 06:04 PM.. Reason: Solved

I had the same problem, followed these directions, and it is fixed. You need to ask the right questions to get the answers. I think that the Ubuntu Community is terrific!

SteveG

---

### Post by anfractuosities on 2011-10-03
I had devices listed in my xorg.conf that did not have a section. Onse I deleted these devices from the top block of code (mouse and keyboard) it booted up. Still haveing issues with my monitors workign properly though.

---

### Post by hasfar on 2011-10-08
im using xubuntu 11.4. im having the same problem.just installed for the 4th time again. if i download something through torrents it freezes halfway through and if i restart i cant get past the 'checking battery state ' message.

---

### Post by The_Prat on 2011-10-20
I'm having the same problem. It all started when I disinstalled Kubuntu, on the next reboot I couldn't login into Ubuntu anymore.

---

### Post by tears of the river on 2011-11-29
Can someone please give me a sure fire way to permanently remove this error because seriously this is getting really annoying

---

### Post by dlanki on 2011-12-10
This solved my problem [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen). I was using an ati radeon 6800 and I was getting black screens. I simply appended:
 
set gfxpayload=1 
 
-in the grub loader. to get to the editing of the grub loader press e during the selection menu. It turns out ati radeon 6800 has some issues with resolution especially if you have a low res monitor that uses non standard resolutions.
 
Best

---

### Post by jaime.mx on 2011-12-19
I tried out other solutions but with not success. 
My problem was that Ubuntu couldn't start, it was locked in the line:
"batery state checking"

But your steps resolved my problem, thanks.

---

### Post by SchneiderIS on 2012-01-08
After loosing much time with this issue and reading through the posts here it became clearer that the majority of time this is a video driver issue.   

I solved my issue by installing the NVIDIA driver again.   This is yet another pet peeve of mine with Linux, it does not keep a registry of such installs in order to reapply they on kernel patches.

---

### Post by xyzzyman on 2012-01-09
> **SchneiderIS said:**
> After loosing much time with this issue and reading through the posts here it became clearer that the majority of time this is a video driver issue.   

I solved my issue by installing the NVIDIA driver again.   This is yet another pet peeve of mine with Linux, it does not keep a registry of such installs in order to reapply they on kernel patches.

If you use nvidia-current it does... If you install it manually it doesn't.

---

### Post by frenzy_usa on 2012-01-14
I fixed it by running
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install --reinstall gdm xorg
```

Got this problem after removing a bunch of installed software in the Ubuntu Software Center followed by a reboot.

Somewhere along the way I accidentally uninstalled xorg.

---

