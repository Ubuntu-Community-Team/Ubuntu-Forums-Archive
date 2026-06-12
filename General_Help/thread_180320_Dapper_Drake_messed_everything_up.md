---
title: "Dapper Drake messed everything up"
date: 2006-05-22
forum: General Help
---

### Post by jonnyfive on 2006-05-22
A whole bunch of stuff on my system is out of whack.

1. Amorak and any other sound player doesn't play through the speakers anymore but it does play through the headphone jack
2. I can't find sound control to try and fix it.
3. When I do update manager it tells me 
```
Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.
```
4. My wireless no longer works.
5. My cd tray won't eject when I press the button.

It could be because of my sources or whatever because some timed out during the upgrade.
Is it possible for someone with a sources list that works to list it for me so I can put it in mine and try again?

---

### Post by K.Mandla on 2006-05-22
I usually build mine off the [source-o-matic]("http://www.ubuntulinux.nl/source-o-matic"). I can still post one if you like. I just did a dist-upgrade on my Dapper Xubuntu system and it went fine.

---

### Post by jonnyfive on 2006-05-22
Yes, Please I would appreciate that

---

### Post by K.Mandla on 2006-05-22
No problem at all. Note that these are tied to the US Dapper repos.

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```
Hope that helps! :)

---

### Post by jonnyfive on 2006-05-22
What do I do about this problem?

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

How do I find out which software needs to be removed and how do I remove it.

---

### Post by Sef on 2006-05-22
From the command terminal try this:

sudo apt-get update

sudo apt-get ubuntu-base ubuntu-desktop

sudo apt-get dist-upgrade

I had some problems dist-upgrading to Dapper, and those commands solved it for me.

---

### Post by K.Mandla on 2006-05-22
My instinct says to go ahead and dist-upgrade, but I don't know if that sounds appealing to you. I'd make sure everything was backed up, and then give it a shot. I think the package manager will correct most of those things when it does the upgrade. :rolleyes:

---

### Post by jonnyfive on 2006-05-22
When I try to 
sudo apt-get ubuntu-base ubuntu-desktop

I get this error
E: Invalid operation ubuntu-base

---

### Post by K.Mandla on 2006-05-22
I'm guessing that should be *sudo apt-get install ubuntu-base ubuntu-desktop*.

---

