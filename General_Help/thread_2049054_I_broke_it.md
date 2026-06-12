---
title: "I broke it"
date: 2012-08-27
forum: General Help
---

### Post by Osteonectin on 2012-08-27
I apologize, I am very new to ubuntu, and not sure how I even got to this mess, but I hope someone can help

I had the os up and running well, I came home And noticed the unity. Launcher missing, so I went to restart the computer and noticed updates, and updated then restarted.
On restart, it worked, but the graphics were all off, attempted nvidia x settings, and received an error message, sorry I don't remember wait it said, so I downloaded and installed new drivers.
On reboot now I only get "ubuntu 12.04.1 LTS myname MS 7673 ttyl
Myname-MS-7673 login:" at the top of the screen, and don't know what to do, please help

O

---

### Post by oldfred on 2012-08-27
Welcome to the forums.

That sounds like the non-gui or terminal login. Can you login? It is the same - username & passwork. But you will be at a terminal.

Then try ( all the # are comments do not type anything after a #)

#if not chroot use: 
sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

All that does is update it again. It may be video issues. What video so you have and did you install new drivers?

---

### Post by Bashing-om on 2012-08-27
Osteonectin ; Hi !

   I expect that what you see is a command line prompt in tty1..

Lets see what happens when you log into your system, and try to get the GUI started.
     at the prompt type your normal username and hit the enter key.
     next will ask for your password //enter that...
     prompt is waiting for next command enter:
```
sudo service lightdm start

```     and password again....
 I expect/hope your desktop is started.

 If so we will re-install your desk top. Please advise on the results of the above>
[INDENT]  regards <==BDQ

[/INDENT]

---

### Post by Osteonectin on 2012-08-27
Thank you oldfred
I was able to login
Typed in all suggestions
Apt-get distro and -f install netted 0 upgrades, ect, don't know if that's important
And last command receive error MSG unknown option --config, and displayed help options

Video card- GeForce gtx550 ti
And I did install new drivers - before I ended up at tty screen

Should I reboot now

---

### Post by Osteonectin on 2012-08-27
Bashing- om, thank you

Unfortunately a no go with lightdm start command
Just a lot of text and a blinking cursor at the end

---

### Post by Moose on 2012-08-27
Hey Osteonecctin, I don't want to be off topic but the title of your thread made me laugh :D

---

### Post by oldfred on 2012-08-27
Did you install the nVidia drivers? Or do you know if they were installed. I think they now install if you check the box to install the proprietary drivers. I did not do that and still had to do nomodeset until I got the nVidia driver working.

 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Some new system also need other parameters also.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by Osteonectin on 2012-08-28
Thanks anarchy tech I hope to add "we fixed it"

Oldfred, sorry wish I could spend all day getting this fixed but had to go to work
I hope you 
Or anybody else is still willing to help
I tried  apt-add-repository ppa:ubuntu-x-swat/x-updates, but no Internet connection
I read through you're links provided, but I'm sorry it just confused me more, 
I rebooted and still same screen, next step???

---

### Post by oldfred on 2012-08-28
I prefer to only install the Ubuntu versions of nVidia, not the bleeding edge versions you get from some other site.

Have you tried the nomodeset on boot or the rescue mode (second line in grub menu)?

---

### Post by Osteonectin on 2012-08-28
If I understand correctly, after bios splash, hit shift.......changed temp with no modest, Ctrl x, and back to same tty1 screen
Should I do permanent, if so
edit can't I do it through a nano command
And change the line to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
Save 
Exit 
"sudo update-grub
Reboot
Should work, is that correct

---

### Post by Osteonectin on 2012-08-28
I'm sure you guys hate it when we try other things, but I did boot from an earlier version and got the correct splash screen, but same distorted graphic, that prompted me to update the video drivers in the first place.  But it is working kinda.

There is a screen that says a volume with software packages has been detected , should I start it?

Or do something else altogether

---

### Post by oldfred on 2012-08-28
If it did not boot into the gui, then you do not have to make it permanent. 

Can you do this at command line after booting.

Manual install:
sudo apt-get install nvidia-current nvidia-settings
or
sudo apt-get --reinstall nvidia-current
sudo modprobe nvidia

sudo nvidia-xconfig
sudo reboot

---

### Post by Bashing-om on 2012-08-28
IRT "we try other things" => what works, works..

  What version do you now have booted? We see what options we have now.
  I can not imagine a "volume with software packages" unless you have the live CD source ticked in software sources. Best give us more information.

       BDQ

---

### Post by Osteonectin on 2012-08-28
Last 2 boots do go to the typical splash screen, but 1st input of pass, a bunch of strange syntax simultaneously adds at the top of the screen as I type my pass
I hit enter, and makes me renter the pass, And then good, but same graphics issue

Boots to Ubuntu 12.04 LTS
Graphics VESA gf106b board, should be GeForce gtx550ti

Ran code as recommended oldfred, unfortunately no changes, should previous be purged

Also click nvidia Xserves settings and error: you do not appear to be using the nvidia x driver please edit your x configuration, but I thought I did that

---

### Post by Bashing-om on 2012-08-28
Osteonectin ;

   oldfred's post 12 is the solution. did you catch the do this OR ? which did you do? ....as to the text appearing on the splash screen ... I have to ask--- have you done any edits to the grub file ?

reinstalling graphics driver: I see no harm in purging and re-installing, as per oldfred's directions.


[INDENT]HTH <==BDQ

[/INDENT]

---

### Post by oldfred on 2012-08-28
I have this in my notes on purging & reinstalling. Not done this but it looks right.

Boot to command line video issues
Remove nvidia drivers -> install nouveau -> reboot and let Ubuntu detect your videocard when you're running the desktop -> install the new drivers -> reboot.
#Remove nvidia
sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-current


sudo apt-get purge nvidia-common
#Install nouveau and remove the xorg.conf
sudo apt-get install xserver-xorg-video-nouveau
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

From man apt-get:
>        remove
           remove is identical to install except that packages are removed
           instead of installed. Note the removing a package leaves its
           configuration files in system. If a plus sign is appended to the
           package name (with no intervening space), the identified package
           will be installed instead of removed.

       purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).



