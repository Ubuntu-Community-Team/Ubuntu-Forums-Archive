---
title: "No available drivers for NVidia GT 240 in Lucid Lynx (10.04 LTS)"
date: 2010-04-30
forum: General Help
---

### Post by mstine on 2010-04-30
I'm having serious problems getting Lucid working with my NVidia GT 240 graphics card.  

When starting up using the default Nouveau driver, I get some pretty nasty screen corruption when I should be seeing the Ubuntu splash screen.  Also, I get numerous "misaligned reg" errors at this point, which I assume means nouveau doesn't support this specific card.  Once the X Server has started, everything seems to work OK until I try to kill the X Server upon shutdown, or even if I simply attempt to switch to a tty (Ctrl+Alt+F1).  Upon either of those conditions, the screen simply freezes, continuing to display the current framebuffer contents.  If I switch back to Ctrl+Alt+F7, then desktop responsiveness returns.

Unfortunately, even the newest driver available under the "Hardware Drivers" menu (v190.53) does not support the GT 240, along with many of the newer NVidia cards.

And possibly most unfortunate of all, if you check under the Lucid "Known Issues" ([http://www.ubuntu.com/testing/lucid/beta2]("http://www.ubuntu.com/testing/lucid/beta2")), it states:
> Because of the new alternatives system used for nvidia driver packages, the nvidia installer from NVIDIA's website currently doesn't work. 

Is there any known workaround to install the NVidia drivers from NVidia's website in Lucid?

Thanks in advance!
Matt

---

### Post by mstine on 2010-04-30
After running
> dpkg -l | grep nvidia
it seems that the nvidia-current driver has installed 195.36 on my system... it just isn't working for some reason.

I'll continue to look into this and post a solution if I find one.

In the meantime, please respond if you find a way to force installation of the downloaded NVidia driver.  It would be useful to eventually use their custom drivers for OpenGL performance analysis among other things.

Thanks!

---

### Post by GSF1200S on 2010-04-30
You will need the 195 drivers in order to use such a new card. If it isnt showing up in Hardware drivers, open a terminal and do:

```
sudo apt-get update
sudo apt-get install nvidia-current-modaliases nvidia-current
sudo apt-get update
```
Then, try to open Hardware Drivers and see if the 195 driver is listed. You shouldnt need to do this, so I dont know whats going on. Let me know how this goes..

**EDIT** Before restarting and AFTER enabling the driver in Hardware Drivers, I would suggest running:
> sudo nvidia-xconfig
just to make sure Xorg is up to date.

---

### Post by mstine on 2010-04-30
I tried what you recommended, and I even tried running
> sudo apt-get install -reinstall nvidia-current nvidia-current-modaliases
but when trying to start X, I get an error stating that my kernel module version 190 is incompatible with my driver component version 195.

I'm not sure how things got into this state, but I've got a feeling it's from attempting to install the downloaded NVidia drivers.

I'm going to give Lucid a reinstall and simply try again, this time NOT installing anything directly from NVidia.

---

### Post by GSF1200S on 2010-04-30
> **mstine said:**
> I tried what you recommended, and I even tried running

but when trying to start X, I get an error stating that my kernel module version 190 is incompatible with my driver component version 195.

I'm not sure how things got into this state, but I've got a feeling it's from attempting to install the downloaded NVidia drivers.

I'm going to give Lucid a reinstall and simply try again, this time NOT installing anything directly from NVidia.

Thats because the common version is for 190, but 195 is the drivers installed. Did you enable 195 in the Hardware Drivers section? A reinstall isnt likely going to help :( Try opening synaptic, removing everything related to 190, closing synaptic, sudo apt-get update, and open hardware drivers again.

Granted, I have a 9800GTX, but I am using the 195 drivers and on 10.04. All I did after a clean install was open a terminal and type:
```
sudo apt-get update
```
and then open Hardware Drivers and select the 195 series, reboot, and it all worked. Let me know if this helps at all

---

### Post by itsjustarumour on 2010-04-30
> **mstine said:**
> I'm having serious problems getting Lucid working with my NVidia GT 240 graphics card.  

When starting up using the default Nouveau driver, I get some pretty nasty screen corruption when I should be seeing the Ubuntu splash screen.

I'm using an NVidia GT 240 card, and I was getting exactly the same thing on Lucid on all versions up to 10.04 RC1 (32-bit) with the NVidia driver - but 10.04 Final resolved that problem (strangely the card/NVidia driver worked perfectly on 9.10). I'm using the 195.36.15 driver now which is from the normal Ubuntu repos. 

Theres a review of a GT 240 card on Phoronix at [http://www.phoronix.com/scan.php?page=article&item=ecs_geforce_240&num=9](http://www.phoronix.com/scan.php?page=article&item=ecs_geforce_240&num=9) which states:

"Unfortunately, for those interested in using this with an open-source driver, the Nouveau driver stack does not yet support this graphics card with kernel mode-setting or really any support at all, but it should come in due time."

That was 22nd January 2010 - I don't really know if things have improved since then.

I'm guessing that support for these cards with either driver perhaps "isn't quite there" yet...


***EDIT*** Just one question - are you on a fresh Lucid install, or did you upgrade from 9.10?

---

### Post by mstine on 2010-04-30
Weird.  After reinstalling, I ran
> sudo apt-get update
followed by installing the latest NVidia driver from the Hardware Drivers menu.  

After this I rebooted the machine, and upon restart got a small error dialog with the same error message I would get before.  Something along the lines of failing to start the NVidia kernel module.  I logged in at a terminal without X, and simply ran > startx, not expecting anything to happen.

Lo and behold, the X server started without issue, and I was running the 195 drivers.

I rebooted and tried this again, and the same thing happened (hand to manually run startx to get it working).

On the third reboot, I planned on writing down the error message in the small dialog box, but this time Ubuntu booted straight into X without a hitch.



In short, everything works now.  All I had to do was:
[LIST][*]sudo apt-get update
[*]install latest nvidia drivers from hardware drivers menu
[*]reboot a few times[/LIST]

Thanks for the help!
Matt

---

### Post by GSF1200S on 2010-04-30
> **mstine said:**
> Weird.  After reinstalling, I ran

followed by installing the latest NVidia driver from the Hardware Drivers menu.  

After this I rebooted the machine, and upon restart got a small error dialog with the same error message I would get before.  Something along the lines of failing to start the NVidia kernel module.  I logged in at a terminal without X, and simply ran , not expecting anything to happen.

Lo and behold, the X server started without issue, and I was running the 195 drivers.

I rebooted and tried this again, and the same thing happened (hand to manually run startx to get it working).

On the third reboot, I planned on writing down the error message in the small dialog box, but this time Ubuntu booted straight into X without a hitch.



In short, everything works now.  All I had to do was:
[LIST][*]sudo apt-get update
[*]install latest nvidia drivers from hardware drivers menu
[*]reboot a few times[/LIST]

Thanks for the help!
Matt

Thats strange. It worked the first time for me- perhaps a bug with that card? At least it works now :)

---

### Post by itsjustarumour on 2010-04-30
@Matt - just one other thing - before you do a reinstall, check the troubleshooting section at [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)  

Thinking about it, I seem to remember having a similar problem a couple of years ago, something to do with a mismatch between the driver and the kernel modules (ie one starting with 1.x.x and the other starting with 1.x.y)

---

### Post by itsjustarumour on 2010-04-30
@Matt - Ah - cool - glad you got it working!  :)

---

