---
title: "Installing Skype on Ubuntu using Terminal at the start"
date: 2010-06-29
forum: General Help
---

### Post by Abu Azzubair on 2010-06-29
Thanks to [Noz3001]("http://ubuntuforums.org/member.php?u=847752")'s link:

[http://www.skype.com/intl/en-gb/get-...omputer/linux/]("http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/")

I clicked on "Download now"

Right-click [Ubuntu 8.10+ 32-bit]("http://www.skype.com/go/getskype-linux-beta-ubuntu-32")             (since my system is a 32-bit system), then Copy Link Location

Note: to find out if you have a 64-bit or a 32-bit system, you would put that into Terminal
```
uname -m
```If you get
```
i686
```Then that means that you have a 32-bit system

If you get
```
i686-64
```Then that means you have a 64-bit system

____________________________________

So then, lets continue from where we left off

Then ctrl+alt+T (or Applications, Accessories, Terminal)

Then type this into Terminal
```
wget
```Press the space bar, then right-click on Terminal, then click Paste

Hit "Enter"

You will see that Terminal is downloading Skype O:)

But we still never finished yet :biggrin:

Go Places, then Home Folder

You will see a file called "skype-ubuntu-intrepid_2.1.0.81-1_i386.deb"

Double-click on it

Package Installer will appear

Click Intall

After it finishes loading - we have Skype :mrgreen:

To see where our new Skype is, we go to Applications, Internet, Skype

Done :arrow:

---

### Post by Bucky Ball on 2010-06-29
Or you could go System->Administration->Synaptic Package Manager, do a search for Skype, tick to install, click apply and your done. ;) It's in the repos.

---

### Post by Abu Azzubair on 2010-06-29
Phew

Thanks a lot Lol

---

