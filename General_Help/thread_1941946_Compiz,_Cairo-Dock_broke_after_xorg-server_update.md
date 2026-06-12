---
title: "Compiz, Cairo-Dock broke after xorg-server update"
date: 2012-03-16
forum: General Help
---

### Post by Cavsfan on 2012-03-16
First of all, I have a 64 bit Ubuntu 10.04 Lucid Lynx system, with PPAs for Thunderbird and Firefox to keep them up to date. 
I also update my nVidia driver when a new one comes out; currently 295.20 which came out on 2012.02.13.
Other than that it is generic.

Yesterday I got several updates I can't recall all of them but I know xorg-server was in the mix. I subscribe to the Lucid Lynx email updates so I am aware of what is coming.
Got the updates, rebooted, compiz and cairo-dock were broken. Compiz was not even running and cairo-dock was just a box that looked like my login wallpaper.
When I entered **compiz --replace** in terminal, it hung the system and I could only press the reset button on the PC.
SCSM looked fine.

Thinking it had something to do with the nVidia driver, I tried to reinstall the two kernels as I had gone by this tutorial to install the driver when a new kernel was installed:

[[COLOR=blue]_HOWTO: Automatically update manually installed NVidia drivers after kernel updates_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")

That did not work. Nothing changed. I even deleted the** /lib/modules/2.6.32-38-generic** folder after removing that kernel because it would not delete it as the nVidea driver was in there.
This forced the driver to be re-installed into the kernel. This still did not solve the problem.

So, after googling for a solution and not finding any, I decided to re-download the driver and install it again via this webpage which I have always used:

[[COLOR=blue]_Instructions on how to install nVida driver in Lucid Lynx 10.04._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")

This finally fixed the problem. I will have to perform the steps in the 1st HOWTO mentioned above as I think the previous driver is corrupt.

I will mark this as resolved but, I wanted to throw this out there in case there are others with the same problem.

---

