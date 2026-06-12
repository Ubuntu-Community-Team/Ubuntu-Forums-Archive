---
title: "Nvidia driver or card broken!"
date: 2009-07-18
forum: General Help
---

### Post by fallenshadow on 2009-07-18
I was playing the game Urban Terror 4.1 and it froze. I restarted the PC, it drops to the command line login instead of showing the Nvidia splash screen and then the GDM.

I have a really bad feeling that damage has been done to my graphics card but it may be only a problem with the Nvidia driver. I can still login via CLI but I need some command to disable the Nvidia driver and see will my PC boot Ubuntu 8.04. At the moment I am using an Opensuse liveDVD to post this and there are coloured streaks going down my monitor.

---

### Post by 3rdalbum on 2009-07-18
You say you can get to a command line on Ubuntu? Then log in and type:

```
sudo gdm
```

This should start gdm, or at least start the little wizard thing that gives you the option to try reconfiguring your graphics to "failsafe". From there you can try reinstalling the Nvidia driver.

The description of "coloured streaks" on your monitor does sound like possible graphics card overheating or damage, but it's just as likely to be the driver that the OpenSUSE live DVD is using. If you get the streaks when you boot Ubuntu in failsafe mode, that's when it could be a real problem.

---

### Post by fallenshadow on 2009-07-18
Thanks for the reply... I did try sudo gdm but it says that gdm is already running. :(

Another thing is that the text in grub is missing pixels. How can I boot with failsafe mode?

---

### Post by c0mput3r_n3rD on 2009-07-18
Does your motherboard have a defualt VGA, or any other monitor plug that you can plug into besides the videos card?  Open up the case and look at the video card while the computer is on.  What is it doing?  Is the fan spinning?  Take out the card and make sure every thing looks kosher.

---

### Post by fallenshadow on 2009-07-18
Does anyone have any commands I could use that might work before I go busting my PC open?? 

I would rather try some commands first to try and confirm if the problem is with my graphics card.

---

### Post by zeronothing on 2009-07-18
try using the command:

sudo /etc/init.d/gdm stop

then

sudo nvidia-config

then

sudo /etc/init.d/gdm restart


This will try and reconfigure the xserver with the Nvidia graphics card settings.

---

### Post by fallenshadow on 2009-07-19
Thanks but when I entered "sudo nvidia-config" I got a statement "command not found".

I opened up my computer and my graphics card looks fine... no burn marks or anything. I used a different monitor and the result is still the same so im pretty sure now that its not a hardware problem but it still might be.

Anyway I got this error message when I tried booting up... I think it may indicate a problem with X.

> 
Starting up...
Loading, please wait...

Xinit: name-to-dev-t(/dev/disk/by-uuid/75c7b727-80db-4ddc-8575-5ca2cfaba9fa)=sda(8,5)

Xinit: trying to resume from (/dev/disk/by-uuid/75c7b727-80db-4ddc-8575-5ca2cfaba9fa)

Xinit: No resume image, doing normal boot... 


I have other live-cds which can allow me to access my config files/edit them etc. Any ideas as to what to do?

---

### Post by jerome1232 on 2009-07-19
Those errors are normal, I believe this command will reconfigure x for you

```
sudo dpkg --configure -phigh xserver-xorg
```

If your seeing text glitches before you ever boot the os (in grub) I fear for your card.

---

### Post by jimmyhacker on 2009-07-19
This happened to me too!my graphics card is broken because of wrong ubuntu drivers.i had coloured dods and my monitor was closing&opening

---

### Post by fallenshadow on 2009-07-19
Yes the text glitches are present in grub... does this mean my graphics card is broken?

---

### Post by The Tronyx on 2009-07-19
> **jimmyhacker said:**
> This happened to me too!my graphics card is broken because of wrong ubuntu drivers.i had coloured dods and my monitor was closing&opening

I don't really think Ubuntu broke your graphics card.  There may have been a problem with the drivers or even the card itself but if it was the card, it was likely caused independent of something done by Ubuntu.

@fallenshadow
If the graphics errors are present at grub, this happens before any drivers are loaded by the OS since you haven't even booted into the OS yet - just accessed the boot loader.

If you take out the card, do the issues persist using onboard video?

I had a fairly similar issue and it turned out to be a problem with the motherboard itself.

---

### Post by fallenshadow on 2009-07-19
Yes the problem still persists after removing my graphics card. I guess its a motherboard problem then... do I have to buy a new motherboard so? :(

---

### Post by jerome1232 on 2009-07-19
Probably a motherboard issue then I think tronyx hit the nail on the head there. I couldn't say for absolute sure though, hardware problems can be deceptive at times.

---

### Post by fallenshadow on 2009-07-19
Would this motherboard suite my needs?:

[http://www.scan.co.uk/Product.aspx?WebProductId=771471](http://www.scan.co.uk/Product.aspx?WebProductId=771471)

I have:

1x Intel Core2 Duo 1.86Ghz
1x 1GB DDR RAM
1x 320GB hard disk
1x Nvidia 7650GS 256mb graphics card
1x Ralink wireless card
2x LG disk drives
1x Connect XL card reader
1x TV card

---

### Post by fragos on 2009-07-19
All current systems use DDR2 memory. If your video card is AGP you'll need to replace it as current mobos use a PCI-E (x16) slot for graphics. If your TV and Ralink cards are both PCI or if only one of them is PCI-E (1x) you should be fine there. You'll only have one IDE port for two CD/DVD drives. Your hard disk needs to be SATA, small plug compared to the many pinned arrangement with IDE.

---

### Post by fallenshadow on 2009-08-11
Hi guys it turned out to be a broken graphics card but I got a 9600GT for a replacement... however I tried to install the graphics drivers from Nvidia from the website and they did not work. Then I uninstalled them since they were useless and now Ubuntu won't boot properly. 

After the Ubuntu loading screen the monitor just flickers. At the moment I am using a live CD... once again! :(  Sigh... all this display problems are giving me a headache. If only Ubuntu provided official updates for its drivers I wouldn't be in this mess.

Can anyone offer me a solution via the command line?

Or I could also delete any conflicting files using the live CD.

---

### Post by fallenshadow on 2009-08-11
Is there a command to login as a user from the root command line?

---

### Post by hangfire on 2009-08-11
> **fallenshadow said:**
> Is there a command to login as a user from the root command line?

```
su - username
```

when done, typing exit will get you back to the root prompt.

---

### Post by fallenshadow on 2009-08-11
Thanks so much:

Continue discussion in this thread plz...

[http://ubuntuforums.org/showthread.php?t=1236571&page=2](http://ubuntuforums.org/showthread.php?t=1236571&page=2)

I will mark this as solved so we can just concentrate on one thread.

---

