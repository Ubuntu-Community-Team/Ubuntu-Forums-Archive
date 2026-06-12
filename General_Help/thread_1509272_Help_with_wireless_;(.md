---
title: "Help with wireless ;("
date: 2010-06-14
forum: General Help
---

### Post by OpressedCalamity on 2010-06-14
Hey guys, I just recently upgraded from 9.04 to 9.10.
Booting into 9.10, My wireless did not work and I was not able to connect to any wireless networks. None would even show up, So I rebooted and I noticed after grub loaded, IT gave me 3 seconds to press escape and enter a menu
You proboly know whats in the menu 
It gave me a choice to boot ubuntu And ubuntu fail safe.
And below that it had duplicate choices I chose the one on thebottom that seems to be a earlier kernal and wireless works
Sorry if i don't make sense, Just ask i can provide with more detail.
I really am A idiot ^^
Thanks in advanced
I use a wireless usb 150n adapter.

---

### Post by OpressedCalamity on 2010-06-14
Forgot to add somthing :D
I am looking to get ubuntu to choose the version with the earlier kernal or whatever.

---

### Post by Crafty Kisses on 2010-06-14
Hello, 

Everyone has to start somewhere. In reguards to your problem, I need a bit more information and some outputs. I'm thinking a possible update you took could have made the wireless stop working, but let's see check a couple of things first here before we jump to any conclusions.

First open up your terminal **(Applications->Accessories->Terminal)** then run the following commands in the terminal:
```
lspci
lsusb
lshw -C network
```

That will tell me more information about your network setup and what not, the only reason I think an update has made the wireless stop working is because you said it works under the older kernel, so we will see if we can get to the bottom of this and hopefully solve the issue.

---

### Post by OpressedCalamity on 2010-06-15
Please disregard this thread and help me with this issue please
[http://ubuntuforums.org/showthread.php?p=9462523#post9462523](http://ubuntuforums.org/showthread.php?p=9462523#post9462523)

---

