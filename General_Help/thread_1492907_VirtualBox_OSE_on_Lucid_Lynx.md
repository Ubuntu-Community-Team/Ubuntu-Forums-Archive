---
title: "VirtualBox OSE on Lucid Lynx"
date: 2010-05-25
forum: General Help
---

### Post by sschafer on 2010-05-25
I installed VirtualBox OSE on Ubuntu 10.04.  When I try to start up a virtual machine I get 2 messages:

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {99404f50-dd10-40d3-889b-dd2f79f1e95e}

and a second later this pops up:
VirtualBox - Error in supR3HardenedMainInitRuntime
RTR3Init failed with rc=-1912 (rc=-1912)
Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.

virtualbox-ose-dkms IS installed:

dpkg -l | grep virtualbox
ii  virtualbox-ose                       3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - base binaries
ii  virtualbox-ose-dkms                  3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - kernel module 
ii  virtualbox-ose-qt                    3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - Qt based user 

vboxdrv is loaded:

modprobe -l vboxdrv
misc/vboxdrv.ko

I found many results when I googled this, but I haven't found any suggestions that work.  Quite often I see a suggestion to do this:

/etc/init.d/vboxdrv setup

however vboxdrv doesn't exist in /etc/init.d

One other thing:  I installed the PUEL version of VirtualBox before I installed the OSE version, however I completely removed it.  dpkg doesn't show it at all.  I've also completely removed and reinstalled the OSE version at least once.

I'd appreciate any suggestions as to h how I can get VirtualBox OSE to work.

---

### Post by gruvn on 2010-06-23
You're not crazy - I have the identical problem, including error messages as well as the fact that I installed (and removed) the PUEL version.

Can anyone help out?

---

### Post by 3Miro on 2010-06-23
Have you tried
```
sudo modprobe vboxdrv
```

If this doesn't help, you can check to see why /etc/init.d/vboxdrv is missing. I am using Virtual Box (non OSE) and I have that file.

---

### Post by anjoze on 2010-07-13
Hi.
I just opened synaptic and reinstall:
Virtualbox_ose
Virtualbox_ose-qt
Virtualbox_ose-dkms

It worked.

---

### Post by lombaardcj on 2010-09-01
Hi,

I've got  exactly what *sschafer* got on his first post dated "May 25th, 2010 03:17 PM"

 I downloaded
  [http://download.virtualbox.org/virtualbox/3.2.6/virtualbox-3.2_3.2.6-63112~Ubuntu~lucid_i386.deb]("http://download.virtualbox.org/virtualbox/3.2.6/virtualbox-3.2_3.2.6-63112%7EUbuntu%7Elucid_i386.deb")
 
Installed it without any error message.
 
Then I ran:
```
sudo /etc/init.d/vboxdrv setup
```

Output below:

```
chris@chris-laptop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for chris: 
 * Stopping VirtualBox kernel module done.
 * Removing old VirtualBox netadp kernel module
 * done.
 * Removing old VirtualBox netflt kernel module                                                                                               *   done.
 * Removing old VirtualBox kernel module                                                                                                      
*   done.
 * Recompiling VirtualBox kernel module 
 * done.
 * Starting VirtualBox kernel module
 *  done.

```

Their is no packages installed for virtual-box through Synaptic. (Have tried the full re-install but did not fix anything.)

Do I require any other packages to be installed or how do I get Virtual box running again.

Little disappointed that after upgrading my Ubuntu (which is recommended) Virtual-box is broken.

---

### Post by lombaardcj on 2010-09-01
Solved!

Sorry for bumping the thread.

Found my perfect solution at:

[COLOR=Blue][http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)[/COLOR]

I fixed my problem by adding the link to the packages from Sun for Virtual Box in Synaptic:

```
deb http://download.virtualbox.org/virtualbox/debian lucid non-free
```Add the Oracle public key for apt-secure can be downloaded [here]("http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc"). 
You can add this key with
```
sudo apt-key add oracle_vbox.asc
```Reload and run:

```
sudo apt-get install virtualbox-3.2
```This procedure will always install the latest available build not yet available through standard sources list

Now everything is working again! Lesson learnt

Just to be clear, I did not re-install ANY other package related to virtual box such as:
virtual-box-dkms etc for any other who have to go through the same

---

