---
title: "Ubuntu 11.04 NVIDIA Problem"
date: 2011-05-31
forum: General Help
---

### Post by cpsusie on 2011-05-31
I've reviewed a whole bunch of other threads but can't seem to find an adequate solution.

I fresh installed (erasing 10.04 LTS installation completely) today on my workstation that has an Nvidia GTX 280 discrete graphics card.

After installation was complete, I noticed under "additional drivers" that my nvidia driver was activated but not currently in use.

So ....
I tried to make it currently in use by that GUI and discovered there was no way to do it.

Then I tried:
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

Restarted.  Still got the queer message about not being in use.  So I uninstalled the NVIDIA drivers.

Then I downloaded the driver NVIDIA.....run from the NVIDIA website and tried to install it with:
sudo sh NVIDIA.run (with the full file name).

Then it tells me that I can't do that because an X server is running.  

So I kill the X-Server from the command line (I forget the command I used) then I Cntr-Alt-F1ed to get to a CLI.

Then I executed the damn file and it tells me it can't install the damn thing because some kind Noveau driver or some crap like that was preventing it and that it would try to write a "mod something" to stop the Noveau thing from running.    So I reset.  Then I was able to run the thing and install the driver.

Well, it restarts and I'm back to having a graphics driver (sort of).

Problem is, even now, IT ISN'T ACCELERATING!  

In every step above, regardless of the default, using the update commands running the .run script, whatever, I got NO or EXTREMELY POOR 3d acceleration, leading me to believe that regardless of what anything said, the proper nvidia drivers were never actually utilized.  

NOTE: Unity DID work -- regardless of how I installed them.  HOWEVER: no option to activate graphical effects, and my 3d emilia pinball game (which ran great on 10.04) got such poor FPS that it was both nauseating and unplayable.

I am considering downgrading to 10.10.  I would like to keep 11.04 just to have the latest, but I don't really care about the stupid unity thingy.  I DO NEED FULL 3D Acceleration.

Anybody have a workaround.  

It seems that other people were satisfied with getting unity to work.  I never had a problem getting unity to work.  What I need is the hardware accelerated graphics.

Thanks.

---

### Post by jocefus on 2011-05-31
This happened to my older laptop after using it problem free for a month or so. Booted up today and low graphics mode, nvidia-current is installed but not in use. I dunno what happened. 

The default setup doesn't use xorg.conf, but I created one to force nvidia to load. After 'sudo service gdm restart', ok I got my graphics back. Used for a while, then I had to run some errands. When I tried to boot up later on, my machine hangs on the splash screen. Apparently something during boot doesn't like the xorg.conf because I removed it using the recovery console and booted normal, but no nvidia driver again. 

I had nothing important saved, configured, or customized, so I did a fresh install and it is working right again. If it happens again, I am going back to LTS as well.

---

### Post by cwwilson721 on 2011-05-31
A few things:
[LIST]
[*]Installing the Nvidia!.run file from Nvidia is a pain. Ubuntu likes to install the open source Nvidia drivers if you uninstall the proprietary ones. Unless you know whta you're doing, don't bother.
[*]When the Proprietary drivers are installed in 11.04, Ubuntu will report 'not activated' in that app. But, if you can run nvidia-settings, you will see that they ARE activated, and working.
[/LIST]So, what to do?

Reinstall the proprietary drivers, run nvidia-settings (if it runs, they're working) and DON'T BELIEVE ADDITIONAL DRIVERS APP

(All of this IS in 40-50 threads in here. A search will find it)

---

### Post by timgood on 2011-06-01
This is a known bug, and as far as I know there is as yet, no solution to it. However, the information given is incorrect: the driver is installed and activated, and you do not need to re-install it. If you are using Unity, it will not load without the driver installed. So if you see Unity, the driver is working. More info here: [https://bugs.launchpad.net/ubuntu/+s...73/+bug/777493](https://bugs.launchpad.net/ubuntu/+s...73/+bug/777493)

Hope this helps.

---

