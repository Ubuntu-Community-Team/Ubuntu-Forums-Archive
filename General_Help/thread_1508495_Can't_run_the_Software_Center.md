---
title: "Can't run the Software Center"
date: 2010-06-13
forum: General Help
---

### Post by Adrastus on 2010-06-13
[FONT=Arial][SIZE=2]I just installed Ubuntu 10.04 on my old desktop (winXP just couldn't handle a 10 year old hard drive) and I'm having a problem with the software center.  When I try to launch from the GUI I get a minimized window that says it's starting and then the application window pops up for a split second and then it's gone.  I tried to launch from the terminal and:

eric@eric-desktop:~$ software-center
Segmentation fault

...and that's about as far as I got.  This is my first Linux installation and I really have no clue what I'm doing with the terminal, it just seemed like the thing to do.

If there's a command I could run that would give a more detailed error report it I can post the print out up here but I honestly have no clue where to go beyond that.

Thank you[/SIZE][/FONT]

---

### Post by amite on 2010-06-13
> **Adrastus said:**
> [FONT=Arial][SIZE=2]  I tried to launch from the terminal and:

eric@eric-desktop:~$ software-center
Segmentation fault
[/SIZE][/FONT]

press alt+f2 :"Run Application" program here enter ubuntu sotware center it will launch ubuntu software center program.But as it is not launched on ur system so try these steps:
Open terminal :
$sudo apt-get update
then 
$sudo apt-get upgrade

after that if ubuntu software center works then fine else try this:
open system >> adminstration >>synaptic package manager
here search "software center" if it installed then reinstall it otherwise install it.and then try ubuntu software center.
good luck!

---

### Post by Adrastus on 2010-06-13
[FONT=Arial][SIZE=2]Thanks for your reply, Amite.

I tried the update first:

eric@eric-desktop:~$ sudo apt-get update
[sudo] password for eric: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Reading package lists... Done
eric@eric-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
eric@eric-desktop:~$ software-center
Segmentation fault

No luck there.

Then I tried reinstalling through the package manager as suggested:
> open system >> adminstration >>synaptic package manager
here search "software center" if it installed then reinstall it  otherwise install it.and then try ubuntu software center.No luck there either.

Any other ideas? Anyone?
[/SIZE][/FONT]

---

### Post by jmszr on 2010-06-13
Adrastus,

I had a somewhat similar problem and the fix was:

```
sudo rm /var/cache/apt/*.bin
```

Hope that helps.

Edit: Just noticed that you are unfamiliar with the terminal, so: Copy and paste the above command into the terminal, press Enter, if it asks for your password,type it in (it won't be visible-security) and press Enter again. That's it.

Here's a link to a thread about using the terminal:
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)   (Terminal for Beginners)

Edit#2: Here's another, quite helpful, more basic one: [http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338)  (Newbie Terminal Intro) . 
One thing - You will notice that the word "code" is used when "command" is actually the proper terminology.

---

### Post by kayvee on 2010-10-15
> **jmszr said:**
> 
I had a somewhat similar problem and the fix was:

```
sudo rm /var/cache/apt/*.bin
```



I am running Maverick and I had the same problem with USC. I came here after some googling and your suggestion worked!

However, instead of removing the bin files from /var/cache/apt folder, I moved them to xxx.bin.old files just so that I can revert back if necessary.

Thanks!

---

