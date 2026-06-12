---
title: "Help before i cry.... PLEASE."
date: 2011-03-04
forum: General Help
---

### Post by Nictra Savios on 2011-03-04
(To skip all the background info and go right to the problem, scroll down to the ><>< line that crosses the post )

Okay so i made a post here, no one helped. I went to the ubuntu irc, they muted me. I went to the linux mint forum, the banned me. I went to the mint chanel... banned.


All i want is some help and no one will give it to me, they all say "Re-install" Or "its not supported" and im gonna freak out and like cry. Nobody will help me at all.... What the hells wrong with this community.....

All i want is someone to help me fix this please.....


My problem is simple. I Removed Linux Mint 10 Gnome and installed Ubuntu 10.10

Kay? So i first got ubuntu on a flashdrive boot, then i got minto on one

I went into a mint live USB and got the package list via 
```
sudo dpkg --get-selections > /media/Shared/Switch/Mint/
```then I went into the Ubuntu live USB and did:
```
sudo dpkg --get-selections > /media//Shared/Switch/Ubuntu/
```Then used this website:

[http://jura.wi.mit.edu/bioc/tools/compare.php](http://jura.wi.mit.edu/bioc/tools/compare.php)

To get the packages that were in mint and not in Ubuntu.

Following ?

This is the list i got :

```
add-apt-key
aptitude
aptoncd
ca-certificates-java
cabextract
compiz-check
compizconfig-settings-manager
cowsay
cups-pdf
dcraw
deskbar-applet
esound-clients
esound-common
f-spot
fortune-mod
fortunes-husse
fortunes-min
gawk
gdebi
gdebi-core
gecko-mediaplayer
gimp
gimp-data
giver
gnome-colors-common
gnome-mplayer
gnome-wise-icon-theme
grub2-theme-mint
gsfonts-x11
gstreamer0.10-esd
gstreamer0.10-ffmpeg
gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gtk2-engines-aurora
gtk2-engines-candido
gufw
gvfs-bin
hardinfo
hddtemp
imagemagick
inxi
java-common
liba52-0.7.4
libaccess-bridge-java
libaccess-bridge-java-jni
libass4
libaudio2
libaudiofile0
libavahi1.0-cil
libavcodec52
libavformat52
libavutil50
libbabl-0.0-0
libboost-iostreams1.42.0
libcdaudio1
libcddb2
libcdt4
libcelt0-0
libclass-accessor-perl
libcwidget3
libdc1394-22
libdca0
libdirac-encoder0
libdirectfb-1.2-9
libdiscid0
libdvbpsi6
libdvdcss2
libdvdnav4
libdvdread4
libebml2
libenca0
libesd0
libfaac0
libfaad2
libfftw3-3
libflickrnet2.2-cil
libflite1
libgconfmm-2.6-1c2
libgdiplus
libgegl-0.0-0
libgif4
libgimp2.0
libglademm-2.4-1c2a
libglew1.5
libgme0
libgnome-keyring1.0-cil
libgraph4
libgsm1
libgvc5
libhal1
libhsqldb-java
libid3tag0
libilmbase6
libio-string-perl
libiptcdata0
libiso9660-7
libkate1
liblzo2-2
libmad0
libmagickcore3-extra
libmatroska2
libmimic0
libmjpegtools-1.9
libmms0
libmng1
libmodplug1
libmono-data-tds2.0-cil
libmono-messaging2.0-cil
libmono-simd2.0-cil
libmono-sqlite2.0-cil
libmono-system-data2.0-cil
libmono-system-messaging2.0-cil
libmono-system-web2.0-cil
libmono-wcf3.0-cil
libmono2.0-cil
libmp3lame0
libmpcdec6
libmpeg2-4
libmusicbrainz3-6
libnetpbm10
libnotify-bin
libnotify0.4-cil
libofa0
liboil0.3
libopenal1
libopencore-amrnb0
libopencore-amrwb0
libopenexr6
libopenspc0
libparse-debianchangelog-perl
libpathplan4
libpostproc51
libqt4-dbus
libqt4-xml
libqtcore4
libqtgui4
libquicktime1
librecode0
librtmp0
libschroedinger-1.0-0
libsdl-image1.2
libservlet2.5-java
libsexy2
libsidplay1
libsoundtouch1c2
libsqlite0
libsub-name-perl
libsvga1
libswscale0
libtar
libts-0.0-0
libtwolame0
libunshield0
libupnp3
libva-x11-1
libva1
libvcdinfo0
libvdpau1
libvlc5
libvlccore4
libvpx0
libwildmidi0
libx264-98
libxcb-keysyms1
libxcb-randr0
libxcb-xv0
libxdot4
libxvidcore4
libzbar0
linuxmint-keyring
lupin-support
medibuntu-keyring
menu
mesa-utils
mint-artwork-common
mint-artwork-gnome
mint-backgrounds-helena
mint-backgrounds-isadora
mint-backgrounds-julia
mint-common
mint-elementary-icons
mint-flashplugin
mint-info-main
mint-local-repository
mint-meta-codecs
mint-meta-gnome
mint-meta-gnome-dvd
mint-meta-main
mint-search-addon
mint-stylish-addon
mint-translations
mint-x-icons
mint-x-theme
mintbackup
mintdesktop
mintinstall
mintinstall-icons
mintmenu
mintnanny
mintsystem
mintupdate
mintupload
mintwelcome
mintwifi
mplayer
nautilus-actions
nautilus-gksu
nautilus-open-terminal
nautilus-wallpaper
ndisgtk
ndiswrapper-common
ndiswrapper-utils-1.9
netpbm
odbcinst
odbcinst1debian2
openoffice.org-base
openoffice.org-java-common
openoffice.org-style-tango
p7zip
padevchooser
paman
paprefs
pavucontrol
pavumeter
pidgin
pidgin-data
pidgin-facebookchat
pidgin-libnotify
pppoe
pulseaudio-module-zeroconf
python-compizconfig
python-gnomedesktop
python-paramiko
python-sexy
samba
shiki-colors-metacity-theme
shiki-wise-theme
simple-ccsm
startupmanager
sun-java6-bin
sun-java6-jre
sun-java6-plugin
thunderbird
tsconf
ttf-dejavu
ttf-dejavu-extra
ttf-droid
tzdata-java
ubiquity-slideshow-mint
ubuntu-system-adjustments
unixodbc
unrar
unshield
vlc
vlc-data
vlc-nox
vlc-plugin-notify
vlc-plugin-pulse
w32codecs
xchat
xchat-common

```I then took that in g-edit,  went through it to get rid of a few things, then
Cntl + A (select all) and then TAB (putting a tab ( \t ) infront of them all)
i then hit Cntl + H to open up the replace ment and put in

Find: \n\t 
# (\n is a new line)
Replace with: 
# <a space, a single space>

Then every 3 lines i madea new line, breaking the list into 20 or so packages a peice.

then selected them all, predded tab, making a tab before each block. 

Then ran

Find: \t
Replace with: sudo apt-get -yf install 


And then put at the top #!/bin/bash , maked it executable

Ran it overnight and tada, got all mah extras.

in the morning i ran
```

sudo apt-get -s ubuntustudio*
```And got a few things from that list
ubuntustudio-graphics , video, few other things, blah blah

In the end i had 3 problems:

1) Mintinstall,mint update,mint welcome etc. I un-installed them pretty easy with
```
sudo apt-get -fy purge( or remove, i forget which) mint*
```and
```
 sudo apt-get -fy install mint-menu mint-backup
```2) Splash screen was ubuntu studio's. , fixed that really easy :P i have my own custom splash so ... done.

