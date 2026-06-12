---
title: "Upgrade to firefox 4.0 the easy and safe way"
date: 2011-03-22
forum: General Help
---

### Post by jeremy on 2011-03-22
Firefox Stable PPA provides the latest Firefox stable builds for Ubuntu 9.10, 10.04 and 10.10.

This repository that provides the latest Firefox 4.0 stable.

Add the PPA using these commands:

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update


Then if you have Firefox installed, you will get an update for the latest Firefox 4, the package name isn't named "firefox-4.0" like it is now in the Mozilla Daily PPA but simply "firefox", so it is simply a case of updating.

I have done this and it works perfectly.

---

### Post by 5149.5 on 2011-03-22
How do you get past the error caused by the connection being refused by the ubuntu keyserver?

---

### Post by lithopsian on 2011-03-22
[Instructions](https://launchpad.net/~mozillateam/+archive/firefox-stable) for adding keys.

---

### Post by kabloink on 2011-03-22
It's also quite safe to download it from the firefox site and extract it to your home directory. Creating a application launcher on your toolbar, pointing it to /home/username/firefox/firefox.

The benefit of doing it this way is that you are able to have both the old and new versions. Which is a consideration if you want to make sure that the new version is compatible with everything you use it for.

---

### Post by 5149.5 on 2011-03-22
> **lithopsian said:**
> [Instructions]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable") for adding keys.

I guess I'm confused. My system already knows about the EC21 key. 

gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection refused

What information would I be entering? The information on your link indicates that the EC21 key would have to be entered manually for a pre 9.10 system but no manual entry should be required for my 10.10 system.

---

### Post by wilee-nilee on 2011-03-22
> **kabloink said:**
> It's also quite safe to download it from the firefox site and extract it to your home directory. Creating a application launcher on your toolbar, pointing it to /home/username/firefox/firefox.

The benefit of doing it this way is that you are able to have both the old and new versions. Which is a consideration if you want to make sure that the new version is compatible with everything you use it for.

You can have both versions without downloading from Mozilla. The ppa's not sure about this one are not upgrades previously at least.

Edit I did put this ppa in the apt list and it did upgrade the 3 to 4 in maverick, with no problems.

---

### Post by jeremy on 2011-03-23
> **wilee-nilee said:**
> You can have both versions without downloading from Mozilla. The ppa's not sure about this one are not upgrades previously at least.

The method I posted at the start of this thread is for upgrading, ie. replacing, firefox 3.6 with firefox 4.0

---

### Post by jeremy on 2011-03-23
> **5149.5 said:**
> How do you get past the error caused by the connection being refused by the ubuntu keyserver?

I had no error, perhaps it is a temporary problem with the keyserver.

---

### Post by RabbitWho on 2011-03-23
I did it as explained here: [http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/](http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/) and have the following problems:

It's in English. It refuses to swap to Spanish, I've tried the Argentinian and Spain Spanish XPIs and they've gone in and been installed and i can see the language packs under "apps" but the language is still English.

There are too many dictionaries. I have to swap between Spanish, Czech and English spell checkers and now I have to go through a list of something like 15 different varieties of English when I'm trying to swap. 
The varieties of English are not included in the add-on page the way the ones I chose to install are. I tried looking for the dictionaries folder to delete them manually, as was suggested on this site a few years ago, but maybe I'm blind or I they've changed the name but I can't see them. 

Sitting on ff3 while I wait :)

---

### Post by RabbitWho on 2011-03-25
Argh. Firefox 4 all my spell checkers and the ability to save tabs in Firefox 3. So now I'm stuck with 2 terrible browsers.

---

