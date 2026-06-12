---
title: "Weird update problem"
date: 2011-09-27
forum: General Help
---

### Post by Condor Cluster on 2011-09-27
I've been trying to update my Lucid netbook recently using Ubuntu Tweak, but it's not working.

It finds a couple of updates, which I tick all, then update, after which I get the following message:

[I]Could not apply changes!
Fix broken packages first.[/I]

Seems to do the same if I update using Ubuntu's default update manager too :(

Any ideas?

Thanks.

---

### Post by Krytarik on 2011-09-27
Run these commands in the Terminal and if it doesn't work after that, post their outputs (in code tags please, use the #-button in the editor):
```
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get upgrade
```
Hope it works!

---

### Post by Condor Cluster on 2011-09-27
I've done a little experimenting, and I managed to install all but one update using Ubuntu's own Update manager.

The offending update is libxvidcore4.

I think that was under a custom vlc ppa, some I'm guessing the problem is in the repo, not my system?

Cheers.

---

### Post by Condor Cluster on 2011-09-28
Should I just wait to see if this will repair itself, or is there anything I can do?

Thanks again.

---

### Post by sarang031705 on 2011-09-28
This appears everytime I update


W: GPG error: [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Frogs Hair on 2011-09-28
> **sarang031705 said:**
> This appears everytime I update


W: GPG error: [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

Please start your own thread !

---

### Post by Krytarik on 2011-09-28
> **Condor Cluster said:**
> Should I just wait to see if this will repair itself, or is there anything I can do?
Well, yeah, you could do so. Without any more details, I can only say that I, too, had an apparently similar issue a while back, with the VLC PPA.

But you could also post the error messages, as initially requested.

---

### Post by Krytarik on 2011-09-28
> **sarang031705 said:**
> This appears everytime I update


W: GPG error: [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
Try this for a start, and if this doesn't fix your issue, please start your own thread, as already suggested by *Frogs Hair*:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```Greetings.

UPDATE: Please see this, just done, post: [http://ubuntuforums.org/showthread.php?p=11293218#post11293218](http://ubuntuforums.org/showthread.php?p=11293218#post11293218)

---

### Post by Condor Cluster on 2011-09-28
Okay, I tried to update via terminal this time, to get a better error message. Note all other updates seem to install fine apart from this one sucker.

[I]The following packages have been kept back:
  libxvidcore4
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.[/I]

My Sherlock Holmes deductions tell me  it's probably the ppa:n-muench/vlc...

---

### Post by Condor Cluster on 2011-09-28
More info:

I just tried to install SMPlayer to use as an alternative to VLC, but got error messages off that too.

```
rob@rob-laptop:~$ sudo apt-get install mplayer smplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  mplayer: Depends: libavformat52 (>= 4:0.5.1-1) but it is not going to be installed or
                    libavformat-extra-52 (>= 4:0.5.1-1) but it is not going to be installed
E: Broken packages
```

So it seems my system maybe borked after all!

:(

---

### Post by Krytarik on 2011-09-28
> **Condor Cluster said:**
> So it seems my system maybe borked after all!
Nah, I don't think so. Just try the same with Synaptic, as 'apt-get' doesn't remove packages to fullfil the dependencies of packages set to install.

---

### Post by Condor Cluster on 2011-09-30
Seems to have fixed itself now today, all updates installed using Ubuntu Tweak.

Weird... :neutral:

---