and now the big one.... Then one nobody will help me fix .......


[CENTER][SIZE=2][I][U][B] ><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><


[/B][/U][/I][/SIZE][LEFT]
When anything tries to idenfity my OS, like grub or the bootscript available on this forums for diagnosing boot problems... **It says its Linux Mint 10 Fluxbox **[SIZE=2][U][I][B]WHEN I AM RUNNING UBUNTU 10.10 ....!!!!

[/B][/I][/U][/SIZE][LEFT]I need help on that! please ive tried everything short of a reinstall. Its a system file. But i dont know what one, and is their a package off the ubuntu repo's that will fix this like uh... ubuntu-main-system-info ? (tried that alredy) 

Please help faaassssttt!
[/LEFT]
[/LEFT]
[/CENTER]

---

### Post by wiggly81 on 2011-03-04
seriously this is 2 posts on here about the same problem, if the title on the grub boot loader is that imprtant to you then change it manually
```
gksudo gedit /boot/grub/grub.cfg
```
look for the line that says linux mint and change it to "im gonna cry" or whatever you like, when you reboot it will say whatever ya changed it too

---

### Post by Nictra Savios on 2011-03-04
> **wiggly81 said:**
> seriously this is 2 posts on here about the same problem, if the title on the grub boot loader is that imprtant to you then change it manually
```
gksudo gedit /boot/grub/grub.cfg
```look for the line that says linux mint and change it to "im gonna cry" or whatever you like, when you reboot it will say whatever ya changed it too


