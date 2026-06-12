---
title: "Hash Sum Mismatch"
date: 2012-02-20
forum: General Help
---

### Post by NeonSamurai on 2012-02-20
This is driving me around the bend as it's happening on Lubuntu, Xubuntu and Ubuntu! All of my systems use 11.04, but I upgraded my Ubuntu laptop to 11.10 and still get the problem.
 
Basically I have three systems, my main being a media server running Xubuntu, which went down a few weeks ago so I tried a rebuild. All went well until I tried installing XBMC. At that point the installation failed with this message:

> Get:1 [http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/](http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/) natty/main xbmc-bin i386 2:11.0~git20120216.dbf9265-ppa2~natty [10.7 MB]
Get:2 [http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/](http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/) natty/main xbmc all 2:11.0~git20120216.dbf9265-ppa2~natty [22.3 MB]
Fetched 33.0 MB in 27s (1,189 kB/s)                                           
Failed to fetch [http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/pool/main/x/xbmc/xbmc-bin_11.0~git20120216.dbf9265-ppa2~natty_i386.deb](http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/pool/main/x/xbmc/xbmc-bin_11.0~git20120216.dbf9265-ppa2~natty_i386.deb)  Hash Sum mismatch
Failed to fetch [http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/pool/main/x/xbmc/xbmc_11.0~git20120216.dbf9265-ppa2~natty_all.deb](http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/pool/main/x/xbmc/xbmc_11.0~git20120216.dbf9265-ppa2~natty_all.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

*Note the alexandr-surkov reposity is one recommended by the XBMC team


The same thing happens when I try synaptic. It goes through the motions of installing XBMC then comes back with the same message.
 
Now I assumed that there might be some issue with my newly rebuilt Xubuntu machine, so I decided to try it out on my Viao laptop running Ubuntu. Different machine, same problem, even when I upgraded to 11.10. I also built another system from scratch using Lubuntu, again same problem. Each time on each machine 'hash sum mismatch' but only on XBMC.

So I tried using a different repository (as above), but it still happens with the same error. I then looked up hash sum mismatches and tried this:
 
#rm -f /var/cache/apt/partial/*
#rm -f /var/cache/apt/*.deb
 
But still the problem persists.
 
My media server runs a slimmed down version of Xubuntu, with only 4 other non-standard installations (Samba, openssh, Deluge and XBMC). The others install fine, but XBMC refuses to, possibly because it's a much larger download.
None of the machines (nor my router) have the firewall on for the installation of XBMC, although when it is on the other packages work fine.
 
Does anyone have any ideas, or is there another way I could install XBMC without using apt-get or synaptic? It has worked fine in the past, but over the past few weeks I get this.

Kind regards



Mark

---

### Post by matt_symes on 2012-02-20
Hi

Try these commands one after another.

```
sudo apt-get remove --purge xbmc
sudo rm /var/lib/apt/lists/*xbmc*
sudo rm /etc/apt/sources.list.d/*xbmc*
sudo apt-add-repository ppa:alexandr-surkov/xbmc
sudo apt-get update
sudo apt-get install xbmc
```

I have just installed in on precise (using oneiric repo; not sure how stable it will be...).

Kind regards

---

### Post by NeonSamurai on 2012-02-20
Hi Matt,

Thanks for that. I've run through your commands, but unfortunately I get the same hash sum mismatch. It's very annoying.

Anything else you can think of I can try?

Kind regards


Mark

---

### Post by matt_symes on 2012-02-20
Hi

Let's try something a bit more drastic and remove all the list cache.

```

sudo apt-get remove --purge xbmc
sudo rm -rf /var/lib/apt/lists/
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get install xbmc
```

Kind regards

---

### Post by NeonSamurai on 2012-02-21
Hi Matt,

Thanks for the reply. I gave it a try and annoyingly:

> Get:2 [http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/](http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/) natty/main xbmc all 2:11.0~git20120216.dbf9265-ppa2~natty [22.3 MB]
Fetched 33.0 MB in 28s (1,153 kB/s)                                           
Failed to fetch [http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/pool/main/x/xbmc/xbmc-bin_11.0~git20120216.dbf9265-ppa2~natty_i386.deb](http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/pool/main/x/xbmc/xbmc-bin_11.0~git20120216.dbf9265-ppa2~natty_i386.deb)  Hash Sum mismatch
Failed to fetch [http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/pool/main/x/xbmc/xbmc_11.0~git20120216.dbf9265-ppa2~natty_all.deb](http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu/pool/main/x/xbmc/xbmc_11.0~git20120216.dbf9265-ppa2~natty_all.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


But judging by the commands you gave me we've completely deleted any evidence of XBMC from my system (especially as the one I'm doing this on has never had XBMC successfully installed on it). 

Is there maybe a way to bypass the check sum?

Kind regards


Mark

---

### Post by matt_symes on 2012-02-21
Hi

It may be a problem with the repos. I installed it using Oneiric and not Natty.

I will set up Natty and try to install it and see if i get the same issue.

You have tried

```
sudo apt-get clean
```

before trying to install ? Not sure if it will hep in this case though.

Kind regards

---

### Post by NeonSamurai on 2012-02-23
Hi Matt,

Sorry to have wasted your time on this but the problem is actually my **Virgin Media** broadband account.

I tried to update my Nvidia drivers today (on a separate Windows 7 PC), downloaded the file, double clicked on the executable only to be told that the file was corrupted. So I tried again, and again and again. Same result each time. Apparently this happens quite a bit with **Virgin Media** broadband causing downloads to become corrupted.

So I installed my 3g broadband modem (not Virgin Media) and the download and installation worked first time. Looks like I'm one of many having this problem:

[http://community.virginmedia.com/t5/Wireless/Corrupt-downloads/td-p/29461]("http://community.virginmedia.com/t5/Wireless/Corrupt-downloads/td-p/29461")

So looks like I'll be trying to sort out the problem with **Virgin Media**, but thank you anyway for your help.

And for those of you having a similar problem accessing ubuntu updates, it might simply be because you're using **Virgin Media** broadband.

Kind Regards


Mark

---

### Post by matt_symes on 2012-02-24
Hi

Thanks for posting your solution. 

I use Virgin media myself so you may have headed off future problems for me.

I'm glad it's sorted as, when i install XMBC in 11.04, i had no problems. I have to be honest, this one had me scratching my head !

Kind regards

---

