---
title: "Lost GUI"
date: 2009-12-01
forum: General Help
---

### Post by f.bludevil on 2009-12-01
Help

First I have Ubuntu 9.10 installed on a IMac as a guest using Virtual Box.

Last night I tried to uninstall python 2.6  I had previously installed python 2.5.  A book I was reading advised that a download package to be used as a tutor along with the book could only be run with Python 2.5.  After I installed 2.5 I noticed my shell still showed python v 2.6 when I  entered python from the shell, so I came up with the happy idea of uninstalling 2.6.

I used the free software depository in the applications drop down menu, selected python v2.6 and hit the uninstall button.  I left the computer to talk with my wife, was gone for a minite or so and when I returned and my gui was gone and I was looking at a black screen with a blinking log-in prompt.

I logged in then used fn + alt + f6 hoping to return back to the gui and instead and was promptly returned to the log-in screen.

I have spent 3 hours now reading manuals, searching the forum for similar treads, trying to fix this problem - I have tried all the various suggestions I stumbled upon.

startx then sudo /etc/init.d/gdm restart
sudo apt-get install ubuntu-desktop 

and others that I can't remember now - however nothing has worked.  Although in the process I don't think I've caused myself any further harm - I still get to the shell - but no gui

Any help would be greatly appreciated.  I will be leaving for work - and hopefully will be able to return this evening and find the answer here.

---

### Post by chrisbay90 on 2009-12-01
> **f.bludevil said:**
> Help

...SNIP...

I logged in then used fn + alt + f6 hoping to return back to the gui and instead and was promptly returned to the log-in screen.

...SNIP....

startx then sudo /etc/init.d/gdm restart
sudo apt-get install ubuntu-desktop 

and others that I can't remember now - however nothing has worked.

...SNIP...


xorg is usally runs in tty7 (as in fn + alt + f7) although restarting gnome`/etc/init.d/gdm restart` should automatically bring you to tty7.

`sudo /etc/init.d/gdm restart` did not work. What did happen then? Any output from the terminal or observations of what gdm may have truied to do (flashing screen etc?)

Also on that note what does

```
sudo /etc/init.d/gdm status
```

yield?

Im not all that experienced with linux myself, so thats about all i can give you. I wish you all the best in sorting out your problems.

---

### Post by Cheesemill on 2009-12-01
Python 2.6 is a dependancy of most of the desktop apps and even gnome itself. By removing 2.6 you also removed all of the apps that use it.

Try doing:
```
sudo apt-get install ubuntu-desktop
```
this may get you back to a usable system (it will also re-install python 2.6).

---

### Post by f.bludevil on 2009-12-01
Cheesemill,

Thanks for the input

Using the sudo apt-get install ubuntu-desktop

returns lots of lines but basically the bottom line for each package it tries to fetch seems to be: "Could not resolve 'us.archive.ubuntu.com" 

It appears to me that it isn't able to connect to the software depository.  But then I've been using Linux for two months - so I'm guessing.

On that note it's back to work and hoping to resolve this tonight, before midnight I hope, gulp

---

### Post by Vakman on 2009-12-01
While you do not have the GUI enter:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This should restore the defaults and restore a usable desktop.

---

### Post by f.bludevil on 2009-12-01
> sudo dpkg-reconfigure -phigh xserver-xorg - This should restore the defaults and restore a usable desktop.

No luck, after I type the sudo command I get the normal prompt for password.  After I enter my password it returns to the prompt line without a message.

---

### Post by Megafag on 2009-12-01
> **f.bludevil said:**
> No luck, after I type the sudo command I get the normal prompt for password.  After I enter my password it returns to the prompt line without a message.

"startx" will give you a basic desktop temporarily. in theory...

---

### Post by doas777 on 2009-12-01
well first off, it looks like a network problem. I think network-manager has python dependencies, and besides that, if you are not logged in, it won't start running.

please post back the output of this command:
```
sudo cat /etc/network/interfaces
```

you can configure your network connection manually in your /etc/network/interfaces file
from the terminal, you can open it for editing in nano (a small cli text editor), with 
```
sudo nano /etc/network/interfaces
```
to save and close nano, just hit ctrl + x, and it will ask you if you want to save.

here is some information about configuring a wired connection:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

set it up for dhcp, unless you know your dns addresses.

---

### Post by f.bludevil on 2009-12-01
**Re: Lost GUI**
 well first off, it looks like a network problem. I think network-manager has python dependencies, and besides that, if you are not logged in, it won't start running.

please post back the output of this command:
     Code:
     sudo cat /etc/network/interfaces 
I get the following output:

auto lo
iface lo inet loopback