BUT everything else STILL SAYS ITS MINT. when its not. Thats a major annoyance and will lead to problems i bet.

Stop giving me work arounds and help fix the problem, if you dont know , then dont give me BS.....

---

### Post by wiggly81 on 2011-03-04
wow ya a real nice person huh!

---

### Post by Nictra Savios on 2011-03-04
> **wiggly81 said:**
> wow ya a real nice person huh!


Well ive been up all night digging through the file system, and when i cant get it solved, i get sarcasm and everyones saying go away, we cant help you and all i want is one person to tell me one package and nobody will and im gonna cry.

---

### Post by CharlesA on 2011-03-04
You don't edit /boot/grub/grub.cfg. It even has a line that says "do not edit this file"

See here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
and
here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Nictra Savios on 2011-03-04
> **CharlesA said:**
> You don't edit /boot/grub/grub.cfg. It even has a line that says "do not edit this file"

See here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
and
here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Thats not my problem ;( i just want help.... who cares about the nitpicky, help my problem, dont correct someone else.....

---

### Post by mikewhatever on 2011-03-04
... and what does it matter if the authentication says Mint or Ubuntu?

Edit: I guess installing most of Mint's packages makes it Mint, don't you think?

> **Nictra Savios said:**
> Thats not my problem ;( i just want help.... who cares about the nitpicky, help my problem, dont correct someone else.....

That kind of explains why you got banned.

---

### Post by CharlesA on 2011-03-04
> **Nictra Savios said:**
> Thats not my problem ;( i just want help.... who cares about the nitpicky, help my problem, dont correct someone else.....
You aren't going to get help with an attitude like that.

If the title in Grub is the problem (and it looks like it is), just edit the title by following the instructions in the linked pages.

---

### Post by wiggly81 on 2011-03-04
> **CharlesA said:**
> You don't edit /boot/grub/grub.cfg. It even has a line that says "do not edit this file"

i am aware of this but i have changed the titles in the grub.cfg in the past with no problems and they displayed in grub in the way i wanted them too..
however i agree it is not best practice, but it is also not best practice to slam down any offer of help when you ask for help on a form / chat network

---

### Post by Dngrsone on 2011-03-04
> **Nictra Savios said:**
> Thats not my problem ;( i just want help.... who cares about the nitpicky, help my problem, dont correct someone else.....

... and yours is not *our* problem.

I can see why you've been ignored and banned elsewhere.

For all the work you are doing, the easiest and simplest solution would be to nuke the drive and reinstall.  I realize you've heard that before and don't want to hear it, but there you are; simple solution.

Have you tried doing a grep search through the drive for the term 'mint'?

---

### Post by CharlesA on 2011-03-04
> **wiggly81 said:**
> i am aware of this but i have changed the titles in the grub.cfg in the past with no problems and they displayed in grub in the way i wanted them too..
however i agree it is not best practice, but it is also not best practice to slam down any offer of help when you ask for help on a form / chat network

Ah gotcha. Thanks for the info. :)

---

### Post by Dans564 on 2011-03-04
i hope he cries... he is mean...
no but really just reinstall, im not sure what u have done, but it has messed something up.  On the other hand, is ur problem really that bad?  Is it effecting the usability at all?  My guess is no.

---

### Post by mmsmc on 2011-03-04
if some thing says mint but is really a ubuntu program, it should not cause any problems in the future, i know a reinstall is not the most favored option, but if you are getting frustrated with this, starting from th beginning can really help, and if you want we can always walk you through the installation process to make it easier and faster and just in case another problem arises. remember, things can be worst, a dwarf warrior could brake down your door and steel your computer

---

### Post by AldenIsZen on 2011-03-06
So, basically you got rid of Linux Mint, and instead installed Ubuntu. But you missed Mint, and wanted Ubuntu Studio's packages, and also installed Linux Mint's packages that Ubuntu didn't have. While I, nor anyone else can quite understand why you would do this, unless you can't install Ubuntu Studio's packages, one thing to consider (if I have it right) is that you may be going about this the wrong way somehow. Perhaps it may in fact be easier to install Ubuntu Studio's packages.

Anyhow, what the others have not so gracefully tried to tell you is that you can't just expect people to help you. They are busy with their own things, and they may not know the answer to you problem. I mean, you do this complicated thing and expect everyone else to sort it out for you when you don't know what you are doing. If you did, you could fix it.

It sounds to me like you have some other issues in your life, and are a bit of a perfectionist, as your tendencies remind me of myself when I was younger. I pray you get them sorted out. Remember, you catch way more flies with honey...

Another thing, just say you diff'd the packages between Ubuntu and Mint, installed them on Ubuntu, installed Ubuntu Studio, and you now have Mint mentioned in grub and boot.cfg. The list of packages may have been helpful, but all the rest was way too much storytelling, when anyone who knows what you are doing knows all of that I bet.

And one more, you are installing Linux Mint packages, and they seem to be the issue, yet expecting help from Ubuntu. Ubuntu people are not familiar with Mint's packages and what they do, in general. They may be able to assist, but you are not acting very mature, and expecting help "FAST". Be patient. Take your time, come back to it if you have to, but getting ready to cry over almost anything means you need to learn to let go somewhere. I wish you the best, and good luck.

---

### Post by NertSkull on 2011-03-06
> **mmsmc said:**
> remember, things can be worst, a dwarf warrior could brake down your door and steel your computer

awesome

---

### Post by MARP1961 on 2011-03-06
AldenIsZen is far too polite!

---

### Post by mmsmc on 2011-03-06
yeah, i think that nictra left, maybe he was ab;e to solve it, or maybe the dwarf took the computer, nobody will ever know!

---

### Post by Timmer1240 on 2011-03-06
Ive lost whole a drive full of music movies games ect due to hard drive failure and I never cried this is not life and death here!I wasnt happy but what can you do!But now I got a 500 gig backup drive!

---

### Post by papaapa on 2011-03-06
Allright everybody take a deep breath -- hold it -- let it out -- slowly.

If you have spent hours on a problem and been made cranky and irritable raise your hand. (counts hands - Ahem it's unanimous.)

We don't fix people here we fix computers. Now smile and type 
(smiles come through and are translated clearly in text.)

---

### Post by mmsmc on 2011-03-06
ha, only REAL computer geeks can fix a problem immediately! :)

---

### Post by davidmohammed on 2011-03-06
to be honest - the OP would have been better advised just to backup his /home directory - install ubuntu studio from fresh and replace /home from his backup.

---

### Post by AldenIsZen on 2011-03-07
> **MARP1961 said:**
> AldenIsZen is far too polite!
There are but two powers that matter in life. Love, and hate. Love is the only power that can conquer hate, and hate only begets more hate. I don't believe in such a thing as too polite, as that would only be sarcasm. This person was obviously frustrated, and as I mentioned had something in life making him act that way. It can be difficult dealing with people like that, but if we don't, who will help us when we are in that type of need?

> [FONT=arial, sans-serif]We  engrave upon everyone our image with all action taken and words spoken,  and turn them into molds that shape others, just as they have done to  us. - [COLOR=#222222]Villein[/COLOR][/FONT]

---

