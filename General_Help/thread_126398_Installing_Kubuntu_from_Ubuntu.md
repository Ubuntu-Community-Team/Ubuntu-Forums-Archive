---
title: "Installing Kubuntu from Ubuntu"
date: 2006-02-06
forum: General Help
---

### Post by MJoshi on 2006-02-06
I tried to follow the instructions from the Kubuntu website however, I still cannot seem to be able to install Kubuntu from Ubuntu.

At the terminal prompt, I typed:

```
sudo synaptic kubuntu-desktop
```

It brings up the package manager however, I cannot find Kubuntu listed?

---

### Post by el3ktro on 2006-02-06
You're wrong here. Either, start the Synaptic Package Manager from the Gnome menu, there, you can search for "kubunu-desktop" & install it

OR

go the the terminal and type "sudo apt-get install kubuntu-desktop"

this will install all Kubuntu related stuff in the terminal window. Which of the two you choose is up to you.


Tom

---

### Post by MJoshi on 2006-02-06
I could not find kubuntu-desktop in the Synaptic Package Manager?

---

### Post by aysiu on 2006-02-06
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by MJoshi on 2006-02-06
Here is the output from that command:

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

---

### Post by aysiu on 2006-02-06
A **#** sign is what's called a *comment*.
It basically tells Ubuntu, "Disregard the entire line after this symbol."

So Ubuntu sees the first line of your sources.list file, and then it sees **nothing else**.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

