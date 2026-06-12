---
title: "Ubuntu Lucid Problems"
date: 2010-05-02
forum: General Help
---

### Post by klapointe on 2010-05-02
I installed Ubuntu 10.04 two days ago, and the upgrade went fine other than the timing for it took nearly the entire day to finish. However, in the first night, the computer crashed several times. I've never experienced a crash in any Ubuntu version before, so this was quite new.

First, I was using FireFox and it stopped loading. I could move the mouse but could not click anything. No matter what I clicked, nothing happened. Nothing would respond, so I restarted. It loaded fine, other than the slow boot, and I was able to use it for some time before it crashed again. This time I was in the middle of watching a youtube video when the computer froze. It unfroze a few minutes later, and I exited from the video, and the title bar disappeared. I started clicking around, and then the window minimized. I tried to maximize, and nothing happened. I clicked FireFox from the top bar, and both the tool bar and window bar disappeared.

I have an Open Office document file on the desktop that I tried to open, and it came up with an error saying it could not find a program to open it. I restarted again, then let it sit for the night. The next day went by fine, and I was expecting it to be just a one time thing.

However last night, it had the same problem with the disappearing title bar that made me restart. After that, I was working on some files when I clicked the Calender to check the dates, and it froze trying to open that so I had to restart again. Today it has been going by fine, but it crashed about a half hour ago and I had to restart.

Is there anything I can do to fix this? Please tell me if there's anything I can do other than downgrade it from a Karmic boot CD. 

Thank you.

---

### Post by BrokeMahPC on 2010-05-02
Please list some hardware, particularly desktop pc / laptop, graphics card etc. Did you install any drivers under system, admin, hardware drivers? any idea what video driver you are using?

---

### Post by klapointe on 2010-05-02
> **BrokeMahPC said:**
> Please list some hardware, particularly desktop pc / laptop, graphics card etc. Did you install any drivers under system, admin, hardware drivers? any idea what video driver you are using?

Desktop PC
Integrated G-Force 7150 Graphics
Motherboard model: N-Force 630I

I have installed the NVIDIA Accelerated Graphics Driver version 173 from the Hardware drivers, but it is not activated. 

How do I find the other information?

---

### Post by BrokeMahPC on 2010-05-02
> I have installed the NVIDIA Accelerated Graphics Driver version 173 from  the Hardware drivers, but it is not activated. 

OK, so after you installed you went to system-admin-hardware drivers and enabled the Nvidia driver it recommended? did you then go back and press the remove button to try and switch back to the default driver or was there a problem with the install?

It's likely you have  a driver problem - I'm not an Nvidia expert but the ubuntu help pages have the following for cleaning up a driver mess:

**Problem:  Need to fully remove -nvidia  and installing or reinstall  -nouveau from scratch**
Here is a recipe which removes  all old video drivers, and reinstalls  nouveau: 
sudo nvidia-settings --uninstall
  sudo apt-get remove --purge nvidia*
  sudo apt-get remove --purge xserver-xorg-video-nv  xserver-xorg-video-nouveau
  sudo apt-get install nvidia-common
  sudo apt-get install xserver-xorg-video-nouveau
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri  xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
Then _reboot_ your system and when it comes up it will be  running  with nouveau.
I'm not an Nvidia expert at all but do you need the Nvidia drivers?  Might be best to stick with nouveau for now? ATI have not caught up with  Lucid yet and I am sticking to the default Radeon driver.

---

### Post by klapointe on 2010-05-03
> **BrokeMahPC said:**
> OK, so after you installed you went to system-admin-hardware drivers and enabled the Nvidia driver it recommended? did you then go back and press the remove button to try and switch back to the default driver or was there a problem with the install?

It's likely you have  a driver problem - I'm not an Nvidia expert but the ubuntu help pages have the following for cleaning up a driver mess:

**Problem:  Need to fully remove -nvidia  and installing or reinstall  -nouveau from scratch**
Here is a recipe which removes  all old video drivers, and reinstalls  nouveau: 
sudo nvidia-settings --uninstall
  sudo apt-get remove --purge nvidia*
  sudo apt-get remove --purge xserver-xorg-video-nv  xserver-xorg-video-nouveau
  sudo apt-get install nvidia-common
  sudo apt-get install xserver-xorg-video-nouveau
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri  xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
Then _reboot_ your system and when it comes up it will be  running  with nouveau.
I'm not an Nvidia expert at all but do you need the Nvidia drivers?  Might be best to stick with nouveau for now? ATI have not caught up with  Lucid yet and I am sticking to the default Radeon driver.