hope this provides some useful information - thanks for your help

---

### Post by f.bludevil on 2009-12-01
> **Megafag said:**
> "startx" will give you a basic desktop temporarily. in theory...

startx - It does one of two things.  It always closes the current terminal window and it opens a new window.  In some cases the window is a login prompt - other times it just opens another window with the standard home directory prompt ~$

The font is different the window title reads ubuntu [Running] - Sun VirtualBox but no luck with the GUI

---

### Post by doas777 on 2009-12-01
if you have a wired connection, add this to the bottom of the file:
```
auto eth0
iface eth0 inet dhcp
```then save your file, and run:
```
sudo /etc/init.d/networking restart
```

edit:L oh yeah, your in virtualbox. does the guest have a virtual network card, and which network type did you select at install?

---

### Post by f.bludevil on 2009-12-01
doas777

Again - thanks for sticking with me

eight lines of text starting wiht Listening on LPF/eth0/8:00:00 etc
then Sending on ditto

final line ends with  -- renewal in 42793 seconds

I'm not sure what that means - if I take it literally thats 11 + hours
is there a easy way to test my connection from the terminal?

---

### Post by tim_mozzie on 2009-12-01
Well I woke up this morning, turned my desktop Ubuntu 9.10 PC on and experienced the same thing. No GUI. Just the login prompt.

After a bit of reading around I found this thread and tried some of the suggestions.
"startx" just gave me a black screen with a mouse pointer.
"sudo /etc/init.d/gdm restart" didn't work because there was no gdm file.

So I did the "sudo apt-get install ubuntu-desktop" and after that gdm was there and "gdm restart" actually worked. Everything is good again.


So how could the ubuntu-desktop have just disappeared like that? This is really starting to bother me. Since I changed from 9.04 to 9.10 a bunch of things no longer work properly,  daily updates seem to cause as many problems as they fix, and I am losing confidence in the OS to the point that I'm seriously thinking of dragging out my old copy of Vista and upgrading it to 7.
Since it's working again now I will persist for a bit longer - keeping very frequent backups of everything just in case.

It's a shame because until I changed to 9.10 I had no reason to doubt Ubuntu at all.

Tim

---

### Post by doas777 on 2009-12-01
that looks promising. now try and enter:
```
ping -c 3 4.2.2.1 
```
hopefully the output will look kinda like this
> 
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=50 time=23.7 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=50 time=25.1 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=50 time=25.4 ms


if it works, try:
```
nslookup www.google.com
```
and see if it returns an ip address. if it does, then your network is up, so the next step, is to reeinstall the ubuntu-desktop package.

```
sudo apt-get install ubuntu-desktop
```

---

### Post by doas777 on 2009-12-01
> **tim_mozzie said:**
> Well I woke up this morning, turned my desktop Ubuntu 9.10 PC on and experienced the same thing. No GUI. Just the login prompt.

After a bit of reading around I found this thread and tried some of the suggestions.
"startx" just gave me a black screen with a mouse pointer.
"sudo /etc/init.d/gdm restart" didn't work because there was no gdm file.

So I did the "sudo apt-get install ubuntu-desktop" and after that gdm was there and "gdm restart" actually worked. Everything is good again.


So how could the ubuntu-desktop have just disappeared like that? This is really starting to bother me. Since I changed from 9.04 to 9.10 a bunch of things no longer work properly,  daily updates seem to cause as many problems as they fix, and I am losing confidence in the OS to the point that I'm seriously thinking of dragging out my old copy of Vista and upgrading it to 7.
Since it's working again now I will persist for a bit longer - keeping very frequent backups of everything just in case.

It's a shame because until I changed to 9.10 I had no reason to doubt Ubuntu at all.

Tim

gdm is now a service, so the command to start/stop it is
```
sudo service gdm stop
```the adivce we have been giving f.bludevil is specific to his problem, related to uninstalling the python runtime. I am glad that reinstalling the ubuntu desktop cleared up your issue, but since we haven't really diagnosed it, I don't feel comfortable saying that your issue had anything to do with an removal of dependant software or updates. I'm sorry your having a rough time with karmic. I recall a number of people had trouble with intrepid at first as well.

---

### Post by f.bludevil on 2009-12-01
doas777

I can't thank you enough for your help.  I thought I was there but I've run into another problem.  I ran the ping test,  I did get an ip address followed by some other messages that I failed to write down, although I think it was related to the address not my problem.

I re-installed the desk-top and then did a sudo/etc/init.d/gdm restart

My system then rebooted and my desktop appeared.  Then I received a reboot message - stating that a reboot was required in order to install some required files.  I rebooted and received a message "mount of filesystem failed. A maintenance shell will now be set-up and finally Control D will terminate this shell and retry.

