---
title: "Minimalist Distro with GUI Installation OR Custom Install Options"
date: 2010-05-13
forum: General Help
---

### Post by johnathanamber on 2010-05-13
Hey everyone!

I was wanting to know if there was a way to customize the Ubuntu installation during the GUI process?

If not, is there a distro that covers only what the system needs and then allows the user to install all of the apps they need instead of using the pre-installed apps?

The distro would have to cover:
Gnome (I don't use KDE, XFCE or any other one)
Drivers (Video, Network, Bluetooth, Sound, system, etc.)
Power management
Network Manager (wired, Wireless, VPN, Mobile Broadband, etc.)
Synaptic
Window Management
Gparted/Disk Utilities
Language Support
Printer Support

Basically the things you need to function the system with a GUI interface.

Then the user simply uses apt-get or Synaptic to setup their system.

Thank you very much and God bless,
Johnathan

PS: I started to use Reconstructor... but the problem is that I do not know the many packages required to accomplish the above. Is there a list available?

---

### Post by mörgæs on 2010-05-14
You could try a minimal Ubuntu:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

The first step in the installation is through command line, but you will soon have GDM and Synaptic running, from which you can do rest of the installation.

---

### Post by humbug01 on 2010-05-14
Hi Johnathan,
I just did this twice with Lucid (on my desktop and laptop) and did it 4-5 times with Jaunty on various machines. I'm NOT an expert in this but with the help of this forum I'm got a fast light machine I can tailor with the software I want.

Here are the essentials I've used with brief descriptions that I can figure out. I would recommend following/reading the discussions on the two links above by Moergaes.

After you have the command-line working, you can do: aptitude show "X" where "X" is the package you are thinking of installing and it will show whether it is installed and give a little info on it.

Essential packages I installed first (again, this is just what *I* did):

gnome-core   # this is 350+ packages and your gnome essentials

gdm  # log-in manager

gnome-utils # self-explanatory

gnome-system-tools  # various stuff

x11-xserver-utils  # stuff for X obviously

plymouth-x11  # graphics in boot up

plymouth-theme-ubuntu-logo  # boot up eye candy

plymouth-label  # more eye candy flashing on screen at boot

startupmanager  # I have subsequently gone back to grub 1 and deleted this

gnome-themes-selected  # = clearlooks theme. This is personal preference
## some like human and other themes. In any case you can install after
## gui installed

firefox
synaptic
gnome-power-manager
gufw  # for security
cups  # for printing; you can do more after gui installed


There's more, of course, like evince, gdebi (for installing from .deb's), but you can basically build up your system very easily from synaptic from the packages above.

Have fun!
Steve

---

### Post by kiepmad on 2010-05-14
Hey, 

you could try archlinux. It does not have a gui installation by default, but if you have some free time, it's definitely worth the time if you want to learn a bit more about how linux and computer work in general. :)

Archlinux only installs the base system. You then create your useraccount and install X and gnome all over commandline.

After that you can login and start installing some more. Archlinux is really cool because its package manager is so powerful, but/because it's only commandline

have fun.

---

### Post by johnathanamber on 2010-05-14
Thank you everyone!

I was hoping that there was a distro with ubunti and the minimal apps and GUI already done... since this obviously seems like a popular thing to do.

@humbug01,

Thanks for labeling out some of the packages.

@mörgæs,

I've thought about that. My only issue is that I do not have a wired connection... only wireless. Bot sure if the wireless drivers would already be integrated, nonetheless be able to connect to a wireless connection via the CLI to download Gnome.

@kiepmad,

Thanks for the suggestion. I would like to stay with Ubuntu.

@All,
As I have found, Ubuntu's community is far better than most other communities that I've had to work with.

God bless,
Johnathan

BTW, why isn't there a custom setup function available for Ubuntu during install?

And another question... the install that is being sent to the HD... does that mimic the changes that are made in the LiveCD?

---

### Post by mörgæs on 2010-05-14
> **johnathanamber said:**
> why isn't there a custom setup function available for Ubuntu during install?

Agree, that would make it a whole lot easier. In the minimalist thread you will find some scripts giving you the options as you go; this is as far as you get with menus.

> **johnathanamber said:**
> 
And another question... the install that is being sent to the HD... does that mimic the changes that are made in the LiveCD?

If you are thinking of a full installation: The CD does not change until release 10.04.1. That means that you are installing the 10.04 as of the release date, but you will probably add  the updates from the web right after the installation. 

Don't expect the wirefree connection to work for the minimal CD. Best is always to use a cable during the installation, both for a full and a minimal.

---

### Post by johnathanamber on 2010-05-14
Hey everyone!