---

### Post by Osteonectin on 2012-08-29
> **Bashing-om said:**
> Osteonectin ;

   oldfred's post 12 is the solution. did you catch the do this OR ? which did you do? ....as to the text appearing on the splash screen ... I have to ask--- have you done any edits to the grub file ?

reinstalling graphics driver: I see no harm in purging and re-installing, as per oldfred's directions.


[INDENT]HTH <==BDQ

[/INDENT]

I initially did the first 
Then tried the second and got an error message
Neither seemed to work

I did make a change to grub,  per MSG 7,8

---

### Post by Osteonectin on 2012-08-29
[QUOTE=oldfred;12203435]I have this in my notes on purging & reinstalling. Not done this but it looks right.

Boot to command line video issues
Remove nvidia drivers -> install nouveau -> reboot and let Ubuntu detect your videocard when you're running the desktop -> install the new drivers -> reboot.
#Remove nvidia
sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-current


sudo apt-get purge nvidia-common
#Install nouveau and remove the xorg.conf
sudo apt-get install xserver-xorg-video-nouveau
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

It worked, again sorry I'm new, but if I understand correctly I should have followed all the above, reboot, then reinstall nvidia.  I followed the above, rebooted and it started working, not complaining, just trying to learn

Thank you guys so much for the help

---

### Post by Bashing-om on 2012-08-30
I defer to old fred's possible forthcoming closing comments.

I am glad of the resolution. For others seeking solution, please mark thread as solved.

[INDENT]regards <==BDQ
[/INDENT]

---

### Post by HarshJ on 2013-03-26
I'm sorry to revive an old thread but i'm having the same problem and followed the instructions but could not make it.Please Help!!!

Be advised that i made a clean installation along with win 7 and an error occurred on the step that said installation of software ,rest of the installation was clean.

Now when i'm running sudo apt-get install nvidia-current    an error message says unable to locate package.

If i continue with the instructions than after this: sudo apt-get install xserver-xorg-video-nouveau   i get an error saying packag not available but is reffered to by another package.This means package is missing,has been obsolete or is only available from another source..


Being a newbie i don't know where i'm going wrong .Please help me fixing this!!!

---

### Post by oldfred on 2013-03-26
What version of Ubuntu? I still show it in my 12.04, I would expect it to be in every version.
xserver-xorg-video-nouveau is in my synatic.

How are you currently booting?

 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

