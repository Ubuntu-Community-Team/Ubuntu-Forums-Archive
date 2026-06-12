---
title: "ubuntu does not boot (urgent)"
date: 2012-01-21
forum: General Help
---

### Post by AmirM on 2012-01-21
Update manager downloaded and installed all it needed and asked for restart.after rebooting I saw a proprietary driver for my nVidia graphic card is available,I downloaded and installed it,it said you have to reboot and this driver will be activated.
after the restart,ubuntu wont boot.after grub it shows that blinking cursor on top of screen for few seconds(as always did) but after that it just shows a blank screen(just backlight).
can anyone help?


ubuntu 10.04 LTS

Acer Aspire 5742G

UPDATE: now the question is how to uninstall graphic card driver?

---

### Post by ewz on 2012-01-21
sounds like the graphics driver hasn't installed properly, 
Try booting into Recovery Mode in the grub menu, from what I remember there are a few options for reconfiguring your Graphics driver.

hope this helps :-)

---

### Post by AmirM on 2012-01-21
> **ewz said:**
> sounds like the graphics driver hasn't installed properly, 
Try booting into Recovery Mode in the grub menu, from what I remember there are a few options for reconfiguring your Graphics driver.

hope this helps :-)
thank you but the recovery option in grub is not working properly.in fact it never did.
after showing some tasks being done,it goes blank.it should show command line,right? it doesnt.(it was like this before this new problem and its still like that.)

---

### Post by drs305 on 2012-01-21
Try editing the menuentry on the Grub menu:
Press 'e' to edit the highlighted entry.
Cursor to the end of the 'linux' line.
Remove "quiet splash" and add "nomodeset"
CTRL-x to boot.

If it boots to the Desktop, reinstall your video driver.

---

### Post by AmirM on 2012-01-21
> **drs305 said:**
> Try editing the menuentry on the Grub menu:
Press 'e' to edit the highlighted entry.
Cursor to the end of the 'linux' line.
Remove "quiet splash" and add "nomodeset"
CTRL-x to boot.

If it boots to the Desktop, reinstall your video driver.
tnx.
edit which option? normal or recovery?

---

### Post by drs305 on 2012-01-21
The normal entry.

---

### Post by AmirM on 2012-01-21
great.tnx,that worked fine.
desktop came up in low graphics,i removed that evil driver and now im back on my ubuntu.
but since i want to play on my ubuntu and i want to install a new driver for my graphic card i downloaded the latest driver few days ago.when using sh do install it is says X is running and I should stop it.
when I use alt+ctrl+F1 to F6 the screen freezes instead of giving me a command prompt.F7 will take it back to normal.
alt+ctrl+backspace does completely nothing.using stop gdm gives me a blank screen.
what should i do?
(should i make a new topic?)

---

### Post by drs305 on 2012-01-21
Is your driver or another driver available via normal methods? In Lucid, it would be:
System, Administration, Hardware Drivers.
Later versions: Dash Home (Upper Left), Additional Drivers and click the icon that appears.

You can wait and see if others respond here, but to get answers to video driver questions you are less likely to get them in a thread about not booting.

---

### Post by BC59 on 2012-01-21
Try this for installing the latest NVIDIA driver:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings 
```

---

### Post by AmirM on 2012-01-21
thanks.
@drs305:i know what you say but the driver which made me into this is the only driver there.

@BC59:
```
amir@amir-laptop:~$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: "Launchpad PPA for Ubuntu-X" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

```
amir@amir-laptop:~$ sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
nvidia-current set to manually installed.
nvidia-current-modaliases is already the newest version.
nvidia-settings is already the newest version.
nvidia-settings set to manually installed.
The following packages were automatically installed and are no longer required:
  libavutil49 polipo squid-common socat libreadline5 libstrongswan
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems

```

one new thing : from the low graphic mode(the way from grub which drs305 said) i can use stop gdm to stop X and go to console.I installed the latest driver which I downloaded few days ago (version 290.10) but the problem came back again,but this time i dont know how to unistall it.
how to uninstall the video card driver??
im planning to uninstall the driver and then use the code that BC59 gave me.

---

### Post by BC59 on 2012-01-21
If you don't have installed Synaptic, install it:

```
sudo apt-get install synaptic
```

Then open it --put your password and from the right Search (there are two) search for NVIDIA. The installed packages have a green square to their left. Choose with right click, complete removal. Then push Apply on the top.

---

### Post by BC59 on 2012-01-21
I just noticed that you have to run:

```
sudo apt-get autoremove
``` to clean the computer from some packages not installed.

And you have a problem to you sources.list

run a 

```
sudo apt-get update
``` and post the result.

---

