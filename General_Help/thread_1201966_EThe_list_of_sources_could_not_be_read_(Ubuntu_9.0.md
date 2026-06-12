---
title: "E:The list of sources could not be read (Ubuntu 9.04 - the Jaunty Ja)"
date: 2009-07-01
forum: General Help
---

### Post by mrsmid on 2009-07-01
Hi everybody, first than all; I'm really new with ubuntu. I got tired of Windows, so, I decided to install Ubuntu.
Well, so far everything it's good, but installing and upgrading some things I did some wrong things (...)

Everytime when I try to open the "Update Manager"; I have this problem: 'An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:Type 'sudo' is not known on line 3 in source list /etc/apt/sources.list.d/shikicolors.list, E:The list of sources could not be read.''

(I checked the post **"[the list of sources could not be read]("http://ubuntuforums.org/showthread.php?t=487554")"** that is similar to my problem)

Based in the post, I did executed this command:
```
gksudo gedit /etc/apt/sources.list.d/shikicolors.list
```this is the content:
```

deb http://ppa.launchpad.net/vicox/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/vicox/ppa/ubuntu jaunty main
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 53FFCC28 && sudo apt-get update

```Can you help me with this??!?!?! So!... How can I resolve it?!?!?!
(another thing... I don't speak english... only some few words...)

:cool: Thnks!!!!

---

### Post by VCoolio on 2009-07-01
The line "sudo apt-key" etc is wrong. That should not be in the file, it is a command that you need to execute in the terminal. It imports the key for the repository. Delete that line from the file and then run it in a terminal. 

btw: welcome to ubuntu

---

