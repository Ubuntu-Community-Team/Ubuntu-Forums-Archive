---
title: "Problem with display - now major probs..."
date: 2010-12-15
forum: General Help
---

### Post by Reishtak on 2010-12-15
Hi all, I will briefly describe what I have been trying to do which has led to my problem, so you see why I have made some (probably) very foolish decisions!

I have been trying to find a reliable way to run a version of OSX on my alienware area51 desktop.  After various tries of iDeneb and iATKOS, i started playing with virtual machines.  I have used ubuntu a bit before, but am not an experienced user by any measure!  VM osx in windows seemed very unstable so I thought I would reinstall ubuntu (previous version was not working, can't remember why)!

I installed 10.10 64bit desktop, which went on fine.  As I use a DVI-HDMI cable to my TV as a monitor, I had problems with the display.  I installed the nvidia drivers as suggested by ubuntu, and tried various xorg.confs to no avail.

After a quick nosey around ubuntu (on an OLD laptop, that I'm using now) I discovered the "Nvtv TV out" app so decided to install that on my desktop.  After a few tries, the application just wouldn't launch, so I thought that maybe I should remove the nvidia drivers first.

Not being an expert, I did this in the synaptic package manager, and removed all the nvidia entries (writing this I realise I am an idiot for not looking for guides online).  I rebooted the system, and now it will boot up fine, I get the bios display and the OS menu (still have vista running on the desktop) but after that, there is no display at all.

I have the same (see boot options and bios but no desktop etc) if I connect to the TV via DVI-VGA and into the tv's PC input, so I am sure it is not that. 

Also, windows vista runs fine (aside from shitty overscan-corrected display) with the current configuration, so I am sure I have just buggered ubuntu.

I have tried to reinstall ubuntu, but am not confident with the menus, and worry that I will delete partitions / os boot sectors etc that I need.  I also have a lot of files that I cannot afford to lose (photos etc).

I am stuck and not sure what to do.  Needless to say I will be googling all night, but I thought I might get some help from the forums as well!

At the moment, I would be happy to go back to an ubuntu install with display problems, and then try to tackle the overscan issues, rather than just a useless installation!

Sorry for the extremely long post, but I thought it better to be over-descriptive than not give enough information!

Many thanks in advance for any help and or tips you gurus can provide!

Ed

---

### Post by Reishtak on 2010-12-16
Bump (from page 18!)

Im still majorly stuck - anyone with any ideas, please?

---

### Post by Krytarik on 2010-12-16
I was a little deterred yesterday by seeing so much text.;)

However imo it should not be too difficult to fix your problem.

Try starting Ubuntu in "recovery mode". Hopefully it works and you get at least a console login. 

If so, look in /var/log/apt/history.log for the nvidia-packages you have removed:
```
cat /var/log/apt/history.log | grep nvidia
```
re-install them, all at once:
```
sudo apt-get install PACKAGE_NAMES
```
restart:
```
sudo shutdown -r now
```
or Ctrl+Alt+Del;)

---

### Post by Reishtak on 2010-12-22
Thanks for the helpful suggestion, but still no luck...

I have tried this with (and without) all the different startup command options that I'm aware of (not many) and still, no display, no console, nothing.

Please, does anyone have any other suggestions?  Im completely stuck :(

---

### Post by Reishtak on 2010-12-23
Any ideas anyone please?  So stuck....

---

### Post by Krytarik on 2010-12-23
Have you identified and re-installed the previously removed packages then?

Does a Ubuntu LiveCD work?

---

### Post by mastablasta on 2010-12-23
easiest solution (probably a bit strange)
 
Boot with liveCD (or USB to be a bit faster). Access and move important file to Vista partition/side or to external hard disk.
 
Delete or just reinstall the whole Ubuntu system.

---

### Post by Reishtak on 2010-12-23
> **Krytarik said:**
> Have you identified and re-installed the previously removed packages then?

No - as I mentioned above, I cannot even get any display after the OS choice menu.  No terminal in recovery mode, nothing at all!

> **Krytarik said:**
> Does a Ubuntu LiveCD work?

If I put the CD in, it allows me the option of installing ubuntu again, but I am not sure which installation is the one I have already, and where to install a new version.  Also I didnt think that I needed a whole new install, but maybe this is the only way to sort out my problem.

I am surprised that there is not more support for things like this, surely there are other newbie users like me who seem to have a habit of messing things up?

Thanks again for your help
Ed

---

### Post by Reishtak on 2010-12-23
> **mastablasta said:**
> Delete or just reinstall the whole Ubuntu system.

Thinking now this is my best option for a quick solution.

How do I identify where the Ubuntu installation is?  Can I delete it from within windows (vista)?  

Thanks for the help

---

### Post by Krytarik on 2010-12-23
If you don't have another monitor to recover your install, I'm afraid a re-install is the only solution.

Check in Vista for the partions, you should find a single ext3/ext4-partition, this would be the partition Ubuntu was installed to. You can format that partition from within Vista also, but during the install process it may be formatted again.

---

