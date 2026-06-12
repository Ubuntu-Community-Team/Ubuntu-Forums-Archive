---
title: "Installing software via Terminal (realplayer)"
date: 2009-11-11
forum: General Help
---

### Post by bobanshirl on 2009-11-11
I have got Ubuntu 9.10 installed alongside Windows XP and it is going ok.The problem I might have is that I am teaching myself how to use Ubuntu with a 2006 version of Beginning UBUNTU LINUX,which is a fine book but is everything in it relevant to this version of Ubuntu that I have installed.One thing that I am trying to do is install RealPlayer.I followed what the book said,ie,downloaded Realplayer which is an icon on my desk top.Then the book says to open a terminal and type 
 
                        chmod +x filename
                        sudo ./filename
now when I do this,replacing filename with RealPlayerSPGold.exe,I get command not found,or cannot access realplayer etc,or no such file or directory.If anyone out there can help me remember I have large L plates up.Many thanks.By the way I dont know what the tags are.

---

### Post by MichealH on 2009-11-11
Why dont you try;

```
sudo apt-get install realplayer
```

Also I noticed that you cant run .EXE files in Linux they are **_WINDOWS_** executables.

---

### Post by oldos2er on 2009-11-11
You need the *bin file, which you can get from [http://www.real.com/linux](http://www.real.com/linux)

---

### Post by bobanshirl on 2009-11-13
Hi there,thanks for your reply,I have the realplayer.bin file on my desktop.I have tried sudo apt-get install realplayer,I get,
Reading package lists....done
Building dependency tree
Reading state information....done
Package real player is not available but is referred to by another package.
This may mean that the package is missing,has been obsoleted or is only available from another source.
E: Package realplayer has no installation candidate.If you can make sense out of all this I would appreciate you pointing me in the right direction.I know it says I have been with Ubuntu since 2006 but because of all the hassle of finding things out I stopped using it and reverted to Windows XP.
Another thing is I said I was running Ubuntu 9.10 but in fact I am using ver 8.04.3.and am giving it another try.One other thing is what/where are the quick reply icons.

---

### Post by scouser73 on 2009-11-13
> **bobanshirl said:**
> I have got Ubuntu 9.10 installed alongside Windows XP and it is going ok.The problem I might have is that I am teaching myself how to use Ubuntu with a 2006 version of Beginning UBUNTU LINUX,which is a fine book but is everything in it relevant to this version of Ubuntu that I have installed.One thing that I am trying to do is install RealPlayer.I followed what the book said,ie,downloaded Realplayer which is an icon on my desk top.Then the book says to open a terminal and type 
 
                        chmod +x filename
                        sudo ./filename
now when I do this,replacing filename with RealPlayerSPGold.exe,I get command not found,or cannot access realplayer etc,or no such file or directory.If anyone out there can help me remember I have large L plates up.Many thanks.By the way I dont know what the tags are.

The commands used are still relevant for updated versions of Ubuntu and beyond.  All you need is to be careful if you are comparing the layout of an image from a book to that of the one on your screen as sometimes things may differ slightly, apart from that everything is good.

---

### Post by wojox on 2009-11-13
You need Medibuntu:

```
sudo wget http://www.medibuntu.org/sources.list.d/karmic.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by oldos2er on 2009-11-13
> **bobanshirl said:**
> Hi there,thanks for your reply,I have the realplayer.bin file on my desktop.I have tried sudo apt-get install realplayer

 apt-get only looks to the repositories for software. You'll need to enable the Medibuntu repository if you want to use apt-get.

 To install the *bin file you already downloaded, open a terminal and run these commands one at a time:
```
cd Desktop
chmod a+x RealPlayer11GOLD.bin
sudo ./RealPlayer11GOLD.bin
```
Once that's done, check the menus Applications, Internet (or Applications, Sound & Video--can't remember off hand where it creates a menu entry), and run Realplayer 11 to complete the install.

---

