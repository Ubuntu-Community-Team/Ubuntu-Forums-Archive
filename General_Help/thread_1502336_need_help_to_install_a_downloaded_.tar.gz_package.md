---
title: "need help to install a downloaded .tar.gz package"
date: 2010-06-05
forum: General Help
---

### Post by DrScum on 2010-06-05
after upgrading to 10.04 my wlan adapter is no longer working.
I figured out that this is probably caused by the absence of the linux firmware nonfree package.
I downloaded the package as .tar.gz file through another machine and copied it to the machine now running 10.04. How do I install the package?

---

### Post by Leppie on 2010-06-05
you most probably have to compile it, the package should contain a readme.txt or something similar with dependencies and instructions on how to install.

---

### Post by DrScum on 2010-06-05
Sorry, no readme.txt included. This is the linux firmware non free package. when extracted it contains two subfolders named "debian" and "firmware". I looked through the files but couldn't find any hint on how to compile.

I do know that I have to compile the package and I tried to follow several sets of instructions available on the internet but didn't succeed so far.

Do I have to be root to do this?
When I try to su to root I get the message "authentication failure" maybe that's the reason I din't succeed so far. I tried to get around the root problem with the sudo command.

---

### Post by drpjkurian on 2010-06-05
Hi
Usually there will be a readme text of possible commands required to install

well usually the command required are

```
cd filename[COLOR="Red"][/COLOR]
```

```
make && make install
```

red letters indicate folder name

These instructions are not exhaustive, they are the basic ones required to install. You may require few more commands to install, but I cant say without going through the readme text

---

### Post by drpjkurian on 2010-06-05
Hi
Usually there will be a readme text of possible commands required to install

well usually the command required are

```
cd [COLOR="Red"]filename[/COLOR]
```

```
make && make install
```

red letters indicate folder name

These instructions are not exhaustive, they are the basic ones required to install. You may require few more commands to install, but I cant say without going through the readme text

oops it got repeated

---

### Post by Leppie on 2010-06-05
> **DrScum said:**
> Sorry, no readme.txt included. This is the linux firmware non free package. when extracted it contains two subfolders named "debian" and "firmware". I looked through the files but couldn't find any hint on how to compile.
not sure which package you're talking about, but if you provide the link we can have a look at it.

> **DrScum said:**
> I do know that I have to compile the package and I tried to follow several sets of instructions available on the internet but didn't succeed so far.

Do I have to be root to do this?
When I try to su to root I get the message "authentication failure" maybe that's the reason I din't succeed so far. I tried to get around the root problem with the sudo command.
normally when compiling, you would change to the folder created when unpacking the archive, then issue the following commands:
```
./configure
make
sudo make install
```
this, however would not update the synaptic/apt/dpkg/aptitude database. you can use checkinstall for this.
```
sudo apt-get install checkinstall
```
the last command would then be:
```
sudo checkinstall -d make install
```
this will create a .deb package (handy for future use) and install it.

---

### Post by davidmohammed on 2010-06-05
> **DrScum said:**
> after upgrading to 10.04 my wlan adapter is no longer working.
I figured out that this is probably caused by the absence of the linux firmware nonfree package.
I downloaded the package as .tar.gz file through another machine and copied it to the machine now running 10.04. How do I install the package?

before you go ahead - look at your system kernel log.  There should be errors at the end that relate to your wlan - please post them here.  It should give a hint on what the issue is.  sometimes it just a case of downloading the firmware rather than having to install extra packages.

Also, can you confirm the exact wireless card you are using - 

lspci from a terminal.

---

### Post by bodhi.zazen on 2010-06-05
What wireless card is it ?

I suggest you search google for a solution first.

What did you download from where ? It could be most anything from a binary to an install script to source code to a patch, so hard to give you specific instructions without further details.

---

### Post by DrScum on 2010-06-06
I downloaded the package from here:
[http://packages.ubuntu.com/karmic/linux-firmware-nonfree](http://packages.ubuntu.com/karmic/linux-firmware-nonfree)
which to me seems to be a trusted source
the package provides firmware and was included in the previous version 9.04 with 9.04 the very same  wlan card worked "out of the box".

The chipset in ubuntu is identified as Intersil Corp. ISL 3890 (PrismGT/PrismDuette)/ISL3886 (Prism Javelin/PrismXbow) rev.01

As I said, I couldn't find a readme.text in the extracted folders.

---

### Post by davidmohammed on 2010-06-06
you dont need to compile anything for that.  

Suggest using synaptic and search for package linux firmware nonfree

install it.  It should fix your wlan issue.

---

### Post by DrScum on 2010-06-06
well, I tried that:
copied downloaded package from USB stick
extracted it
opened synaptic package mgr
selected "add downloaded package"
browsed to the folder with the extracted files
non of the directories nor single files were recognized as packages, everything was greyed out

---

### Post by realzippy on 2010-06-06
[http://mirror.informatik.uni-mannheim.de/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.8_all.deb](http://mirror.informatik.uni-mannheim.de/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.8_all.deb)

here it is as .deb file,just click it.

---

### Post by Soul-Sing on 2010-06-06
.tars without a readme and a  proper uninstall should be ignored.

---

### Post by DrScum on 2010-06-06
Thanks a bunch realzippy! Your post did the trick. Did you create the .deb yourself? Or did you get it on the net? I tried to find a .deb but didn't succeed.

Anyway, thanks.

---

### Post by realzippy on 2010-06-06
> **DrScum said:**
> Thanks a bunch realzippy! Your post did the trick. Did you create the .deb yourself? Or did you get it on the net? I tried to find a .deb but didn't succeed.

Anyway, thanks.


...did a google search:

*linux-firmware-nonfree .deb*

---