Well I've used Reconstructor to build my own ISO of MinBuntu. The name may change since it *used* to be another distro I suppose.

Basically I selected what I could find to be a minimal GUI with some applets, firefox and chrome, the drivers for video and wireless, printer functions, network functions, grub2, custom repository script with basic repos, etc.

I'll load it in a VM to test. If it works out right then I will try reloading my system with it.

Again thanks humbug01 for some basics.

Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2010-05-14
OK I am a bit confused....

Using Reconstructor:
reconstructor.org

I keep getting the filesize over 700 MB.

Does anyone else use Reconstructor here?

Mind if you review myself to see what I am missing. the only two large packages taht I am inserting are the ATI and NVidia drivers. Given they together are over 120 MB... but that is about it that is that size. Everything else is under 1 MB.

BTW, rename:
MinBuntu_johnathanamber.gz

To:
MinBuntu_johnathanamber.rpj to upload to Reconstructor.

---

### Post by johnathanamber on 2010-05-14
OK, I DLed the Alternate CD.

Installed the text only version of Ubuntu
I've added the cdrom as a repository.
I've also updated aptitude.

When I tried to install a package, i.e. gdm, etc.

It tell me that the files can't be found and it lists a ton of files that it tried to find and install from the cdrom.

What am I missing here?

Thank you and God bless,
Johnathan

PS: Running a liveCD for now.

---

### Post by humbug01 on 2010-05-15
> **johnathanamber said:**
> OK, I DLed the Alternate CD.

Installed the text only version of Ubuntu
I've added the cdrom as a repository.
I've also updated aptitude.

When I tried to install a package, i.e. gdm, etc.

It tell me that the files can't be found and it lists a ton of files that it tried to find and install from the cdrom.


I don't quite understand this problem. In my experience, it's been pretty painless, so let me just list the commands I've done and see if that helps. (This is from my little black notebook I use to record Linux notes, but really comes from the links above.)

1. Use F4 from Alternate CD to install command line system and reboot when asked.

2. sudo nano /etc/apt/sources.list
# uncomment the CDRom (remove # in front) so that apt-get will pull latest files off CD Rom rather than internet. Save.

3. sudo mount /dev/cdrom /cdrom
# This was something I picked up on this forum because apt did not see the CD Rom in Lucid. I never had to do this before.

4. sudo apt-get update && sudo apt-get upgrade
# You did not say that you used the "upgrade" command above. As you probably know, it will upgrade the packages already installed.

5. sudo apt-get install gnome-core gdm gnome-utils gnome-system-tools x11-xserver-utils plymouth-x11 plymouth-theme-ubuntu-logo plymouth-label startupmanager gnome-themes-selected firefox synaptic gufw

6. Do clean up step in link above with logrotate and locale-purge etc.

7. sudo reboot

This *should* get you a basic gnome windows system. I do add a few more packages in step 5 like evince, gdebi, nautilus-gksu etc. that I find really helpful, but the ones above are the main windowing system I believe.

Again, I'm not an expert but I just did this twice with no problems on two computers....

God bless you too, H.

---

### Post by johnathanamber on 2010-05-18
@humbug01,

Thank you so much for your help.

I did as you've suggested... but for some reason it would not install from the CD. When I hooked it up to the wired connection, it gathered everything from the net and it all worked.

I do not know why it didn't from the CD. All I know is that it wouldn't work without the net connection.

It is weird... it informed that it could not 'fetch from the... cdname'. It MAYBE due to a bad ISO download or something simular. So once I get some new blank CDs I will re-download and re-burn and try again.

I want to be able to eventually make a script to do all this and make a minimal setup with all that you need without all the extra stuff that slows the system down. Thus far I am seeing a good performance increase by doing this.

Question... my sound doesn't seem to be working... the mixer is loaded and seems to be working... gives me the option to mute, etc.

Video drivers look good.

Had to install compiz to get the titlebar working.

Wired and wireless network connection are good and working.

Also, do you know which package does the notification system in 10.04... looks like I have the old one... with the colored bar on the left... etc.

Thank you very much for your help.

God bless,
Johnathan

---

### Post by humbug01 on 2010-05-19
Hi J.,

On not accessing the CD for installation, I had the same experience. The item #3 above solved that for me:
> 3. sudo mount /dev/cdrom /cdrom
# This was something I picked up on this forum because apt did not see the CD Rom in Lucid. I never had to do this before.

I can't help with the other questions, like notification. I am really minimalist. :)

Best,
H

---

### Post by johnathanamber on 2010-06-08
I did finally get it all working but had to use the wired cable... I will retry again via the CD another time.

I can post the scripts I've made thus far if anyone is interested.

Thanks Hum for your help.

God bless,
Johnathan

---

