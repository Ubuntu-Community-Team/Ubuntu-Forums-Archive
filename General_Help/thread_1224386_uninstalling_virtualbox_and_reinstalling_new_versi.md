---
title: "uninstalling virtualbox and reinstalling new version?"
date: 2009-07-27
forum: General Help
---

### Post by jake16424 on 2009-07-27
im running the new mint 7 gloria, 

tried using STEAM in my windows machine but it wont launch any games after i finally got it to run. all i want to do is play a few games from steam any suggestions other than virtualbox or wine? both fought me tooth and nail to run

---

### Post by hibliss on 2009-07-27
You question doesn't seem to have a lot to do with the thread title.


If you want to install the new version of Virtualbox, go to Sun's website and add their repository, then

```
sudo apt-get install virtualbox-3.0
```

---

### Post by jake16424 on 2009-07-27
> **hibliss said:**
> You question doesn't seem to have a lot to do with the thread title.


If you want to install the new version of Virtualbox, go to Sun's website and add their repository, then

```
sudo apt-get install virtualbox-3.0
```

well yes it does, i want to install virtual box, and i want to game, if there is another app that will let me game i still need to UNINSTALL virtual box to upgrade it or replace it.

how do i uninstall virtual box? =(

thanks for the prompt reply!

---

### Post by jake16424 on 2009-07-27
simply, how do i uninstall virtual box so i can reinstall the new 3.0 version?

---

### Post by hibliss on 2009-07-27
> **hibliss said:**
> 
If you want to install the new version of Virtualbox, go to Sun's website and add their repository, then

```
sudo apt-get install virtualbox-3.0
```

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

All of this is doen in terminal, or after you add the repo, you can use your package manager.

Add the repo for whatever version of Ubuntu that you are using, for Jaunty, it would be:

```
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free

```

Then add the public key:

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

```

Then install:

```
apt-get install virtualbox-3.0

```

If you have a previous version installed when you giv ethe command to install the new version, it will remove it automatically. Installing from the repo is your best solution because it assures you get the needed updates and makes updating to new versions much easier.

---

### Post by jake16424 on 2009-07-27
> **hibliss said:**
> [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

All of this is doen in terminal, or after you add the repo, you can use your package manager.

Add the repo for whatever version of Ubuntu that you are using, for Jaunty, it would be:

```
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free

```

Then add the public key:

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

```

Then install:

```
apt-get install virtualbox-3.0

```

If you have a previous version installed when you giv ethe command to install the new version, it will remove it automatically. Installing from the repo is your best solution because it assures you get the needed updates and makes updating to new versions much easier.

im running mint 7, this should work then? thank you for answering my ? =)

---

### Post by hibliss on 2009-07-27
Mint is Ubuntu with a bunch of non-free software and bloat when you install it.

Just like Ubuntu is Debian-based, Mint is Ubuntu-based. Adding a repo should be exactly the same, and so should updates. 

I have never used Mint except in Virtual machine, and it wasn't for long, but yes, I assume it will work just fine. Why don't you try it?

---

### Post by jake16424 on 2009-07-27
> **hibliss said:**
> Mint is Ubuntu with a bunch of non-free software and bloat when you install it.

Just like Ubuntu is Debian-based, Mint is Ubuntu-based. Adding a repo should be exactly the same, and so should updates. 

I have never used Mint except in Virtual machine, and it wasn't for long, but yes, I assume it will work just fine. Why don't you try it?

at work ATM haha,, i will when i get home, ok thank you for all your help!

---

### Post by jake16424 on 2009-07-27
> **hibliss said:**
> Mint is Ubuntu with a bunch of non-free software and bloat when you install it.

Just like Ubuntu is Debian-based, Mint is Ubuntu-based. Adding a repo should be exactly the same, and so should updates. 

I have never used Mint except in Virtual machine, and it wasn't for long, but yes, I assume it will work just fine. Why don't you try it?

fail

 deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free
bash: deb: command not found
jacob@the ~ $ deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-freemint
bash: deb: command not found
jacob@the ~ $ apt-get install virtualbox-3.0
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jacob@the ~ $

---

### Post by hibliss on 2009-07-27
You have to add the first command through software sources, did you click the link to go to the Virtualbox page that details install instructions? Here is the link again:

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

You have to edit this file - /etc/apt/sources.list

You also skipped adding the public key.

---

### Post by jake16424 on 2009-07-27
> **hibliss said:**
> You have to add the first command through software sources, did you click the link to go to the Virtualbox page that details install instructions? Here is the link again:

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

You have to edit this file - /etc/apt/sources.list

You also skipped adding the public key.


i tried giogn to wiki, for some reason my AMD PHENOME PROCESSOR wont work in linux, but its working now? in anycase EVERYTHING X86 or whatever wont run, says fail to run 64bit something or other and i need to download drivers from AMD.com but i can't cause there not there.

adding the public key failed.

---

### Post by jake16424 on 2009-07-27
just uninstalled an installed new virtual box 3.0 so thread closed, it should work if not at least i know how to uninstal and install the old one.

thanks guys\girls

---

