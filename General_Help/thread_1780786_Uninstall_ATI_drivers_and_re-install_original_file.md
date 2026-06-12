---
title: "Uninstall ATI drivers and re-install original files ..."
date: 2011-06-12
forum: General Help
---

### Post by Bucky Ball on 2011-06-12
Hi all,

I am running a recently installed minimal install. I am having some fun building the system up but trying to keep things slim. I have installed the ATI catalyst drivers working from the tutorial here under 'Installing the Restricted Drivers Manually':

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_proprietary_drivers_.22the_ATI_way.22](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_proprietary_drivers_.22the_ATI_way.22)

After successfully getting the ATI driver running, I realise I really don't need or want it and am wanting to uninstall it completely and return the config to the way it was. Some of that I can do with the aid of some of the links I have found but installing the ATI drivers no doubt killed some of the packages that were there in the first place (graphics was fine in the first place incidentally).

Question: What might these squashed packages be so I can reinstall them and have graphics setup as it was before I  installed the ATI drivers and how can I remove all trace of the ATI drivers?

Is there a quick, clean and easy way of achieving these two things? Tnx in advance ... ;)

---

### Post by tredegar on 2011-06-12
I don't have ATI.

But the files for the original configuration should still be there.
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Will stop the ATI stuff being loaded.

Logout, login, and X should configure itself to use ubuntu's original defaults. 

If it doesn't you can reverse the **mv** above, and have another think.

---

### Post by Bucky Ball on 2011-06-12
Thanks for the tip. I'll try it. There was no /etc/X11/xorg.conf file to begin with as minimal install and not needed I guess. The ATI driver install created on and set it up. Guess deleting that file might have the same result.

* UPDATE: Yep, that mv definitely sped up the boot time again. Figuring I can safely delete the xorg.conf backup files as I have no xorg.conf file in use. I am now looking at removing the files suggested on this page:

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

Trouble is, it suggests that some of the original packages will now be missing as they were replaced by the restricted ones which will be removed. It gives a link to remedy this but there is no info on the link indicating which packages exactly I should re-install.

I'm hesitant to go any further as I am having visions of me spending eight hours battling in a terminal attempting to remedy a blank screen ...

---

### Post by tredegar on 2011-06-12
Some progress.
> 
Trouble is, it suggests that some of the original packages will now be missing as they were replaced by the restricted ones which will be removed.
Well, you could try just _printing out_ (in case you are dropped to the command line) the commands to remove the ATI driver and see how you get on. Printing out the relevant parts of the ubuntu wiki your link references would be a good idea too.
> there is no info on the link indicating which packages exactly I should re-install.
There is:```

[I]The uninstall script in the first command will only exist if you 
downloaded the drivers and installed them directly (rather than building 
packages as this guide does). Skip the first command if it does not 
exist.[/I] 

$ sudo sh /usr/share/ati/fglrx-uninstall.sh
$ sudo apt-get [COLOR="Red"]remove[/COLOR] --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx

$ sudo apt-get [COLOR="Red"]remove[/COLOR] --purge xserver-xorg-video-ati xserver-xorg-video-radeon
$ sudo apt-get [COLOR="Green"]install[/COLOR] xserver-xorg-video-ati
$ sudo apt-get [COLOR="Green"]install --reinstall[/COLOR] libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
$ sudo dpkg-reconfigure xserver-xorg
```

> I'm hesitant to go any further as I am having visions of me spending eight hours battling in a terminal attempting to remedy a blank screen ...

Presumably you have a backup? A reinstall takes < 8Hrs.
Or, if nothing's broken, you could leave well alone!

Good luck.

---

### Post by Bucky Ball on 2011-06-12
Why would I want to reinstall? Want to fix it. Minimal install which I've taken some time over, actually just want to remove all trace of the ATI drivers. So, you're saying the ones in green I should re-install? Thanks. Ones in red remove. Below is the result of the second command (the first file doesn't exist, as suggested):

```
tosher@binky:~$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting fglrx-driver-dev for regex 'fglrx_*'
Note, selecting fglrx for regex 'fglrx_*'
Note, selecting xfree86-driver-fglrx-dev for regex 'fglrx_*'
Note, selecting fglrx-control for regex 'fglrx_*'
Note, selecting fglrx-amdcccle for regex 'fglrx_*'
Note, selecting fglrx-dev for regex 'fglrx_*'
Note, selecting fglrx-modaliases for regex 'fglrx_*'
Note, selecting fglrx-kernel-source for regex 'fglrx_*'
Note, selecting xorg-driver-fglrx for regex 'fglrx_*'
Note, selecting fglrx-control-qt2 for regex 'fglrx_*'
Note, selecting xorg-driver-fglrx-dev for regex 'fglrx_*'
Note, selecting fglrx-amdcccle for regex 'fglrx-amdcccle*'
Note, selecting xfree86-driver-fglrx-dev for regex 'fglrx-dev*'
Note, selecting fglrx-dev for regex 'fglrx-dev*'
Note, selecting xorg-driver-fglrx-dev for regex 'fglrx-dev*'
E: Couldn't find package fglrx-dev*
```This is not just a regular Ubuntu install. It is a minimal I have been thinking about for a long time (and not minimal enough still) and I am doing my best to keep it as close to the bone as I can and still fulfill my needs production-wise. 

For instance, even though I have deleted the xorg.conf file as suggested and I am not using the driver, the junk still sitting around and whatever is being used of it has extended the time it takes to get from the grub selection menu to the login screen from 12 seconds to 20. Might sound petty to some, perhaps, but that is the aim of this install; rock solid racehorse with no fat. 

A re-install is ***always*** a last resort for me. (And yes, I have got backups - been repartitioning my machine and setting it up for the last three days; currently triple booting with Minimal 10.04 LTS, 10.10 and Win7.)

---

### Post by linuxinstalledfromhdd on 2011-06-12
try using slim and openbox too

---

### Post by Yellow Pasque on 2011-06-12
You're making it too difficult. Just run the 6 commands listed in the wiki and restart (X or the whole system): [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by Bucky Ball on 2011-06-12
Thanks for that. 

Well, I ran those commands, rebooted, and all seems normal. Graphics fine, etc. 

Question: why have I still got ATI Catalyst Control Centre and ATI Catalyst Control Centre (Administrative) in my settings? How do I kill these and the third-party ATI package and its diaspora completely?

* Update: Kill Catalyst Control Centre by going to Synaptics and removing fglrx-amdcccle. Logout then in again and it's gone. ;)

---

### Post by Bucky Ball on 2011-06-12
This shows some promise:

[http://www.ehow.com/how_7162488_manually-remove-ati-drivers-ubuntu.html](http://www.ehow.com/how_7162488_manually-remove-ati-drivers-ubuntu.html)

... but then I'm wondering if I would have any graphics after it ...

---

