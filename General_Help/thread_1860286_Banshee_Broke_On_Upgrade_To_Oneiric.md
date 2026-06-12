---
title: "Banshee Broke On Upgrade To Oneiric"
date: 2011-10-14
forum: General Help
---

### Post by stevedude on 2011-10-14
Yesterday I upgraded from Ubuntu Natty 11.04 to Ubuntu Oneiric 11.10. Upon testing my applications, Banshee would not launch from the Unity launcher, or from Dash, or from terminal though it worked fine in Natty. I am currently running Oneiric 64-bit version.

Next I ran the Update Manager and noticed Banshee was listed to upgrade, but everything was "grayed-out" so I could not select it. I then went to Synaptic Manager and tried to select Banshee and mark it for an install, but I received a message similar to the one below.

I removed Banshee via the software center (The SC stated it was installed), logged-off/on then tried to add the Banshee PPA via terminal and install it. This is the message I receive:

"Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 banshee : Depends: libmtp9 but it is not going to be installed
E: Unable to correct problems, you have held broken packages." 

In Synaptic, I do not see anything listed as "Broken". The PPA I used was for Oneiric from Launchpad for Banshee ([https://launchpad.net/~banshee-team/+archive/ppa]("https://launchpad.net/%7Ebanshee-team/+archive/ppa"))

Also, in the Software Center to reinstall Banshee I receive the following error message: 
"The following packages have unmet dependencies:

banshee: Depends: libc6 (>= 2.7) but 2.13-20ubuntu5 is to be installed
         Depends: libglib2.0-0 (>= 2.29.92) but 2.30.0-0ubuntu4 is to be installed
         Depends: libgtk2.0-0 (>= 2.23.90) but 2.24.6-0ubuntu5 is to be installed
         Depends: libsoup-gnome2.4-1 (>= 2.27.4) but 2.36.0-0ubuntu1 is to be installed
         Depends: libsoup2.4-1 (>= 2.26.1) but 2.36.0-0ubuntu1 is to be installed
         Depends: mono-runtime (>= 2.10.1) but 2.10.5-1 is to be installed
         Depends: libc0.1 (>= 2.13) but it is not going to be installed
         Depends: libgconf2.0-cil (>= 2.24.0) but 2.24.2-1 is to be installed
         Depends: libgdk-pixbuf2.0-0 (>= 2.24.0) but 2.24.0-1ubuntu1 is to be installed
         Depends: libglib2.0-cil (>= 2.12.10-1ubuntu1) but 2.12.10-2ubuntu1 is to be installed
         Depends: libgtk2.0-cil (>= 2.12.10-1ubuntu1) but 2.12.10-2ubuntu1 is to be installed
         Depends: libmono-cairo4.0-cil (>= 2.10.1) but 2.10.5-1 is to be installed
         Depends: libmono-corlib4.0-cil (>= 2.10.1) but 2.10.5-1 is to be installed
         Depends: libmono-posix4.0-cil (>= 2.10.1) but 2.10.5-1 is to be installed
         Depends: libmono-system-core4.0-cil (>= 2.10.3) but 2.10.5-1 is to be installed
         Depends: libmono-system4.0-cil (>= 2.10.1) but 2.10.5-1 is to be installed
         Depends: gnome-icon-theme (>= 2.16) but 3.2.0-0ubuntu1 is to be installed"

Can anyone assist me in removing and/or installing the current packages and dependencies for Banshee?

Thanks in advance!

---

### Post by ChavaiotH on 2011-10-15
Same problem, no solution found.

---

### Post by ChavaiotH on 2011-10-15
I found a solution for me (ubuntu 11.10 64-bit)

1. type this in terminal:

*sudo apt-get install libmtp9 libmtp-common*

this ask to remove vlc and libmtp8 say yes

2.     [I]sudo apt-get install banshee

[/I]latest banshee installed[I].
[/I]

---

### Post by stevedude on 2011-10-15
Thanks ChavaiotH!

But does this mean I won't be able to use VLC?  I use VLC for most everything else media related.

I'll give it a try and repost later.

---

### Post by stevedude on 2011-10-15
You are right ChavaiotH.

This worked with no issues and I'm glad to have my Banshee back. It does remove your VLC player so I am hoping that in the future that those conflicts will be resolved so I can use both programs.

** EDIT ** For those in the same situation, I found a program called "UM Player" that I like a whole lot more than VLC Player. So for the media I needed VLC player for, UM Player is able to play the same types of media. This workaround actually suits me better.

---

### Post by machumi14 on 2011-10-20
thanks it works but after it uninstalled vlc i tried re-installing in ubuntu tweak and now i have both banshee and vlc working.

---

### Post by stevedude on 2011-10-27
~ Just as an update ~

Update Manager had notifications today (10-27-2011) for an update to VLC Player (ver. 1.12) on my system. I installed the updates and now I have VLC Player back and working along with Banshee so I am a happy camper right now!

---

