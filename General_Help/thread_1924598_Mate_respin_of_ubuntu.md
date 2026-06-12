---
title: "Mate respin of ubuntu"
date: 2012-02-13
forum: General Help
---

### Post by varunpr97 on 2012-02-13
I want to create a mate respin of ubuntu without unity 3d and unity 2d included as default? How do I go about things? Can I do that by removing the unity and unity lens packages and installing mate( a fork of gnome 2) and then using remastersys with the "dist" option to create the distro or should I use Ubuntu Customisation Kit(UCK). Or should I go about building the distro manually? I plan to start with this as soon as precise is released. I also want to upload the cd image and create a website for the project. Anybody intrested? I'm just 15:D and know some C so is that useful?

---

### Post by cwklinuxguy on 2012-02-13
Hello. I'm 16 and attempting essentially the same thing as we speak. Any chance in collaborating?

I'm working on the second Alpha release, which isn't going the best...trying to remove Unity makes Synaptic install Gnome Shell, and vice versa. What a nuisance. But yeah...wanna work together? [http://paradiseos.wordpress.com](http://paradiseos.wordpress.com)

---

### Post by varunpr97 on 2012-02-13
> **cwklinuxguy said:**
> Hello. I'm 16 and attempting essentially the same thing as we speak. Any chance in collaborating?

I'm working on the second Alpha release, which isn't going the best...trying to remove Unity makes Synaptic install Gnome Shell, and vice versa. What a nuisance. But yeah...wanna work together? [http://paradiseos.wordpress.com](http://paradiseos.wordpress.com)
Collaboration .... ya sure! but after precise release... Also we will have to make an attractive website.. We can try hosting our own server....And what are you using to make your builds?
Can you please  try this and tell me what happens?
add > deb [http://tridex.net/repo/ubuntu/](http://tridex.net/repo/ubuntu/) oneiric main to your software sources
> sudo apt-get update sudo apt-get install mate-archive-keyring sudo apt-get update sudo apt-get install mate-core This repository contains 300Mb of *pure* Mate-desktop packages - that is, the Gnome-2 packages after the fork. This will install mate...  
Now, uninstall unity by removing the foll. packages:
> sudo apt-get remove unity unity-2d-places unity-2d unity-2d-panel unity-2d-spread unity-asset-pool unity-services unity-lens-files unity-lens-music unity-lens-applications gir1.2-unity-4.0 unity-common indicator-sound indicator-power indicator-appmenu libindicator6 indicator-application evolution-indicator indicator-datetime indicator-messages libnux-1.0-0 nuxtoolsThis will remove Transmission and Tomboy, no problem there, just reinstall them after using
  > sudo apt-get install tomboy transmissionAnd then install remastersys and try to create the distro by using the dist command(just google it)
[FONT=Arial]I will begin work when I get a faster internet connection (using 50kbps 2g internet connection[/FONT]) I will get a 512 kpbs line after my final exams(after the precise release)
[COLOR=Red]_**NOTE:**_[/COLOR]Try this on ubuntu 11.10 and not 12.04(it wont work on 12.04) and see if you get some success.....

---

### Post by cwklinuxguy on 2012-02-13
> **varunpr97 said:**
> Collaboration .... ya sure! but after precise release... Also we will have to make an attractive website.. We can try hosting our own server....And what are you using to make your builds?
Can you please  try this and tell me what happens?
add  to your software sources
This repository contains 300Mb of *pure* Mate-desktop packages - that is, the Gnome-2 packages after the fork. This will install mate...  
Now, uninstall unity by removing the foll. packages:
This will remove Transmission and Tomboy, no problem there, just reinstall them after using
  And then install remastersys and try to create the distro by using the dist command(just google it)
[FONT=Arial]I will begin work when I get a faster internet connection (using 50kbps 2g internet connection[/FONT]) I will get a 512 kpbs line after my final exams(after the precise release)
[COLOR=Red]_**NOTE:**_[/COLOR]Try this on ubuntu 11.10 and not 12.04(it wont work on 12.04) and see if you get some success.....

I have already installed MATE in 11.10. The thing I've been having trouble with is removing Unity w/o installing Gnome Shell in the process. Does the terminal method avoid that problem? And yeah, I already know about Remastersys and plan to use it as soon as we're ready to build again.

---

### Post by winh8r on 2012-02-13
you might get some useful info here:


[http://ubuntuforums.org/showthread.php?t=1858282&highlight=MATE&page=25]("http://ubuntuforums.org/showthread.php?t=1858282&highlight=MATE&page=25")

hope this helps you.

---

### Post by snowpine on 2012-02-13
Also:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

(to install Ubuntu without Unity or Gnome)

---

### Post by cwklinuxguy on 2012-02-13
@winh8r: thanks. I keep an eye on that thread anyway. Like...ridiculously often.
@snowpine: so I assume the Minimal CD just boots into shell?

---

### Post by bluexrider on 2012-02-13
The perfectminimal

[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

Good tutorial

---

### Post by cwklinuxguy on 2012-02-13
Might look into that...it sure could make my life easier.

---

### Post by snowpine on 2012-02-13
> **cwklinuxguy said:**
> 
@snowpine: so I assume the Minimal CD just boots into shell?

Correct; then you install your choice of desktop environment and applications:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by cwklinuxguy on 2012-02-13
Cool cool. I've already started on a version with the regular Ubuntu 11.10, but we can consider moving to minimal after that.

---

### Post by varunpr97 on 2012-02-14
> **cwklinuxguy said:**
> Cool cool. I've already started on a version with the regular Ubuntu 11.10, but we can consider moving to minimal after that.
So what we essentially do is install mate from the minimal install cd so that we have only mate and not unity and then use remastersys? Am I correct?

---

### Post by cwklinuxguy on 2012-02-14
What we'd need to do is install the minimal CD, install the programs we want, install x11, install MATE, and THEN install remastersys. I've already started working on it, but I'm running into issues booting into the installation. I can't troubleshoot right now, but why don't you message me at your convenience and we can try and work on it when we have some free time?

---

### Post by varunpr97 on 2012-02-14
> **cwklinuxguy said:**
> What we'd need to do is install the minimal CD, install the programs we want, install x11, install MATE, and THEN install remastersys. I've already started working on it, but I'm running into issues booting into the installation. I can't troubleshoot right now, but why don't you message me at your convenience and we can try and work on it when we have some free time?
Ohk.... that will be a lot of work..... Did you try to remove unity through terminal after installing from from the main cd?
And is this what we have to do to install x11?
> sudo apt-get install x11-xserver-utils
And how do we install software center? is it:-
> 
sudo apt-get install software-center
??

---

### Post by Trapper on 2012-02-14
> **snowpine said:**
> Also:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

(to install Ubuntu without Unity or Gnome)

It would be nice to know exactly what items I must install to also have a bootable install of mate-core on this mini-install I've done of ubuntu 11.10. I've been working trying to get that. I installed mate-core okay and it installed many dependencies but I am nowhere close to getting it to actually boot up.

---

### Post by snowpine on 2012-02-14
> **Trapper said:**
> It would be nice to know exactly what items I must install to also have a bootable install of mate-core on this mini-install I've done of ubuntu 11.10. I've been working trying to get that. I installed mate-core okay and it installed many dependencies but I am nowhere close to getting it to actually boot up.

See here for a good how-to: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

(You won't need icewm though.)

---

### Post by Trapper on 2012-02-14
> **snowpine said:**
> See here for a good how-to: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

(You won't need icewm though.)

Okay, I previously looked that over and thought about doing that. I assume you are saying that I simply replace icewm with mate-core (after enabling the repo and getting the key). I will give that a try and will post my results.

I checked here first though because I was getting tired of reinstalling the minimalCD everytime I screwed things up. However, I've now tarred the entire fresh install to another partition so I can just format the minimal partition and untar everything back into it if need be.

---

### Post by snowpine on 2012-02-14
> **Trapper said:**
> I checked here first though because I was getting tired of reinstalling the minimalCD everytime I screwed things up. However, I've now tarred the entire fresh install to another partition so I can just format the minimal partition and untar everything back into it if need be.

VirtualBox would be ideal for this kind of experimentation. You  can use its Snapshot feature to roll back to a certain point in time.

---

### Post by Trapper on 2012-02-14
Here's the process I just used to successfully integrate MATE into a fresh MinimalCD installation that was done through the command line option of the installer. This complete MATE install is quite "barebones" but that was my aim and it's the box I am on now. Here are the steps I took:

```


sudo nano /etc/apt/sources.list

Add this repository:

deb http://tridex.net/repo/ubuntu oneiric main

sudo apt-get update

sudo apt-get install mate-archive-keyring

sudo apt-get update

sudo apt-get install xorg xterm gdm menu mate-core gksu firefox synaptic --no-install-recommends

sudo service gdm start


```Just a note ... After you install U1110 from the MiminalCD and boot into the installation you WILL NOT get a prompt or login when the bootup completes. Pressing ALT + F1 will take you to the prompt so you can login. Once you've completed the MATE install you will go directly to the Login GUI when you boot up.

Now I'll start experimenting with what I have and don't have and with what works and what doesn't. :)

---

### Post by Trapper on 2012-02-14
> **snowpine said:**
> VirtualBox would be ideal for this kind of experimentation. You  can use its Snapshot feature to roll back to a certain point in time.

Yeah, I do think it's time for me to figure out and start using virtualbox and quit doing things the archaic way.

Thanks for your help and your suggestions.

---

### Post by varunpr97 on 2012-02-15
> **Trapper said:**
> Here's the process I just used to successfully integrate MATE into a fresh MinimalCD installation that was done through the command line option of the installer. This complete MATE install is quite "barebones" but that was my aim and it's the box I am on now. Here are the steps I took:

```


sudo nano /etc/apt/sources.list

Add this repository:

deb http://tridex.net/repo/ubuntu oneiric main

sudo apt-get update

sudo apt-get install mate-archive-keyring

sudo apt-get update

sudo apt-get install xorg xterm gdm menu mate-core gksu firefox synaptic --no-install-recommends

sudo service gdm start


```Just a note ... After you install U1110 from the MiminalCD and boot into the installation you WILL NOT get a prompt or login when the bootup completes. Pressing ALT + F1 will take you to the prompt so you can login. Once you've completed the MATE install you will go directly to the Login GUI when you boot up.

Now I'll start experimenting with what I have and don't have and with what works and what doesn't. :)
What packages do we hav eto install to get lightdm as the default dm? and I have installed mate on my pc... it loads under guest session but when I load it under my username it doesnt boot... it did boot for the 1st time then hung...

---

### Post by cwklinuxguy on 2012-02-15
I have not been able to get my Minimal install to boot at all...it pretty much just sits there as a blank screen. Any help?

@varunpr97: What do you say we worry about trying the minimal CD later down the line, but for now focus on what I've already started (building on top of normal Ubuntu 11.10)? Also, do send me a message with your name/preferred pseudonym so I can post a message to the Paradise OS blog welcoming you to the development team! :D

---

### Post by Trapper on 2012-02-15
> **cwklinuxguy said:**
> I have not been able to get my Minimal install to boot at all...it pretty much just sits there as a blank screen. Any help?


Did you press ALT + F1 after the install boots up?

---

### Post by cwklinuxguy on 2012-02-15
> **Trapper said:**
> Did you press ALT + F1 after the install boots up?

No. Was I supposed to?

---

### Post by Trapper on 2012-02-15
> **cwklinuxguy said:**
> No. Was I supposed to?

Yes, that's why I inserted this in the bottom of my post concerning how I installed MATE.

> Just a note ... After you install U1110 from the MiminalCD and boot into  the installation you WILL NOT get a prompt or login when the bootup  completes. Pressing ALT + F1 will take you to the prompt so you can  login. Once you've completed the MATE install you will go directly to  the Login GUI when you boot up.

I experienced the same difficulty. After searching around I discovered it is expected behavior when installing 11.10 minimal. I'm not sure it's the same with previous versions.

---

### Post by Trapper on 2012-02-16
> **varunpr97 said:**
> What packages do we hav eto install to get lightdm as the default dm? and I have installed mate on my pc... it loads under guest session but when I load it under my username it doesnt boot... it did boot for the 1st time then hung...


I tried the routine I posted earlier but sustituted lightdm for gdm. When I booted to the gui I did not get a login screen. Instead I got mate's blue striped background but that was all ... just a background. No panels, no nothing. I don't know why yet but an working on it.

---

### Post by Trapper on 2012-02-16
> **Trapper said:**
> I tried the routine I posted earlier but substituted lightdm for gdm. When I booted to the gui I did not get a login screen.

I finally managed to get lightdm working properly. Apparently it doesn't install a greeter, by default.

I replaced gdm with the following in my apt-get command:

lightdm lightdm-greeter-example-gtk


Reminder. After you've installed lightdm don't forget to run:

sudo service lightdm start

To change the login window background color, put a logo in, etc. I edited:

/etc/lightdm/lightdm-gtk-greeter-ubuntu.conf

In my case I made the background a solid color:

background=#2C001E

You can have a background image instead:

background=/path/to/my/image.png

For a logo in the login box:

logo=/path/to/my/logo_image.png

---

### Post by cwklinuxguy on 2012-03-13
Thank you very much for the information on configuring Light DM! It's MUCH appreciated!! I was going to need to find that eventually.

[Here]("http://ubuntuforums.org/paradiseos.wordpress.com/2012/03/14/alpha-2-1-development-update/") is a development update for the Paradise OS project.

---

### Post by bodhi.zazen on 2012-03-14
If you are going to do anything half way decent, I highly advise you use the debian live scripts.

They are in the repos, automate much of the process, and will make a nicer, more polished iso.

See:

[http://manpages.ubuntu.com/manpages/precise/man7/live-build.7.html](http://manpages.ubuntu.com/manpages/precise/man7/live-build.7.html)

[http://live-manual.debian.net/manual-2.x/html/live-manual.en.html](http://live-manual.debian.net/manual-2.x/html/live-manual.en.html)

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

[http://askubuntu.com/questions/83617/can-i-build-a-ubuntu-iso-from-a-manifest](http://askubuntu.com/questions/83617/can-i-build-a-ubuntu-iso-from-a-manifest)

Aye, it is a bit of reading and a learning curve, but well worth the effort.

---

### Post by cwklinuxguy on 2012-03-14
^Hmm...might be something to look into later on, but I think I'll stay with Remastersys for the time being. I'll pursue the polish after I have a good, working concept.

When using the Perfectminimal script to install LXDE, is X11 taken care of for you, or do I need to manually do that?

---

### Post by cwklinuxguy on 2012-03-19
@Trapper: I used the Perfectminimal script to download and install Lubuntu on my system (which included LXDM or whatever the name of their display manager is). From there, I used the instructions you provided to install LightDM. It asked me what Display Manager I wanted to use, and I selected "Light DM". However, it doesn't look like the LightDM in Ubuntu 11.10...here's a screenshot. How do I change the look of LightDM to what it should be in an Ubuntu install?

The black box is to protect my privacy. It is not a malfunction in the login screen.

---

### Post by Trapper on 2012-03-20
> **cwklinuxguy said:**
> @Trapper: I used the Perfectminimal script to download and install Lubuntu on my system (which included LXDM or whatever the name of their display manager is). From there, I used the instructions you provided to install LightDM. It asked me what Display Manager I wanted to use, and I selected "Light DM". However, it doesn't look like the LightDM in Ubuntu 11.10...here's a screenshot. How do I change the look of LightDM to what it should be in an Ubuntu install?

The black box is to protect my privacy. It is not a malfunction in the login screen.

To disable guest session I added a allow-guest=false to my /etc/lightdm/lightdm.conf

[SeatDefaults]
user-session=mate-session
allow-guest=false


I did my background and logo customizations in /etc/lightdm/lightdm-gtk-greeter-ubuntu.conf

logo=/path/to/image

background=/path/to/image

 (or for background color use a color #)

background=#000000

---

### Post by flurospar on 2012-03-20
> **varunpr97 said:**
> I want to create a mate respin of ubuntu without unity 3d and unity 2d included as default? How do I go about things? 

See [relinux]("http://sourceforge.net/projects/re-linux/") to create respins of Ubuntu.

---

### Post by cwklinuxguy on 2012-03-22
^Thanks, I'm sticking with Remastersys for now, but someone suggested alternative methods, which I will look into down the road.

@Trapper: I'm not asking how to modify the color scheme and the like, but rather how to change the layout from the one posted above to the Ubuntu default, as [shown here]("http://i1-news.softpedia-static.com/images/extra/LINUX/large/ubuntu1110loginscreen-large_001.jpg").

---

### Post by cwklinuxguy on 2012-04-03
Here is my /etc/lightdm/lightdm-gtk-greeter-ubuntu.conf file. The shown background and theme don't exist, so I assume that may be part of my problem. I have no /etc/lightdm/lightdm.conf file, however I do have an /etc/lightdm/lightdm-gtk-greeter.conf file which seems to be the same as what is below, however the layout is not the default Ubuntu one, and I see no place to change it (see above screenshot from Post #31 for how it looks right now). Any help?

> 
#
# background = Background file to use, either an image path or a color (e.g. #772953)
# theme-name = GTK+ theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
# show-language-selector (true or false)
#
[greeter]
background=/usr/share/backgrounds/warty-final-ubuntu.png
theme-name=Ambiance
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-language-selector=false


---

### Post by Trapper on 2012-04-03
> **cwklinuxguy said:**
> Here is my /etc/lightdm/lightdm-gtk-greeter-ubuntu.conf file. The shown background and theme don't exist, so I assume that may be part of my problem. I have no /etc/lightdm/lightdm.conf file, however I do have an /etc/lightdm/lightdm-gtk-greeter.conf file which seems to be the same as what is below, however the layout is not the default Ubuntu one, and I see no place to change it (see above screenshot from Post #31 for how it looks right now). Any help?


Okay. Here is my edited /etc/lightdm/lightdm-gtk-greeter-ubuntu.conf. After I manually edit it I log out and back in for changes to take affect.

```

[greeter]
background=#000000
theme-name=Ambiance
logo=/usr/share/icons/lightdm/my-lightdm-logo.png
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-language-selector=false

```Here's my complete lightdm.conf. 

```

[SeatDefaults]
user-session=mate-session
allow-guest=false

```I "think" lightdm.conf was created when I ran:

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s mate-session
```I ran that just prior to starting lightdm service the first time after initial MATE installation. I manually inserted the "allow-guest=false" section to prevent guest login.

---

