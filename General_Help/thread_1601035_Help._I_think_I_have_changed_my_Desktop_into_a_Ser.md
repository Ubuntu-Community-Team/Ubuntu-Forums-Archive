---
title: "Help. I think I have changed my Desktop into a Server"
date: 2010-10-19
forum: General Help
---

### Post by Bryan55 on 2010-10-19
I was trying to fix my mic that was not working by following these instructions.
--------------------------------------------------------------------------------------------------------
                                  **Howto fix microphone on Ubuntu 9.10**             
                                                                  1. From ubuntu menu go to System > Administration > Synaptic Package Manager
 
 2. Search for "linux-backports-modules-alsa-2.6.31-15-generic" - the  version number of this package should match your current (latest)  kernel. To find out your kernel version type "uname -a" in terminal.
----------------------------------------------------------------------------------------------------------
but I installed the server version by mistake and it seems to have changed my PC into a sever. Even though I removed it again.

When I run "uname -a" in the terminal it now says sever after the kernel number.

How can I get my Desktop back ????

Thanks for any help.

---

### Post by wojox on 2010-10-19
Try

```
startx
```

See if it does anything.

---

### Post by ironic.demise on 2010-10-19
Try reinstalling the desktop gui...
I believe it's
```

sudo apt-get install ubuntu-desktop

``` you may want a double check.

---

### Post by Bryan55 on 2010-10-19
I ran " startx" and got.
-----------------------------------------------------------------------------------------
bryan@Bydand:~$ sudo startx
[sudo] password for bryan: 


Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
bryan@Bydand:~$ 
--------------------------------------------------------------------------------

Bryan

---

### Post by Hippytaff on 2010-10-19
Just to clarify, have you lost the desktop or are you worried about it saying 'server' after the kernel details?

---

### Post by Bryan55 on 2010-10-19
"Just to clarify, have you lost the desktop or are you worried about it saying 'server' after the kernel details?
To be honest I don't know what a sever version looks like but my desktop has changed. I no longer have the minimized, maximize and quite function at the top right corner of windows.

Bryan.

---

### Post by Hippytaff on 2010-10-19
> **ironic.demise said:**
> Try reinstalling the desktop gui...
I believe it's
```

sudo apt-get install ubuntu-desktop

``` you may want a double check.

ok...sorry to butt in...I'd do this and see what happens :-)

---

### Post by Bryan55 on 2010-10-19
Here is what I got


bryan@Bydand:~$ sudo apt-get install ubuntu-desktop
[sudo] password for bryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
  paprefs xdotool libgconfmm-2.6-1c2 libgtkglext1 paman libinklevel5
  libetpan13 pulseaudio-module-zeroconf
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bryan@Bydand:~$ 
Display all 2362 possibilities? (y or n)


Bryan

---

### Post by themusicalduck on 2010-10-19
So the only difference is that the buttons at the top right have gone? Or has the entire of the title bar gone? So there is no border on the top of windows? Posting a screenshot might help.

The server edition means no desktop at all and just a command line, so you haven't quite changed your install that drastically yet.

p.s. I'm from Malvern, UK too :guitar:

---

### Post by wojox on 2010-10-19
Yeah this is a good one. You have a server kernel and some gui functions? Try

```
sudo apt-get install --reinstall ubuntu-desktop
```

Sometimes giving it the --reinstall flag will help. :)

---

### Post by Hippytaff on 2010-10-20
A bit dangerous?

```

sudo apt-get remove ubuntu-desktop && sudo apt-get install ubuntu-desktop

```

get rid completely and resinstall?

---

### Post by tajiknomi on 2010-10-20
[SIZE=2]*Post your desktop **Screen-shot**...it will be helpful...*[/SIZE]

---

### Post by Bryan55 on 2010-10-20
Hi themusicalduck. 
Yes the title bar has gone which also means I can not move windows about which is making life difficult. I have also been reduced to one desktop.
Here is a screenshot of the Terminal window when I tried to reinstall as suggested by wojox.

Hippytaff. I might resort to dangerous stuff but not yet.

Thanks for the help.
Bryan.

PS I live near the Wyche.

---

### Post by Bryan55 on 2010-10-20
Hi.
Have just found that the drivers for my ati/AMD card had been deactivated when I activated them the appearance and behavior of my desktop returned to normal. Though I have no sound which I am now working on.( fixed )

The only thing that concerns me now is that my System thinks it has a Sever Kernel (see attached) Could this affect updates or upgrades??

Bryan.

---

### Post by wojox on 2010-10-20
> **Bryan55 said:**
> Hi.
Have just found that the drivers for my ati/AMD card had been deactivated when I activated them the appearance and behavior of my desktop returned to normal. Though I have no sound which I am now working on.( fixed )

The only thing that concerns me now is that my System thinks it has a Sever Kernel (see attached) Could this affect updates or upgrades??

Bryan.

No it doesn't care what kernel your using from the repo's. Good call on the Visual Effects. :P

---

