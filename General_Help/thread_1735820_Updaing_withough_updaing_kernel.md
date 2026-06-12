---
title: "Updaing withough updaing kernel?"
date: 2011-04-21
forum: General Help
---

### Post by garrett228 on 2011-04-21
I have a 3dsp pci wifi card, and the last kernel it supports is Ubuntu 10.04 2.6.32-(21-24) I want to update but dont want to accidentally update the kernal. Any advice guys?

---

### Post by drs305 on 2011-04-21
> **garrett228 said:**
> I have a 3dsp pci wifi card, and the last kernel it supports is Ubuntu 10.04 2.6.32-(21-24) I want to update but dont want to accidentally update the kernal. Any advice guys?

If you are just talking about updating packages in Maverick, you can 'lock' the kernel in Synaptic/Update Manager and/or via the command line.

For Synaptic: Type 2.6.32- in the upper right search bar. The kernels and headers should appear. CTRL-click on any package you don't want updated, then from the top menu: Package > Lock Version

I would also 'pin' the kernel via the Command Line with the following command:
```
sudo -i
echo '<package_name> hold' | dpkg --set-selections		
exit

```	


To Unlock a package in Synaptic, reverse the procedure.

To remove a hold from the terminal: 
```
sudo -i 
echo  <package_name> install | dpkg &#8211;set-selections
sudo apt-get update && sudo apt-get upgrade
exit
```

In my experience, the Synaptic lock will not prevent a command line update, and vice versa. I don't know if that's how it's meant to be, but I do both CLI and Synaptic to make sure nothing updates the package.

---

### Post by garrett228 on 2011-04-21
> **drs305 said:**
> If you are just talking about updating packages in Maverick, you can 'lock' the kernel in Synaptic/Update Manager and/or via the command line.

For Synaptic: Type 2.6.32- in the upper right search bar. The kernels and headers should appear. CTRL-click on any package you don't want updated, then from the top menu: Package > Lock Version

I would also 'pin' the kernel via the Command Line with the following command:
```
sudo -i
echo '<package_name> hold' | dpkg --set-selections		
exit

```	


To Unlock a package in Synaptic, reverse the procedure.

To remove a hold from the terminal: 
```
sudo -i 
echo  <package_name> install | dpkg –set-selections
sudo apt-get update && sudo apt-get upgrade
exit
```

In my experience, the Synaptic lock will not prevent a command line update, and vice versa. I don't know if that's how it's meant to be, but I do both CLI and Synaptic to make sure nothing updates the package.

What packages do i need to lock exactly? :/ I have nooo clue there is ALOT of packages

---

### Post by drs305 on 2011-04-21
> **garrett228 said:**
> What packages do i need to lock exactly? :/ I have nooo clue there is ALOT of packages

Well, you can start by seeing which kernel you are currently running:
```
uname -r
```
You would most likely want to lock that kernel and headers. So if you wanted to lock 2.6.32-24 (and perhaps a spare 2.6.32-23) you would select linux-image-2.6.32-24 (and linux-image-2.6.32-24-generic) and the same version of "linux-headers-2.6.32-24" and "linux-headers-2.6.32-24-generic". Only those with a green tick box are currently installed.

There is another way to use a specific kernel. Since Ubuntu won't uninstall an older kernel without your consent, you could allow the system to install newer kernels but force Grub2 to always use a specific kernel.

Get a list of your current menu entries in Grub2:
```
grep menuentry /boot/grub/grub.cfg
```

Open this file for editing as root:
```
gksu gedit /etc/default/grub
```

Find the kernel you *always* want to boot from the first command. In gedit, change:
> GRUB_DEFAULT=0
# to
GRUB_DEFAULT="Enter the exact title between the quotes from the grep results"

Example:
GRUB_DEFAULT="Ubuntu, with Linux 2.6.38-8-generic"

Update the Grub2 menu:
```
sudo update-grub
```

The only warning is that if the Grub2 package is updated (not with update-grub but with a new grub-pc package), you would have to make sure to reset the GRUB_DEFAULT entry. (You could lock grub-pc from updating if you wanted ;-) ).

Is your head spinning yet?  Perhaps someone else can explain it a bit more simply or provide an easier solution.

---

