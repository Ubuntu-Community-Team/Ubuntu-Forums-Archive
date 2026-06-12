---
title: "Xubuntu shortcomings..."
date: 2012-01-15
forum: General Help
---

### Post by HDave on 2012-01-15
I've recently set up Xubuntu virtual machine to get a workable Unity-free environment.  After having used if for a few hours, I have to say that I find it to be excellent.

I guess, before I make the big switch, I am wondering are there any common pitfalls or problems I am likely to run into?  I've been using Gnome for 3 years, running the following apps:

Java (Sun Hotspot)
Eclipse / Maven
Bibble
Firefox w/ Flash
Thunderbird
Chrome w/ Flash
VirtualBox
SMB Client
GEdit
Terminal
Google Earth
Compiz
VLC
Rythymbox
External Monitor (nvidia-settings)
Dropbox
Skype
LibreOffice
Stellarium
Nexuiz
XSane

Any recent Xubuntu converts run into problems with this stack?

---

### Post by mike555 on 2012-01-15
I think you will like Xubuntu, a couple of things , do a "clean" install and don't use old /home from ubuntu ....... you will want transparent background behind desktop icons text .. easy fix .... get Thunar extras , they really help ........ be careful not to install kde apps ,  turn off "recommends" in package manager and software center , (actually I recommend not using software center because it doesn't tell you what it's installing) ... use synaptic package manager that way you can decide if you want to load on a bunch of stuff .....

---

### Post by Toz on 2012-01-15
Also, install gvfs-backends so that you can access your smb (cifs) shares though Thunar.

---

### Post by HDave on 2012-01-15
> **mike555 said:**
> I think you will like Xubuntu, a couple of things , do a "clean" install and don't use old /home from ubuntu ....... you will want transparent background behind desktop icons text .. easy fix .... get Thunar extras , they really help ........ be careful not to install kde apps ,  turn off "recommends" in package manager and software center , (actually I recommend not using software center because it doesn't tell you what it's installing) ... use synaptic package manager that way you can decide if you want to load on a bunch of stuff .....

Good stuff...thanks.  Should have added Synaptic to my list up above...its a life saver.

---

### Post by HDave on 2012-01-15
> **Toz said:**
> Also, install gvfs-backends so that you can access your smb (cifs) shares though Thunar.

Will do.  Assuming here that Thunar is the Nautilus of Xfce?

---

### Post by BlinkinCat on 2012-01-15
> **HDave said:**
> Will do.  Assuming here that Thunar is the Nautilus of Xfce?


Yes it is - :)

---

### Post by electrojustin on 2012-01-15
I wouldn't try running nautilus if that's something you may ever plan to do. It tends to reset the desktop to what it would look like if you had gnome or unity. Also, I've never gotten Compiz to work correctly...The default compositor is nice enough though.

---

### Post by HDave on 2012-01-15
Turns out Thunar was already installed by default, as was Synaptic.

The thing rocks...though I'm still bracing for disappointment!

---

### Post by HDave on 2012-01-15
> **electrojustin said:**
> I wouldn't try running nautilus if that's something you may ever plan to do. It tends to reset the desktop to what it would look like if you had gnome or unity. Also, I've never gotten Compiz to work correctly...The default compositor is nice enough though.

Really not missing nautilus at all at this point.  Frankly, its been one day and I'm having difficulty trying to recall anything from the Gnome desktop I ever cared about that isn't already in Xubuntu.

My only complaint is that the panel cpu/memory/network graph is very narrow.

---

### Post by Guitar John on 2012-01-15
> **HDave said:**
>   ...I've been using Gnome for 3 years, running the following apps:

Java (Sun Hotspot)
Eclipse / Maven
Bibble
Firefox w/ Flash
Thunderbird
Chrome w/ Flash
VirtualBox
SMB Client
GEdit
Terminal
Google Earth
Compiz
VLC
Rythymbox
External Monitor (nvidia-settings)
Dropbox
Skype
LibreOffice
Stellarium
Nexuiz
XSane

Any recent Xubuntu converts run into problems with this stack?

The text editor in Xubuntu (leafpad) has less features than Gedit, like no spell-check.

