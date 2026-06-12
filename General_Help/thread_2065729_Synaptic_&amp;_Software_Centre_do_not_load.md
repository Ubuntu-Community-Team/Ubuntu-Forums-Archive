---
title: "Synaptic &amp; Software Centre do not load"
date: 2012-10-02
forum: General Help
---

### Post by Jonners59 on 2012-10-02
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-31-generic
GNOME 3.4.2
AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ × 2 

On my wife's PC.  When trying to start Software Centre is fails to start.  Synaptic fails with the following message.

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/opensync.gforge.punktart.de_repo_opensync-0.21_dists_sid_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

I have had this issue for a while and found some command instructions to try.  They work for a couple of days then fail again.  Need to fix this.

  	 	 	 	 	 	    [COLOR=#333333][SIZE=4]Synaptics won't load[/SIZE][/COLOR]
  [COLOR=#333333][SIZE=2]might be a borked index

sudo rm /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get autoclean

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a[/SIZE][/COLOR]

---

### Post by thatguruguy on 2012-10-02
> **Jonners59 said:**
> Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-31-generic
GNOME 3.4.2
AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ × 2 

On my wife's PC.  When trying to start Software Centre is fails to start.  Synaptic fails with the following message.

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/opensync.gforge.punktart.de_repo_opensync-0.21_dists_sid_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```I have had this issue for a while and found some command instructions to try.  They work for a couple of days then fail again.  Need to fix this.

                                   [COLOR=#333333][SIZE=4]Synaptics won't load[/SIZE][/COLOR]
  [COLOR=#333333][SIZE=2]might be a borked index

sudo rm /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get autoclean

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a[/SIZE][/COLOR]

What are you using that particular repository (the opensync.gforge.punktart.de_repo_opensync-0.21_dists_sid_main_binary-amd64_Packages repo) for?  Are you using it for opensync? Is it even still maintained?

---

### Post by Jonners59 on 2012-10-02
In truth, I do not know.  I do not understand the message at all...

What do you suggest?

---

### Post by thatguruguy on 2012-10-02
> **Jonners59 said:**
> In truth, I do not know.  I do not understand the message at all...

What do you suggest?

I suggest removing the repository.

```
sudo gedit /etc/apt/sources.list
```

Look for the line containing that repository, and remove it.  The try
```
sudo apt-get update
```
again, and see what errors are reported.

---

### Post by Jonners59 on 2012-10-02
Good, seems to have fixed...  though I got error messages in the apt-get update...  Get:49 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en [82.7 kB] Fetched 2,431 kB in 5s (481 kB/s)                                    W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages)  404  Not Found [IP: 195.10.11.10 80]  E: Some index files failed to download. They have been ignored, or old ones used instead.  And I also had a string of Error Report messages, but they seemed to have stopped.

---

### Post by thatguruguy on 2012-10-02
> **Jonners59 said:**
> Good, seems to have fixed...  though I got error messages in the apt-get update...  Get:49 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en [82.7 kB] Fetched 2,431 kB in 5s (481 kB/s)                                    W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages)  404  Not Found [IP: 195.10.11.10 80]  E: Some index files failed to download. They have been ignored, or old ones used instead.  And I also had a string of Error Report messages, but they seemed to have stopped.

Remove anything that says "hardy"; you're running 12.04 and 1) the hardy repositories don't apply, and 2) the hardy repositories haven't been maintained for years now. Do it the same way you removed the other repository.

You can also remove the skype repository, since skype is included by default in Ubuntu. You should be good to go after that.

---

### Post by Jonners59 on 2012-10-06
Seems to be working nicely now...  Cheers "thatguruguy"...

---

