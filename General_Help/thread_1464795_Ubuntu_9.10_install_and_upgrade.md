---
title: "Ubuntu 9.10 install and upgrade"
date: 2010-04-28
forum: General Help
---

### Post by shipinomore on 2010-04-28
I am a newbie and lost in Ubuntu. I use to use Suse and Fedora.
OK I have installed 9.10 many times and it seems to stall or freeze when loading Language. stalls at different time left on the install and I SKIP it and it seems to finish ok. then today several times I did the ALT F2 and did an upgrade to 10.04 LTS and it got down to 3 minutes and got a message about continue without GRUB well I know you cannot boot without GRUB but it will not proceed without it. 
Hopefully tomorrow we will be able to download the new versions but I cannot find out if I should get up in the middle of the night and start the bittorrent downloads.
Any advice out there from anyone Please?
Larry

---

### Post by cariboo on 2010-04-28
Moved to General Help.

You can skip the extra language packs when installing without doing any harm, if you find you need them, they can always be installed later.

If at some point your upgrade fails, don reboot, until the erros have been fixed. I had this happen a couple of times, what I do is open a terminal and type:

```
sudo apt-get -f install
```

after that command has finished, in the same terminal type:

```
sudo aptitude update && sudo aptitude -y safe-upgrade
```

Once the above has finished, you should be able to boot to your brand new desktop.

---