Rythmbox is no longer being developed.  The Xubuntu default music player is called gmusicbrowser, which takes some getting used to.  You will need a separate program to rip cd's.  I use Asunder.

Not sure, but I think I read somewhere that there is an issue with Bluetooth in Xubuntu.

None of these are huge problems, just things to consider.

---

### Post by HDave on 2012-01-15
> **Guitar John said:**
> The text editor in Xubuntu (leafpad) has less features than Gedit, like no spell-check.

Rythmbox is no longer being developed.  The Xubuntu default music player is called gmusicbrowser, which takes some getting used to.  You will need a separate program to rip cd's.  I use Asunder.

Not sure, but I think I read somewhere that there is an issue with Bluetooth in Xubuntu.

None of these are huge problems, just things to consider.

Very helpful...thanks.  Yes -- I forgot about Brasero...that one always worked very well.  Also forgot to add nixnote and handbrake to the list, but neither of those is Gnome anyway.

This desktop runs so fast...I feel like an idiot for not having switched 2 years ago...but 10.04 was so awesome...  sigh.

---

### Post by Maximus559 on 2012-01-15
To the OP - you and I seem to be in the same boat. I just recently upgraded from Ubuntu 10.04 to Xubuntu 11.10 and I'm loving it. Xfce is perceptibly snappier than Gnome 2.x on my aging PC.

One thing I've noticed is that there seems to be a problem with theme integration on Xubuntu. The only pre-installed theme that integrates nicely with everything is the default, greybird. I think this has to do with greybird being a GTK 3 theme. It seems that all the other themes that are installed by default are GTK 2 themes, and thus have problems integrating with some applications (gcalctool and gedit are two examples). Not a big deal, though.

---