Comment out (put a # sign in front of) the first source (the CD-ROM) and then remove the # sign from all of the things that look like web addresses.

Then save.

```
sudo apt-get update
sudo apt-get install kubuntu-desktop
``` Log out. Click **Session > KDE**. Log back in.

P.S. Can I ask how you got that sources.list?

---

### Post by MartinG on 2006-02-06
Try```
sudo apt-get install kubuntu-desktop
```Whoops, my browser didn't refresh so I missed all you other helpful people's posts!

---

### Post by MJoshi on 2006-02-06
Thanks for that *aysiu* - I was able to proceed with the KDE install after doing what you mentioned.

Just before the installation finished, it said that there were multiple login environments installed and which one I wanted to use?

The options were:

GDM
KDM

I chose KDM?

When I restarted the computer, the login prompt was for KUbuntu however, the desktop and applications still look like GNOME?

I'm not sure what you meant by > Can I ask how you got that sources.list? as I just installed Ubuntu from the original C.D with no modifications?

---

### Post by cblanquer on 2006-02-06
Just choose the one you are going to use more often:
[LIST]
[*]kdm if you expect to use more often Kubuntu (KDE)
[*]gdm if you expect to use more often Ubuntu (Gnome)
[/LIST] 
In both cases you can select which is the desktop you want to access, check one of the buttons low in the screen under the space you type your userid to login.

The difference is that from Ubuntu you can directly switch off when login off if you are starting with gdm; the same applies for the couple Kubuntu and kdm.
Instead if you log off from Ubuntu to kdm you still have to confirm once again and the same applies fo r the combination Kubuntu and gdm.

I hope that helps.

---

### Post by MJoshi on 2006-02-09
Thanks *cblanquer* - I have now worked out how to login to KDE.  I didn't realise that the option is still available to revert back to a GNOME interface.

Unfortunately, the problem that I was experiencing with no sound on GNOME is still present?

See the following thread for further details:

[http://ubuntuforums.org/showthread.php?t=123492](http://ubuntuforums.org/showthread.php?t=123492)

---

### Post by flight_master on 2006-02-09
Can you hear sound generated by KDE? I.E. the logon sound, or the sound-effects from programs? Also, what are your current settings under System Settings -> Sound System ?

Regards,
Christian

---

### Post by MJoshi on 2006-02-09
The current setting under System Settings -> Sound System is 'Autodetect'.

---

### Post by flight_master on 2006-02-09
Under "Hardware" Set it to use Advanced Linux Sound Architecture., hit apply, then go back to the "General" tab, and hit Test Sound. It should work for you ;)

-Christian

---

### Post by MJoshi on 2006-02-14
Unfortunately, that still gives me the same error as before?

---

### Post by 5lack3r on 2006-04-25
so i tried aptget install kubuntudesktop and this is what i get.

sudo apt-get install kubuntu-desktop
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done
slacker@server:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: adept but it is not going to be installed
                   Depends: akode but it is not going to be installed
                   Depends: akregator but it is not going to be installed
                   Depends: amarok but it is not going to be installed
                   Depends: ark but it is not going to be installed
                   Depends: arts but it is not going to be installed
                   Depends: gtk2-engines-gtk-qt but it is not going to be installed
                   Depends: gwenview but it is not going to be installed
                   Depends: hplip-base but it is not going to be installed
                   Depends: ivman but it is not going to be installed
                   Depends: k3b but it is not going to be installed
                   Depends: kaffeine-gstreamer but it is not going to be installed
                   Depends: kamera but it is not going to be installed
                   Depends: karm but it is not going to be installed
                   Depends: katapult but it is not going to be installed
                   Depends: kate but it is not going to be installed
                   Depends: kaudiocreator but it is not going to be installed
                   Depends: kcontrol but it is not going to be installed
                   Depends: kcron but it is not going to be installed
                   Depends: kde-guidance but it is not going to be installed
                   Depends: kde-systemsettings but it is not going to be installed
                   Depends: kdeadmin-kfile-plugins but it is not going to be installed
                   Depends: kdebase-kio-plugins but it is not going to be installed
                   Depends: kdebluetooth but it is not going to be installed
                   Depends: kdegraphics-kfile-plugins but it is not going to be installed
                   Depends: kdemultimedia-kappfinder-data but it is not going to be installed
                   Depends: kdemultimedia-kfile-plugins but it is not going to be installed
                   Depends: kdemultimedia-kio-plugins but it is not going to be installed
                   Depends: kdenetwork-filesharing but it is not going to be installed
                   Depends: kdenetwork-kfile-plugins but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Depends: kdepim-wizards but it is not going to be installed
                   Depends: kdeprint but it is not going to be installed
                   Depends: kdesktop but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: kfind but it is not going to be installed
                   Depends: kghostview but it is not going to be installed
                   Depends: khelpcenter but it is not going to be installed
                   Depends: kicker but it is not going to be installed
                   Depends: kio-apt but it is not going to be installed
                   Depends: kio-locate but it is not going to be installed
                   Depends: klaptopdaemon but it is not going to be installed
                   Depends: klipper but it is not going to be installed
                   Depends: kmail but it is not going to be installed
                   Depends: kmenuedit but it is not going to be installed
                   Depends: kmilo but it is not going to be installed
                   Depends: kmix but it is not going to be installed
                   Depends: knetworkconf but it is not going to be installed
                   Depends: konq-plugins but it is not going to be installed
                   Depends: konqueror but it is not going to be installed
                   Depends: konqueror-nsplugins but it is not going to be installed
                   Depends: konserve but it is not going to be installed
                   Depends: konsole but it is not going to be installed
                   Depends: kontact but it is not going to be installed
                   Depends: konversation but it is not going to be installed
                   Depends: kooka but it is not going to be installed
                   Depends: kopete but it is not going to be installed
                   Depends: kpdf but it is not going to be installed
                   Depends: kpf but it is not going to be installed
                   Depends: kppp but it is not going to be installed
                   Depends: krdc but it is not going to be installed
                   Depends: krfb but it is not going to be installed
                   Depends: krita but it is not going to be installed
                   Depends: kscd but it is not going to be installed
                   Depends: kscreensaver but it is not going to be installed
                   Depends: ksmserver but it is not going to be installed
                   Depends: ksnapshot but it is not going to be installed
                   Depends: ksplash but it is not going to be installed
                   Depends: ksvg but it is not going to be installed
                   Depends: ksysguard but it is not going to be installed
                   Depends: ksystemlog but it is not going to be installed
                   Depends: kubuntu-default-settings but it is not going to be installed
                   Depends: kubuntu-docs but it is not going to be installed
                   Depends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Depends: kuser but it is not going to be installed
                   Depends: kwalletmanager but it is not going to be installed
                   Depends: kwifimanager but it is not going to be installed
                   Depends: kwin but it is not going to be installed
                   Depends: openoffice.org2-kde but it is not going to be installed
E: Broken packages
slacker@server:~$

how do i fix this?

---

### Post by gingermark on 2006-04-25
Again, post the contents of your sources.list file located in /etc/apt.

I suspect you've also got the majority of your repositories commented out.

---

### Post by jis on 2006-05-18
[QUOTE=cblanquer]Just choose the one you are going to use more often:
[LIST]
[*]kdm if you expect to use more often Kubuntu (KDE)
[*]gdm if you expect to use more often Ubuntu (Gnome)
[/LIST] 
In both cases you can select which is the desktop you want to access, check one of the buttons low in the screen under the space you type your userid to login.

The difference is that from Ubuntu you can directly switch off when login off if you are starting with gdm; the same applies for the couple Kubuntu and kdm.
Instead if you log off from Ubuntu to kdm you still have to confirm once again and the same applies fo r the combination Kubuntu and gdm.

I hope that helps.[/QUOTE]

Can I change the kdm/gdm setting later? (I do not know yet, which I will use more often in the future.) Do you mean switching computer power off or what by "switch off"?

---

