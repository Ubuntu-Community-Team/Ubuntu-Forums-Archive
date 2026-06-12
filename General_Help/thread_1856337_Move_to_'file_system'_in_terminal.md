---
title: "Move to 'file system' in terminal"
date: 2011-10-08
forum: General Help
---

### Post by einstein**-7 on 2011-10-08
In ubuntu 11.04 I'm having the stupid problems with videos not playing sometimes and other times they work fine and someone suggested reverting to the older 2.6.32 kernel fixed the issue but i'm a noob and can't seem to figure out how navigate to the 'file system' location and from there edit a readonly file as sudo.:(
 Thanks in advance.;)

---

### Post by dcstar on 2011-10-08
> **einstein**-7 said:**
> In ubuntu 11.04 I'm having the stupid problems with videos not playing sometimes and other times they work fine and someone suggested reverting to the older 2.6.32 kernel fixed the issue but i'm a noob and can't seem to figure out how navigate to the 'file system' location and from there edit a readonly file as sudo.:(
 Thanks in advance.;)

```
cd /
gksudo gedit *whatever*
```

---

### Post by F.G. on 2011-10-08
yeah, dcstar's method is exactly how to do it.

however what i do sometimes, (particularly if i'm copying multiple files from different locations and don't want to have to type out their paths all the time and don't like typing) is:
```
sudo nautilus

```
then you get a nautilus file browser window, with all the root privileges (and can edit permissions / open files and then they're open with the same privileges).

---

### Post by Morbius1 on 2011-10-08
I think you meant:
```
gksu nautilus
```
"sudo nautilus" will eventually corrupt your system.

---

### Post by F.G. on 2011-10-08
quite possibly.
I've always bandied sudo around without really thinking about it. do you have some more info about this? if so can you let me know? thanks.

---

### Post by collisionystm on 2011-10-08
> **Morbius1 said:**
> I think you meant:
```
gksu nautilus
```
"sudo nautilus" will eventually corrupt your system.

That is completely false.

Using sudo nautilus is OKAY

---

### Post by F.G. on 2011-10-08
can someone elaborate on why using sudo may or may not be a bad idea? thanks.

---

### Post by Morbius1 on 2011-10-08
@F.G., 
[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)
> **Graphical sudo**

 You should **never** use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on *Kubuntu*) to run such programs.  gksudo  sets HOME=~root, and copies .Xauthority to a tmp directory.  This  prevents files in your home directory becoming owned by Root.  (AFAICT,  this is all that's special about the environment of the started process  with gksudo vs. sudo). 

---

### Post by nothingspecial on 2011-10-08
Because if you open a graphical application with sudo you use configuration files in your home directory.

gksudo and kdesudo make the application use roots home.

If the ownership of some files in your home directory change to root bad things can happen.

**Edit - like it says above**

---

### Post by drofart on 2011-10-08
> **F.G. said:**
> can someone elaborate on why using sudo may or may not be a bad idea? thanks.
It is completely depend upon your nature of work. sudo mode will automatically exits after finishing an execution , so need not be worry about "sudo"
    recommended guide for beginner : linuxcommand.org

---

### Post by drofart on 2011-10-08
> **einstein**-7 said:**
> In ubuntu 11.04 I'm having the stupid problems with videos not playing sometimes and other times they work fine and someone suggested reverting to the older 2.6.32 kernel fixed the issue but i'm a noob and can't seem to figure out how navigate to the 'file system' location and from there edit a readonly file as sudo.:(
 Thanks in advance.;)
  You should try :
[COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#464646][FONT=verdana]1.) Add the kernel ppa and update your system:
sudo add-apt-repository ppa:kernel-ppa/ppa  sudo apt-get update2.) Check available kernels with the command:
apt-cache showpkg linux-headers[/FONT][/COLOR][/LEFT]
[/FONT][/COLOR]Now just install latest kernel available. 
Most probably you have to run this command:
sudo apt-get install linux-headers-2.6.38-11-generic-pae


Now remove all previous version through synaptic.
Hope it will fix non-responsive natty-narwhal as it did for me.

---

### Post by F.G. on 2011-10-08
> **Morbius1 said:**
> @F.G., 
[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)
thanks, this is some interesting reading. unfortunately I do tend to break things before looking at the documentation. I think i now understand the whole 'Ubuntu not having root password' thing and it's benefits.

---

### Post by Morbius1 on 2011-10-08
@F.G., 
> unfortunately I do tend to break things before looking at the documentationWe all do :)

> sudo mode will automatically exits after finishing an execution , so need not be worry about "sudo"Run a command requiring sudo - it will ask for a password.
After the command is executed run another command that requires sudo - you are not asked for a password.

sudo mode will not automatically exit after finishing an execution - it will eventually though.

Not sure how relevant it is when the "sudo mode" exits and whether or not you should sudo with a graphical utility ( especially something like Nautilus that also has control of part of the desktop ).

---

### Post by einstein**-7 on 2011-10-08
Thanks all! Now synaptic tries to load the maverick backport but it fails any ideas for the easiest way to get the 2.6.32 linux kernel image to be available assuming i don't have the cd :confused:?

---

