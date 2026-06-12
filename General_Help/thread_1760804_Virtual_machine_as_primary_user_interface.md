---
title: "Virtual machine as primary user interface"
date: 2011-05-17
forum: General Help
---

### Post by 2badgersblue on 2011-05-17
Summary:
Automatically run a virtual machine (Windows XP) as the main user interface on machine startup.

I've been playing with this for a few days now and I think I need help - technical and mental :>
I want to set up a Ubuntu (or other Linux) machine that is as clean as possible. This will have the sole purpose of running VirtualBox (or other) with one virtual machine.
The user of this machine will see the following:
Start the machine, Ubuntu boots, X starts, Windows XP starts running as virtual machine. User is not asked for username or password in Linux. Windows XP is the only 'interface' the user should be able to access. When VM is closed the host machine shuts down too. As far as user is concerned XP is the only OS running - apart from slightly extended boot time and two boot splash screens.

I have got to the point of having a Ubuntu server boot, manual login, issue command 'xinit', issue command 'VBoxManage startvm XP'. I know there are switches to make it full screen, remove menus etc, just trying to keep it simple for testing.

The sole point of this is to have a kiosk type machine that discards all changes on each reboot. I know how to configure VBox disks to do this, it's the other details I'm hazy on.
This is close:
[http://www.quicktweaks.com/2008/10/14/run-your-virtual-os-directly-from-gdm-in-ubuntu/](http://www.quicktweaks.com/2008/10/14/run-your-virtual-os-directly-from-gdm-in-ubuntu/)
But it seems to be for an older distro and I would need it to auto logon to the X session.

I can ssh in from another machine to do config changes and swap in and out virtual machines for different purposes.

Any ideas? Big ask I know.

---

### Post by mlentink on 2011-05-17
Why use X at all?

See here: [http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-10.10-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-10.10-server)

---

### Post by 2badgersblue on 2011-05-18
Because I'm thinking that X may be useful to allow the local user to use the Windows guest machine?
This machine is to appear like it's running Windows natively i.e. Windows on the attached display.

If I had a budget bigger than the price of coffee I could use VMWare ACE or similar. As I don't I'd like to use free resources.

We have public access PCs. At the moment we use Windows XP with MS Steady State and Disk Protection turned on. Resets the machine to preconfigured state on each reboot - no matter what the user has done.
Windows 7 no longer supports this feature.
The other advantage of using VBox or VMWare is it's hardware independence. Once I have an image set up I can copy it to any hardware running VBox or VMWare.

---