When I use Control D the same output is repeated.  There is more to it than this although it's about six to eight lines with several references to "Mountall: fsck /[1801] terminated with status 4.  Mountall: Filesystem has errors: / Mount of filesystem failed

If you need me to I can print the whole thing out verbatim or if there is a way to copy from the terminal (I'm new to Linux - let me know).

In the mean time I am going to shut everything down and see what happens.

---

### Post by f.bludevil on 2009-12-01
doas777

Ok looks like I'm good.  I shut-down everything rebooted the system did a boot check when rebooting and I was returned to my desktop without any error messages.

I don't know how stable the installation is going to be yet - but I'm optimistic and once more grateful for the help.

Hope I will be able to repay the favor to somebody else in the future.

Many Thanks

---

### Post by doas777 on 2009-12-01
well, in the maintenence shell, lets run a disk check.
first we need to know the name of your partition. 
run:
```
sudo fdisk -l
```and look for your ubuntu partiton. note the name in the form of "/dev/sdx1" where x is a letter like a,b,c and 1 is a number like 1,2,3,4. the letter id's the physical drive, and the number, the partition on the disk.

replace your dev name below and enter:
```

sudo e2fsck -f /dev/sda1

```then reboot with 'sudo reboot'

Edit:
Great! glad it worked out for you. next time you rebuild, give some thought to sepperating your home directory to another partition. that way you can blow away your os any time without losing data. just rebuild your os and mount up the old home.

good luck and have fun

---

### Post by f.bludevil on 2009-12-01
doas777

I just reviewed your orginal reply which I imagine was to "my still having problems post".  I read up a little "Linux in a Nutshell" on the e2fsck and decided to give it a try.

First I when executed the fdisk command I got a table showing three partitions
/dev/sda1 boot * System = Linux
/dev/sda2 System = Extended
/dev/sda5 System = Linux swap / Solaris

I then ran sudo e2fsck -f /dev/sda1 

and I received the following message

WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.  Do you really want to continue (y/n)

Having spent two days recovering from my last exercise in curiosity (i.e. this can't possibly hurt - I already have another version of python installed etc., I bravely responded N as in "heck no".

On the other hand, I would like to do a check and repair but the triple exclamation point, upper case warning message leaves me a bit leery.  What's your recommendation - "leave well enough alone" or "be brave and learn?"

---

### Post by doas777 on 2009-12-01
no no. don't do it!

I'm sorry, that instruction was pertinent when you were unable to boot in the maintenence shell, not once the system is booted. I was writing that post while you were posting to announce your success, so I missed it, until you were past that part. sry bout that.

if you want to run a check, do it from a live cd, so that the root partition is not mounted at the time.

good luck!

---

### Post by f.bludevil on 2009-12-01
> **doas777 said:**
> no no. don't do it!

I'm sorry, that instruction was pertinent when you were unable to boot in the maintenence shell, not once the system is booted.

if you want to run a check, do it from a live cd, so that the root partition is not mounted at the time.

good luck!

no worries - I wasn't about to proceed without confirmation - I will go back and do a little more self-study before attempting  further surgery.

---

### Post by Cheesemill on 2009-12-02
> **tim_mozzie said:**
> So how could the ubuntu-desktop have just disappeared like that?

It disappeared because you uninstalled python 2.6. The ubuntu-desktop package requires python to run, by uninstalling python you automatically uninstalled **all** of the programs that need it as well.

---

### Post by Surachinen on 2010-03-04
okay, i had the same problem as the guy who deleted python (did the exact same thing) followed your guys's advice and my gui is back and raring to go. the only problems i had were the following

when i tried sudo cat /ect/network/interfaces it kept saying that no such file existed. i knew this to be untrue so i booted up from a live cd using the try ubuntu without installing option.
i then entered my hdd's file system and lo and behold, there was the file. it would not let me edit it at first, so i used gksudo gedit /ect/network/interfaces and added the two lines that this guide told me too (auto eth0 and iface eth0 inet dhcp) but it STILL would not let me save the edited file. so i got creative. i opened a basic text editor copy pasted what was in the interfaces file into the new file and i saved as "interfaces" in the network folder. a prompt then asked me if i wanted to replace the original file to which i said yes. it took like a charm and sudo apt-get install ubuntu-desktop worked fine after that. i only had a few issues/hiccups afterward

my google chrome and skype programs had been deleted for some reason and where my network used to appear on my upper bar it now says not connected to a network, though obviously i am (i did manage to post THIS after all!) so all in all im happy with the solution. thank you guys this forum was a life saver

---