### Post by cottfcfan on 2012-01-16
HDAVE...
I've done the same as you.
There were a few issues I hit initially, Truecrypt being one, but nothing I haven't been able to work round.
I keep having spells with unity & gnome shell, but keep coming back to Xubuntu. Excellent, polished distro.
With ref. to the theming issue from the last poster, add the webupd8 themes ppa from here:
[http://www.webupd8.org/2011/10/4-beautiful-gnome-32-compatible-gtk.html](http://www.webupd8.org/2011/10/4-beautiful-gnome-32-compatible-gtk.html)
All work well & integrate well with Xubuntu.

---

### Post by HDave on 2012-01-16
> **cottfcfan said:**
> HDAVE...
I've done the same as you.
There were a few issues I hit initially, Truecrypt being one, but nothing I haven't been able to work round.
I keep having spells with unity & gnome shell, but keep coming back to Xubuntu. Excellent, polished distro.
With ref. to the theming issue from the last poster, add the webupd8 themes ppa from here:
[http://www.webupd8.org/2011/10/4-beautiful-gnome-32-compatible-gtk.html](http://www.webupd8.org/2011/10/4-beautiful-gnome-32-compatible-gtk.html)
All work well & integrate well with Xubuntu.

I used to use Truecrypt all the time, but in 11.10 have switched over to the "Encrypt my home directory" home in the install.  I know it's not as secure as whole disk encryption and I am also sure the algorthm isn't as strong, but I just love the simplicity of it all.  Have you looked into it?

Thanks for the tip on the ppa...nice.

---

### Post by Hazzabin on 2012-01-16
ok guys, I'm not new to Ubuntu OS's, but am wanting to try this one

At my download site, I'm confused as to which os.......ie: alternate, list, metalink etc etc
my machine tends to run happier with "i386"

alternate v desktop   ????

any advise appreciated

Hazz

---

### Post by epic.mint on 2012-01-16
if you already have ubuntu installed just install the xfce desktop enviroment
```
sudo apt-get install xubuntu-desktop
```if you want this to be defualt for the startx command make a file called ".xinitrc" and write this in it
```
!# /bin/sh

exec ck-launch-session startxfce4
```this file should be stored in your home directory and be called "**.xinitrc**"

---

### Post by Hazzabin on 2012-01-16
Thanks Epic-mint

I'll give the desktop one a try out  :)

probably a half dummy question......by installing via 'apt-get' will I still be able to switch between the 2 different setups
as in from my version 10.10 and xubuntu without re-booting

I'm not as yet wanting to be the default

Hazz

---

### Post by epic.mint on 2012-01-17
you will still be able to switch between your DE's/window managers the from your login manager and if you don't like xfce you can simply uninstall it with 
```
sudo apt-get purge xubuntu-desktop
sudo apt-get autoremove
sudo apt-get autoclean
rm ~/.xinitrc
```this should remove xubuntu but you may have to remove abiword and such applications

---

### Post by Hazzabin on 2012-01-17
epic-mint, once again thanks you for your help

one day I'll get my head around all this stuff


Hazz

---

### Post by epic.mint on 2012-01-17
i myself have only been using ubuntu for about a year so i'm relatively new to it myself.
thing i have discovered that i now cant live without is 
1. starting another x-session with startx -- :1   (numbers range from 1-5 and you switch between sessions bith ctrl-alt-f1-12)
2. customizing my xsession with the ~/.xinitrc file 
3. installing different window managers/ desktop environments and using them in different xsessions.

hope this helps your ubuntu experience.

---

### Post by mastablasta on 2012-01-17
> **Hazzabin said:**
> Thanks Epic-mint
 
I'll give the desktop one a try out :)
 
probably a half dummy question......by installing via 'apt-get' will I still be able to switch between the 2 different setups
as in from my version 10.10 and xubuntu without re-booting
 
I'm not as yet wanting to be the default
 
Hazz
 
 
you switch desktop environments on login screen. 
 
getting back to pure gnome on Ubuntu 10.10 copy and paste the command you need:
[http://www.psychocats.net/ubuntu/puregnomemaverick](http://www.psychocats.net/ubuntu/puregnomemaverick)

---

### Post by Hazzabin on 2012-01-17
mastablasta, thanks for that info too

Hazz

---

### Post by HDave on 2012-01-17
> **epic.mint said:**
> if you already have ubuntu installed just install the xfce desktop enviroment
```
sudo apt-get install xubuntu-desktop
```if you want this to be defualt for the startx command make a file called ".xinitrc" and write this in it
```
!# /bin/sh

exec ck-launch-session startxfce4
```this file should be stored in your home directory and be called "**.xinitrc**"

Thanks for the info.  I am curious however, have you been running like this (switching between Gnome and Xfce) for a while?

I ask because the last time I got sick of Gnome, I installed kde-desktop and spend the next year fighting issues between KDE and Gnome where they each wanted control of certain .* system files, etc.

I really want to do this with xubuntu, but would like to hear from anyone who has both that it works well.

Edit:  For example, how does one use the xubuntu startup instead of gnome (GDM) ?

---

### Post by epic.mint on 2012-01-17
by xubuntu startup do you mean the login manager? i use KDM as a login manager i have however had no success opening a second session of KDM (on tty8+) and i'm stuck with only one running on tty7 another problem i have ist that i cant get more than one system tray working. you shouldn't need to use the XFCE login manager because you can choose a session in GDM before you login. 

when installing XFCE i got a popup asking me what login manager i would like to use as default but there is also a command to bring up this popup. i don't know what the command is however.

 i don't switch between gnome and xfce that much but i have never had any problems running more than one desktop environment for example i often run one kde/razor-qt session and one xfce session

i can post my .xinitrc script if you want to see it although it's it's a mess


sorry for my bad english im cursed to be swedish.

---

### Post by HDave on 2012-01-17
> **epic.mint said:**
> by xubuntu startup do you mean the login manager? i use KDM as a login manager i have however had no success opening a second session of KDM (on tty8+) and i'm stuck with only one running on tty7 another problem i have ist that i cant get more than one system tray working. you shouldn't need to use the XFCE login manager because you can choose a session in GDM before you login. 

when installing XFCE i got a popup asking me what login manager i would like to use as default but there is also a command to bring up this popup. i don't know what the command is however.

 i don't switch between gnome and xfce that much but i have never had any problems running more than one desktop environment for example i often run one kde/razor-qt session and one xfce session

i can post my .xinitrc script if you want to see it although it's it's a mess


sorry for my bad english im cursed to be swedish.

Got it -- thanks.  I just did the install and yes, GDM works just fine for logging into Xfce.  I did notice however, that I had a ton of startup programs and there was no menu settings choice to let me get rid of them.

I eventually found the command `xfce4-session-settings` and fixed it.  Why oh why can't we have multiple desktops installed without all these conflicts and hassle!

---

### Post by cottfcfan on 2012-01-17
To get rid of your unnecessary startup apps:
settings/settings manager/Session & Startup/Application Autostart.
Just untick the ones you don't want.

---

### Post by Hazzabin on 2012-01-17
HDave   "without all these conflicts and hassle!"  well said

I did run into huge problems with xbuntu installed with 11.10.

I'm kind of thinking a separate install on its own partition, on my machine at least, may work better.

Anyways I got some work that came in so distro hopping will have to wait a while for now.

Again thanks guys for your help

Hazz

---

### Post by HDave on 2012-01-17
> **cottfcfan said:**
> To get rid of your unnecessary startup apps:
settings/settings manager/Session & Startup/Application Autostart.
Just untick the ones you don't want.

It's official -- I'm blind!!

(Thanks)

---

### Post by HDave on 2012-01-17
> **mike555 said:**
> ... you will want transparent background behind desktop icons text .. easy fix .... get Thunar extras , they really help ...

Where does one get this?  Could not find it in synaptic...

---

### Post by HDave on 2012-01-17
BOOM!

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/212789](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/212789)

Anybody else on Xubuntu seeing this?

---

### Post by Toz on 2012-01-17
> **HDave said:**
> Where does one get this?  Could not find it in synaptic...

Create a file in your home directory called ~/.gtkrc-2.0:
```
leafpad ~/.gtkrc-2.0
```
...with the following contents:
```


#desktop icon transparency tweak
style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 0

    base[NORMAL] = "#000000"
    base[SELECTED] = "#000000"
    base[ACTIVE] = "#000000"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

```
Save the file and:
```
xfdesktop --reload
``` should enable it. If not, logout and back in again.

---

### Post by Toz on 2012-01-17
> **HDave said:**
> BOOM!

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/212789](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/212789)

Anybody else on Xubuntu seeing this?
Yup. Its not specific to xubuntu though.I'm seeing the same when resuming from suspend when cifs shares are mounted. Right now workaround is to:
```
fusermount -u ~/.gvfs
```
...prior to logout or suspend. Waiting for a fix.

---

### Post by buckyaustin on 2012-01-17
I have been using xubuntu for years... i have only found a few shortfalls, nothing major because these shortfalls are easily fixed because xubuntu can run kde and gnome software.... so if there is anything in gnome you like or kde just run it in xubuntu.... but remember some software will by default install kde and gnome desktops, so remember to check which desktop you are signing into.... 

I have gnome,xfce,kde and lxde..... and I always forget which one is the default as the default changes so rapidly.... so i have to log out to get the one i want... 

I hope more people are like you, instead of complaining about unity just switch desktop

---

### Post by HDave on 2012-01-17
> **Toz said:**
> Create a file in your home directory called ~/.gtkrc-2.0:
```
leafpad ~/.gtkrc-2.0
```
...with the following contents:

...
```



Perfection.  Thanks.

> **Toz said:**
> Yup. Its not specific to xubuntu though.I'm seeing the same when resuming from suspend when cifs shares are mounted. Right now workaround is to:
[code]fusermount -u ~/.gvfs
```
...prior to logout or suspend. Waiting for a fix.

Not a problem...thanks

> **buckyaustin said:**
> I have been using xubuntu for years... i have only found a few shortfalls, nothing major because these shortfalls are easily fixed because xubuntu can run kde and gnome software.... so if there is anything in gnome you like or kde just run it in xubuntu.... but remember some software will by default install kde and gnome desktops, so remember to check which desktop you are signing into.... 

I have gnome,xfce,kde and lxde..... and I always forget which one is the default as the default changes so rapidly.... so i have to log out to get the one i want... 

I hope more people are like you, instead of complaining about unity just switch desktop

I think Xubuntu is Canonical's best kept secret.  I've been waiting 3+ years for Gnome to fix the problem where desktop icons overlap and panel item position is messed up on screen resolution resize.  Both of these work flawlessly in Xfce, and I can tell it isn't an accident.

---

### Post by HDave on 2012-01-18
The text on my desktop icons is cut short and its hard for me tell which file is which without clicking on the icon.  Anyone have a quick fix that will get it to display more text?

---

### Post by vasa1 on 2012-01-18
> **mike555 said:**
> I think you will like Xubuntu, a couple of things , **do a "clean" install and don't use old /home from ubuntu** ....... you will want transparent background behind desktop icons text .. easy fix .... get Thunar extras , they really help ........ be careful not to install kde apps ,  turn off "recommends" in package manager and software center , (actually I recommend not using software center because it doesn't tell you what it's installing) ... use synaptic package manager that way you can decide if you want to load on a bunch of stuff .....

Dave, did you finally do a "clean" install as Mike suggested? I'm lurking here because I just might put Xubuntu on someone's old PC.

---

### Post by KBD47 on 2012-01-18
> **Guitar John said:**
> 

Rythmbox is no longer being developed.  The Xubuntu default music player is called gmusicbrowser, which takes some getting used to.  You will need a separate program to rip cd's.  I use Asunder.

Not sure, but I think I read somewhere that there is an issue with Bluetooth in Xubuntu.

None of these are huge problems, just things to consider.

Rhythmbox is going to be the chosen player in Ubuntu 12.04 and someone is still working on it:
[http://git.gnome.org/browse/rhythmbox](http://git.gnome.org/browse/rhythmbox)

---

### Post by KBD47 on 2012-01-18
It's funny, I have a hard time thinking of any shortcomings for Xubuntu where it is rather easy with other OS's. I'm using Xubuntu on my desktop right now and loving it. Also using Xfce installed onto Mint 12. I wish you well with Xubuntu. If it was 5 years LTS this Spring instead of just 3 years it would be just about perfect :-)
KBD47


Why I Like Xfce:
[http://kbd-thinkingoutloud.blogspot.com/2012/01/why-i-like-xfce.html](http://kbd-thinkingoutloud.blogspot.com/2012/01/why-i-like-xfce.html)

---

### Post by Toz on 2012-01-18
> **HDave said:**
> The text on my desktop icons is cut short and its hard for me tell which file is which without clicking on the icon.  Anyone have a quick fix that will get it to display more text?

Have a look here for possible xfdesktop customizations, including icon spacing, sizing, etc: [http://git.xfce.org/xfce/xfdesktop/tree/README]("http://git.xfce.org/xfce/xfdesktop/tree/README").

This code can also be put into the ~/.gtkrc-2.0 file.

---

### Post by cl17g on 2012-01-18
I have Ubuntu 11.10 and I installed Xfce4. I didn't have special problems, apart that I had to redefine the use of the "F10" key that was modified by the new desktop. I also found that I had to enable volume control in Gnome before having it working in Xfce (I don't know why). Once I solved those problems, everything has always been ok (so far, at least!).

I have just one question: is there any difference between installing Xubuntu directly and installing (as I did) Ubuntu and Xfce on top of it (if you are going to use only Xfce, I mean)? 

Thank you

---

### Post by HDave on 2012-01-18
> **vasa1 said:**
> Dave, did you finally do a "clean" install as Mike suggested? I'm lurking here because I just might put Xubuntu on someone's old PC.

I didn't.  I wanted to, but couldn't spare the hours this week so I did the install along size Gnome.  As usual, its a bit confusing as to what came from where...no question but that a clean install is the way to go.  Maybe in a couple weeks.

---

### Post by GraeW on 2012-01-18
I think XFCE has been doing things right for the users since way back in the 2.x and 3.x days - I remember tinkering with it back then. Along with everyone else, I recommend a clean install of Xubuntu if it is the only desktop environment you will ever use. Sometimes I do swap around if I hear of a new version of the others, but I seem to always come back to XFCE.
 
When 12.04 is official, I will probably do a clean install of Xubuntu and then maybe slide something else in later if I feel like tweaking.

---

### Post by HDave on 2012-01-18
> **GraeW said:**
> I think XFCE has been doing things right for the users since way back in the 2.x and 3.x days - I remember tinkering with it back then. Along with everyone else, I recommend a clean install of Xubuntu if it is the only desktop environment you will ever use. Sometimes I do swap around if I hear of a new version of the others, but I seem to always come back to XFCE.
 
When 12.04 is official, I will probably do a clean install of Xubuntu and then maybe slide something else in later if I feel like tweaking.

I agree 100%.  I am so used to the endless tweaks to Unity, the desperate searching through 50 replies on a launchpad bug, hoping for a work-around -- upgrading Ubuntu has become a white knuckle experience that always costs me several days.  

With Xubuntu...it was so easy it was almost anti-climactic!  I installed it and it Just Worked.  I was like "oh...so I guess I can just get to work."  I'm still geeking out about it...

---

### Post by KBD47 on 2012-01-18
Interestingly, I had Xubuntu 11.10 on my netbook, and am using Mint 12 with Xfce desktop installed right now, and the Xfce4 on top of Mint is running several degrees cooler on my netbook than Xubuntu ran on it. I'm guessing it would be the same case with Ubuntu 11.10 with Xfce4 installed on it. Could just be my particular hardware, but a nice side effect. I'm staying between 47-52c with Mint/Xfce4 compared to 54-57c with Xubuntu.
  Very easy to add Xfce4 from Synaptic Package Manager, just install the Meta package, then log out and log into Xfce. For precise instructions this is a great source:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
 just scroll down the page a bit. It gives instructions for installing the Xubuntu desktop onto Ubuntu.
KBD47

---

### Post by vasa1 on 2012-01-19
> **KBD47 said:**
> Interestingly, I had Xubuntu 11.10 on my netbook, and am using Mint 12 with Xfce desktop installed right now, and the Xfce4 on top of Mint is running several degrees cooler on my netbook than Xubuntu ran on it. I'm guessing it would be the same case with Ubuntu 11.10 with Xfce4 installed on it. ...

Interesting. I'm on Unity 3D, 11.10 and I have 44/50 as temperatures on my laptop. Anyways, this is about Xubuntu and not Mint.

---

### Post by cl17g on 2012-01-19
> **KBD47 said:**
> Interestingly, I had Xubuntu 11.10 on my netbook, and am using Mint 12 with Xfce desktop installed right now, and the Xfce4 on top of Mint is running several degrees cooler on my netbook than Xubuntu ran on it. I'm guessing it would be the same case with Ubuntu 11.10 with Xfce4 installed on it. Could just be my particular hardware, but a nice side effect. I'm staying between 47-52c with Mint/Xfce4 compared to 54-57c with Xubuntu.
  Very easy to add Xfce4 from Synaptic Package Manager, just install the Meta package, then log out and log into Xfce. For precise instructions this is a great source:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
 just scroll down the page a bit. It gives instructions for installing the Xubuntu desktop onto Ubuntu.
KBD47
So, you seem to suggest that the answer to my question "is there any difference between installing Xubuntu directly and installing (as I did) Ubuntu and Xfce on top of it?" is: better to install the full version and then install Xfce4, right? I thought this might be the answer because of better hardware optimization and the like, but I was not sure. Do you think this can be a valid reason to prefer this way to a fresh install of Xubuntu? Shouldn't they use the same kernel?

---

### Post by GraeW on 2012-01-19
AFAIK any single version number of Ubuntu (11.10, 11.04, etc) regardless of whether it is X,K,L or Ubuntu (or Myth, Studio, etc) will default to using the same kernel. The difference is what "extras" are loaded with the default because of Gnome/Unity, over a straight Xubuntu which does not require some/many of those background programs which otherwise get installed and started on boot up. I have not done a temperature check on my laptop so I couldn't begin to say which really runs cooler for me, but from what I do know about the installs in general, I would expect at least some differences because of the differing amounts of CPU usage by background programs.

---

### Post by KBD47 on 2012-01-19
> **cl17g said:**
> So, you seem to suggest that the answer to my question "is there any difference between installing Xubuntu directly and installing (as I did) Ubuntu and Xfce on top of it?" is: better to install the full version and then install Xfce4, right? I thought this might be the answer because of better hardware optimization and the like, but I was not sure. Do you think this can be a valid reason to prefer this way to a fresh install of Xubuntu? Shouldn't they use the same kernel?

I don't think you would go wrong either way. The temp difference could just be my particular hardware. You will have some extra programs if you install Xfce4 on top of Ubuntu. You could try both live cd or live usb to see if you have any noticeable difference. Since you already have Xfce installed on top of Ubuntu if it were me I'd just keep it that way. The only thing I can think you might run into is selecting which file manager to use, Xfce Thunar is what I use.
KBD47

---

### Post by drfox on 2012-01-22
I am aware of only 3 shortcomings in XFCE.
1. No thumbnails on the desktop
2. No change in the desktop icon when you click to open a link
3. No way to turn off the touchpad when you have a USB mouse plugged in.
Otherwise, XFCE is perfect and is currently my preferred DM for netbook, old laptop, and highend laptop.

Larry

BTW, if anyone has a workaround for any of the 3 shortcomings I've mentioned, I would appreciate hearing from you! Thanks.

---

### Post by KBD47 on 2012-01-22
#2 use the info at the link below to improve your desktop shortcuts, you then notice a difference in the icon when you click on it:

fix background text on xubuntu shortcuts
[http://xubuntu.wordpress.com/2007/08/27/howto-remove-the-borders-of-your-desktop-icon-text/](http://xubuntu.wordpress.com/2007/08/27/howto-remove-the-borders-of-your-desktop-icon-text/)

---

### Post by pbrane on 2012-01-22
> **drfox said:**
> ...

BTW, if anyone has a workaround for any of the 3 shortcomings I've mentioned, I would appreciate hearing from you! Thanks.

Check out this thread. [http://ubuntuforums.org/showthread.php?t=1912377]("http://ubuntuforums.org/showthread.php?t=1912377")

---

### Post by mikodo on 2012-01-23
> **mike555 said:**
> I think you will like Xubuntu, a couple of things , do a "clean" install and don't use old /home from ubuntu

I still use Ubuntu 10.04. I like bringing forward my /home partition in installs. What is the disadvantage of doing that, from Ubuntu 10.04 to Xubuntu 12.x?

Would it be better to use my backup of my ~/ and bring it forward to Xubuntu 12.x, by using my backup utility?

---

### Post by mike555 on 2012-01-23
It's good to have a backup of your /home folder, but you should not use it in a new install , it contains hidden conf. files that might mess up your new install....... just copy & paste files you need from the old /home to the new /home ........ like bookmarks, email addresses, documents, etc.

---

### Post by mikodo on 2012-01-23
> **mike555 said:**
> It's good to have a backup of your /home folder, but you should not use it in a new install , it contains hidden conf. files that might mess up your new install....... just copy & paste files you need from the old /home to the new /home ........ like bookmarks, email addresses, documents, etc.

Thank you for your advice. I will try to follow it when it comes to the clean install of Xubuntu. Maybe I'll cp my important data to a different partition before installation, and cp or mv it into the new install after. I have ~50 gigs of compressed music data, I don't want to loose. Doing it that way, seems safe and easy.

:)

---

### Post by HDave on 2012-01-23
> **mike555 said:**
> It's good to have a backup of your /home folder, but you should not use it in a new install , it contains hidden conf. files that might mess up your new install....... just copy & paste files you need from the old /home to the new /home ........ like bookmarks, email addresses, documents, etc.

I agree with this advice.  I also think that I should eat right and exercise....and I don't do that either.

I still have the same home directory with Xubuntu 11.10 that started with Ubuntu 9.10. Does it cause problems?  Yes, but usually small ones that can be quickly overcome...

---

### Post by neu5eeCh on 2012-01-23
> **drfox said:**
> I am aware of only 3 shortcomings in XFCE.
1. No thumbnails on the desktop...

I thought I read somewhere that Thunar would manage the desktop in 12.04 (meaning you will have thumbnails) but that change hasn't yet(?) been introduced in Xubuntu 12.04 Alpha.

---

### Post by neu5eeCh on 2012-01-23
[COLOR=Black]Beware[/COLOR] of [this bug]("https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/495361"). It struck me. It struck Jesse over at Distrowatch. It buzzed my wife just today and I just installed Xubuntu on a young woman's laptop (headed off to Egypt for the year) without warning her about it. I just fired off an E-Mail telling her what to do **when**, *not if*, it strikes.

Here are a couple of threads on the subject (just today):

[http://ubuntuforums.org/showthread.php?t=1874423](http://ubuntuforums.org/showthread.php?t=1874423)

and here:

[http://ubuntuforums.org/showthread.php?t=1846266](http://ubuntuforums.org/showthread.php?t=1846266)

Here's what I wrote in my E-Mail (bear in mind that this is for a complete Linux newbie):

> 

There is one bad bug in Xubuntu that I thought was fixed, but is not. So  it goes in Linux Land. 

This is important, so keep this E-Mail where you can retrieve it in case  this bug shows up on your little laptop, or you're going to be lost. 

First, two things. Do this ***now***: 

1.) And you only have to do this once: Rather than shut down your little  computer, log out. You will see a little check box asking if you want to  save the "session". Make sure this is ***unchecked***.  Log back in. 

2.) While it's running, go to: 

Ubuntu Logo --> Settings --> Settings Manager 

Then choose "Session and Startup". 

Choose the APPLICATION AUTOSTART TAB. At the bottom left of this window,  click Add. Under name type Window Manager. You can leave description  blank. Under "Command:" type "XFWM4" - without the quotes . Then click  OK and make sure it appears ***checked*** in your Application Autostart list. 

Second: 

If this isn't enough to prevent the bug, here's what it looks like and  what to do if it happens: 

You will start up your little laptop and none of your windows will have  "borders". You won't be able to do anything with them. You will be stuck  with whatever window popped up & your computer will be virtually useless. 

Try these remedies in this order: 

1.) Hit ALT-F2. If you can type in this window, type "XFWM4 --replace",  without quotes, and press enter. 

If you can't do that: 

2.) Right click with your mouse or touchpad anywhere on the ***desktop***,  ***not*** a program window, look for the desktop, choose OPEN TERMINAL HERE.  If you can open a terminal type, "XFWM4 --replace &" without quotes. 

If you can't do that: 

3.) Right click with your mouse or touchpad anywhere on the ***desktop***,  choose APPLICATIONS, then at the very bottom of that sub-menu, LOG OUT.  Once you have logged out, type CTRL-ALT-F1. Don't panic. You are in a  Virtual Terminal. That's a good thing. Enter your username and the  prompt, then your password. Next type the following: 

mv ~/.cache/sessions ~/.cache/sessions.bak 

And just to be darn sure: 

rm -rf ~/.cache/sessions 

To get out of the Virtual Terminal, type CRTL-ALT-F7. You should be  right back at your login screen. From there, you will be able to login  and everything will be normal. 

---

### Post by mr_pouit on 2012-01-29
> **drfox said:**
> I am aware of only 3 shortcomings in XFCE.
1. No thumbnails on the desktop
2. No change in the desktop icon when you click to open a link
3. No way to turn off the touchpad when you have a USB mouse plugged in.
Otherwise, XFCE is perfect and is currently my preferred DM for netbook, old laptop, and highend laptop.

Larry

BTW, if anyone has a workaround for any of the 3 shortcomings I've mentioned, I would appreciate hearing from you! Thanks.

FWIW, in the current xubuntu development release, xfdesktop has been patched to add support for thumbnails (hidden key to set in xfconf to enable them, e.g. with 'xfconf-query -c xfce4-desktop -p /desktop-icons/show-thumbnails -t bool -s true --create'), and single click (in Desktop Settings > Icons). Also, the improved mouse and touchpad settings' dialog has been backported from 4.9.x, and it should let you set some touchpad options (disable, tap-to-click, horizontal scrolling, etc.).

(Although that might be reverted before the final 12.04 release if it's too unstable…)

> **VTPoet said:**
> I thought I read somewhere that Thunar would manage the desktop in 12.04 (meaning you will have thumbnails) but that change hasn't yet(?) been introduced in Xubuntu 12.04 Alpha.

That was supposed to land in Xfce 4.10, but the schedule is still uncertain, and the main thunar developer is still busy with other things (so I wouldn't count on that to be part of Xubuntu 12.04).

---

