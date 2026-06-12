---
title: "Offline updates"
date: 2010-03-12
forum: General Help
---

### Post by sandy8925 on 2010-03-12
I have a laptop with all updates and many extra programs already installed. I know the .debs are in /var/cache/apt/archives. I can copy them to the desktop where I want them to be installed. The main problem here is dependencies. Both aptoncd and keryx are useless in this case because I have the .debs anyway. I just need apt to have the package and dependency information and I know it will then install just fine. The problem is I just can't find out what files to copy over so that apt can find out all the package information and dependencies. The packages I want to install also include software from other repositories, such as wine,chromium etc. 

sudo dpkg -i *.deb does NOT help even with --force-depends. 

I don't want to put each package and it's dependencies in a separate folder and do them one-by-one as suggested in some how-to's because it's too time consuming.

---

### Post by ajgreeny on 2010-03-12
The deb files may be in /var/cache/apt/archives, but perhaps the dependencies are not.

However, you say you are putting the .deb files on your desktop, but do you mean on your desktop machine, or on the desktop of a machine with a GUI, eg gnome.  If you have a GUI, you should try synaptic, rather than ```
sudo dpkg -i *.deb
```as that will find all the dependencies that are in the cache.  I thought that dpkg would also do that, but perhaps not.  Synaptic following the use of aptoncd will certainly do this without a problem.  I know this as I have done it many times myself to avoid big downloads of masses of updates after installling a new version on two or three different machines.

---

### Post by sandy8925 on 2010-03-12
Ok let me clarify the situation.

I have a computer with internet access.I've installed lots of software and updates on it.I want to  be able to install all those software and updates(that is whatever I installed through apt or synaptic) on another computer that is not connected to the internet by just transferring the package files. I copied all the package files from /var/cache/apt/archives in the computer with internet access and put them in var/cache/apt/archives on the other computer. Doing dpkg -i *.deb didn't work. apt-get install <program-name> also does not work.

I'll try doing it through synaptic.

---

### Post by mac9416 on 2010-03-13
Hey sandy8925,

So you have one offline machine on which you've installed a lot of software - we'll call it Machine A. Now you want to install those same packages on other offline machines - Machine B, etc. Here's how:

**[SIZE=2]On Machine A:[/SIZE]**

[LIST=1]
[*]Copy the **/var/cache/apt/archives/** and **/var/lib/apt/lists/** directories onto a flash drive.
[*]Also get **/etc/apt/sources.list** and **/etc/apt/sources.list.d/**.
[/LIST]
**[SIZE=2]On Machine B:[/SIZE]**

[LIST=1]
[*] Paste those files into their respective locations (this will require root privileges).
[*]Run '**sudo apt-cache gencaches**'. This will force APT to read the files in /var/lib/apt/lists/ and know what packages are available.
[*]Run '**sudo apt-get install <package_names>**' to install any of the packages you've installed.
[/LIST]

I hope that makes some sense.  :)

By the way, Keryx 0.92.4 handles this process automatically with the new Install Packages tool. But it's not much harder to do it by hand since you already have the packages.

---