I tried all of this, but I'm not sure what Nouveau is, or if it is even working on my computer. When I click Monitors "Ancor Communicatoins Inc 20" comes up. I'm not sure what that means. However, the graphics of the computer, what it displays, isn't always too clear and doesn't look right. The first command line - 
sudo nvidia-settings --uninstall
- Came up with an error. I went on to the next steps and they all work, except the last one didn't do anything. I rebooted at that point, and it said there was no graphics driver installed for this computer, so it gave me the choice to run it in Ubuntu Low Graphics driver mode for the session. I clicked that to try and see what was going on. Then I rebooted and it came up with that screen again. This time I clicked Default Driver, and it came up with this. It's froze twice and I've had to restart, however the purple Ubuntu screen does what it should when it shows the white dots loading red. 

I'm pretty certain I messed up something along here, because there is nothing on my computer that says anything about Nouveau.

---

### Post by BrokeMahPC on 2010-05-03
Ok Nouveau is the new open source driver for Nvidia cards which is supplied by Ubuntu. It is installed at 1st install you don't need to do anything it's there.
If you were to go to System-Admin-HardwareDrivers it will give you the option of installing another driver provided by Nvidia - Nvidia-GLX-xxx. This should install over the top of Nouveau

Try the code I gave you again 1 line at a time but replace that 1st line with this:
sudo apt-get --purge remove nvidia-glx-* nvidia-settings

Try the following to fix any broken packages:
sudo dpkg --configure -a
sudo dpkg-reconfigure apt
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

Try activating the Nvidia driver under hardware drivers and see if it installs it. Hardware Drivers may show it as inactive even after install - that is just another bug - it should be installed and working.
Appologies for the above not working, Lucid is new and good info is scarce - even the ubuntu gods are giving conflicting advice.
If you get really stuck it may be worth doing a fresh install to get back to how things should be - I have had to do that a couple of time testing out the Beta and release candidate.

---

### Post by klapointe on 2010-05-04
> **BrokeMahPC said:**
> Ok Nouveau is the new open source driver for Nvidia cards which is supplied by Ubuntu. It is installed at 1st install you don't need to do anything it's there.
If you were to go to System-Admin-HardwareDrivers it will give you the option of installing another driver provided by Nvidia - Nvidia-GLX-xxx. This should install over the top of Nouveau

Try the code I gave you again 1 line at a time but replace that 1st line with this:
sudo apt-get --purge remove nvidia-glx-* nvidia-settings

Try the following to fix any broken packages:
sudo dpkg --configure -a
sudo dpkg-reconfigure apt
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

Try activating the Nvidia driver under hardware drivers and see if it installs it. Hardware Drivers may show it as inactive even after install - that is just another bug - it should be installed and working.
Appologies for the above not working, Lucid is new and good info is scarce - even the ubuntu gods are giving conflicting advice.
If you get really stuck it may be worth doing a fresh install to get back to how things should be - I have had to do that a couple of time testing out the Beta and release candidate.


Okay, so I have done this, and my computer is still crashing. I'm pretty certain the graphics card is working because I can view the text clearly again. Thanks for your help so far; I wish this was an easier problem to fix.

---

### Post by StuartN on 2010-05-04
> **klapointe said:**
> Okay, so I have done this, and my computer is still crashing. I'm pretty certain the graphics card is working because I can view the text clearly again. Thanks for your help so far; I wish this was an easier problem to fix.

A similar thread from earlier: [http://ubuntuforums.org/showthread.php?t=1469650](http://ubuntuforums.org/showthread.php?t=1469650) with links to some Launchpad bug reports you might wish to read.

(ignore the title, the OP has decided that it crashes without Firefox as well as with Firefox)

---

### Post by klapointe on 2010-05-04
> **StuartN said:**
> A similar thread from earlier: [http://ubuntuforums.org/showthread.php?t=1469650](http://ubuntuforums.org/showthread.php?t=1469650) with links to some Launchpad bug reports you might wish to read.

(ignore the title, the OP has decided that it crashes without Firefox as well as with Firefox)

Okay, so in short, I can just hold on and wait for a workaround to come up?

Thanks for all your help!

---

### Post by StuartN on 2010-05-04
> **klapointe said:**
> Okay, so in short, I can just hold on and wait for a workaround to come up?

Ideally you should check your log files and symptoms to see which Launchpad bug matches your problems, and post any additional information that you have on the relevant bug page.

---

