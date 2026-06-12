---
title: "Error: could not write bytes: Broken pipe"
date: 2012-09-15
forum: General Help
---

### Post by aplonis on 2012-09-15
It happened like this on Ubuntu 12.04 LTS:

1. Tried to update nVidia on a Dell M6300 following some online instruction.
2. On reboot got an nVidia API mismatch. Black screen.
3. Per another instruction, to fix the problem I did this: "sudo apt-get purge nvidia*" followed by "sudo apt-get update"
4. Rebooted.
5. Now xserver comes up and I get a purple graphical login.
6. But on entry of password, screen flashes black, and very briefly says...
   "could not write bytes: Broken pipe"
   ...plus a few more lines that aren't on long enough to read.
7. Goes back to purple graphical login screen.

Like that, over and over. Good thing I have two Ubuntu laptops or I'd not be able to post this query. I have no Internet at the house and am mooching WiFi from a laundromat. So, please, be detailed with any help as it will take me plural trips to the laundromat to sort this out. And I am no kind of Linux guru. Hand holding probably needed. Thanks in advance.

---

### Post by Epodx64 on 2012-09-15
First try and click on the Ubuntu logo on the log in screen and switch it to 2D Unity and see if you can log into that if you can go to Dash then to Jockey and download and install the Current-Post-Release drivers. 

If that doesn't work you could try using the VESA driver reboot your computer and before grub loads hit escape and add vga=391 to the boot parameters then follow above advice

---

### Post by aplonis on 2012-09-18
No amount of tapping or holding ESC during attempts to reboot did anything but delay the reboot. However, after a boot, once at the purple login screen, CTRL-ALT-F1 does get me a CLI. I can login there. 

But how do I install Current-Post-Release drivers via "sudo apt-get ..." or the like, please?

---

### Post by bogan on 2012-09-19
Hi!,** aplonis**,

After logging in on the TTY prompt there are several alternatives: apt-get install; jockey-gtk or synaptic.

The first: is the only choice if the graphics screen is not accessible, yours is, so it is not essential: ```
sudo apt-get update 
sudo apt-get install nvidia-current-updates # the package name of the post-release version 295.49
```Second will give you access to the same GUI as running System Settings>Additional Drivers, and it gives no indication of which version it will load, and maybe not only that but the name may be uninformative; eg: " NVIDIA binary Xorg driver, kernal module and VDPAU library"```
gksu lockey-gtk
```Thirdly: ```
gksu synaptic
```Will run the Synaptic Package Manager and you can choose which version to mark for installation, and select 'Apply'.

When the Window opens, give it time to renew the index and display " Quick Filter " above the string box, then enter 'nvidia'.

I would recommend, if it shows, 'nvidia-current' version 304.43-0ubuntu1, rather than the 'nvidia-current-updates' version 295-49-0ubuntu0.2.

I have had the 'Broken Pipe' error messages, at log-in and shut down,  ever since I installed 12.04 on the first day of its release. I have  Posted about it but have had no response, nor found any info about its  cause or effect. For me, at least, it seems to have no importance.

Chao!, **bogan.**

---

### Post by aplonis on 2012-10-10
My problem was plural errors which led to non-guru confusion loop inside my brain. I fixed it after consulting several forum help-request posts (mostly answered by bogan).

Broken pipe went away by re-upgrading nvidia from scratch, like so...

sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install invida-current-updates


Which repaired the mis-match in drivers. But that **still** left me stuck in a password entry loop (same as before but without the broken pipe message flashing in between). The reason for the login loop was that root now had ownership of my Xauthority file. Per another how-to, I just removed it, like so...

sudo rm .Xauthority

Then I rebooted and all was hunky dory.

Thanks to all

---

### Post by dnintzel on 2013-01-24
Thanks aplonis. I had the same problem after installing VNC server and rebooting and doing: 
1. CTRL-ALT-F1 (to get a CLI)
2. then "sudo rm .Xauthority
 
...fixed my login issue as well.
 
This is a fresh install of ubuntu and i'm a noob so i may have done something else to shoot myself in the foot. Anyway, relieved to be fixed.

---

### Post by PhilAlban on 2013-03-04
> **aplonis said:**
> My problem was plural errors which led to non-guru confusion loop inside my brain. I fixed it after consulting several forum help-request posts (mostly answered by bogan).

Broken pipe went away by re-upgrading nvidia from scratch, like so...

sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install invida-current-updates


Which repaired the mis-match in drivers. But that **still** left me stuck in a password entry loop (same as before but without the broken pipe message flashing in between). The reason for the login loop was that root now had ownership of my Xauthority file. Per another how-to, I just removed it, like so...

sudo rm .Xauthority

Then I rebooted and all was hunky dory.

Thanks to all

Thanks for this - it worked for me as well. However, I had no Xauthority issues. I also needed to run a repair from recovery mode. I am running a dual-boot (rEFIt) MacBook 5.1, with 12.04 LTS and the newest experimental NVidia drivers obviously broke my Ubuntu install.

Couldn't figure it out, since I only got the login (CLI) screen once and never stuck around long enough for this error to appear. Ended up leaving the MacBook at boot-up for a few minutes and came back to this error. Thank you very much Steam for requiring the latest (experimental drivers). (Actually, the latest Steam lets me play with those you suggested, but warns me they're out of date).

---

### Post by jabbarZA on 2013-07-06
> **aplonis said:**
> My problem was plural errors which led to non-guru confusion loop inside my brain. I fixed it after consulting several forum help-request posts (mostly answered by bogan).

Broken pipe went away by re-upgrading nvidia from scratch, like so...

sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install invida-current-updates


Which repaired the mis-match in drivers. But that **still** left me stuck in a password entry loop (same as before but without the broken pipe message flashing in between). The reason for the login loop was that root now had ownership of my Xauthority file. Per another how-to, I just removed it, like so...

sudo rm .Xauthority

Then I rebooted and all was hunky dory.

Thanks to all

Thanks!! This worked for me. After searching all over and purging the Official nvidia drivers, that i had loaded from their site, which is how i broke it all in the first place. I managed to get the login screen back and that was it. but deleting  .Xauthority has solved that problem. Was getting to the point where i was considering a clean install. Anyway, thanks for this.

---

### Post by drknght on 2014-03-26
Thanks... Wish I had found you 4 hours earlier...

My system was wrecked trying to install Ati drivers for V5700 firepro for mining Litecoins

... Learned more about X and Ati and working the commandline than I wanted to.

---

### Post by brieven on 2014-08-23
ah thanks. i've had this problem for ages now. super.

---

