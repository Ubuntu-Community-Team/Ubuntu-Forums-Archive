---
title: "Partially Solved - apt-get upgrade error"
date: 2012-08-05
forum: General Help
---

### Post by ytene on 2012-08-05
All,

Before I go any further, let me acknowledge that in large part the problem I describe below is self-inflicted... 

Set-up:
I have a Shuttle X35 "Media PC" [tiny fanless workstation] set up to be a completely silent unit for basic WP, Web and Email activity. I also have an Acer D150 Atom-Powered 10.1" netbook. Both use the 32-bit edition of ubuntu 12.04. 

I also have a QNAP NAS, and both workstations connect to this device using the following fstab connection string:-

[FONT="Courier New"][COLOR="Blue"]#
# QNAP TS-459 Pro II NAS via CIFS/SAMBA
//192.168.1.41/Public				/media/nas cifs defaults,rw,username={myusername},password={mypassword},file_mode=0777,dir_mode=0777
#[/COLOR][/FONT]

So far so good...

Then, just for good measure, I have the following softlink in my /var/cache folder:-

[COLOR="Blue"][FONT="Courier New"]apt -> /media/nas/Software/Linux/ubuntu/Updates/12.04-Precise/i386/var/cache/apt[/FONT][/COLOR]

Initially, this worked an absolute treat. Basically, with this setup I can run "apt-get update" and "apt-get upgrade" on one of these two machines, and a slew of new packages will be brought in. I can then run the same commands on the other machine, and although the updates are applied, they are pulled from the QNAP NAS as opposed to my having to pull them in from the repositories again. I save oodles of bandwidth and time... 

About a month ago, this stopped working. I kept on getting this really weird error message:-

[COLOR="Blue"][FONT="Courier New"]root@ubuntu:/var/cache/apt# apt-get upgrade
Reading package lists... Error!
E: Problem renaming the file /var/cache/apt/pkgcache.bin.iSrZeM to /var/cache/apt/pkgcache.bin - rename (17: File exists)
W: You may want to run apt-get update to correct these problems
root@ubuntu:[/FONT][/COLOR]

So basically, what the apt script is trying to do is replace the existing file 

/var/cache/apt/pkgcache.bin

with a newer version of the same file. The new version is stored in the same location and has the same name as above, but with a random suffix, eg:

/var/cahce/apt/pkgcache.bin.iSrZeM

"Easy!" I hear you cry. Delete "pkgcahe.bin" and re-run the "upgrade" script. Well, when you try this, you'll get an error telling you that "pkgcache.bin" is in fact busy. Because it's on the NAS, you might suggest I try and remove it from another workstation, but that too fails. So then you might suggest that I reboot the NAS, and/or the workstation. All of these permutations will fail. 

The only solution I have come up with so far, and it works reliably, is to do this:-

[COLOR="Blue"][FONT="Courier New"]mv pkgcache.bin pkgcache.dud
rm pkgcache.dud[/FONT][/COLOR]

which works a treat, every time. Weird thing is, I cannot for the life of me see why the system will permit me to "mv" a file that it won't permit me to "rm", and *then*, after the mv, it *will* permit me to remove it. Weird, huh?

You are no doubt sat reading this thinking, "But why is this plonker trying to do these smart-**** things with his apt cache in the first place? 

Well, two good reasons:

1. I have a slow and unreliable 'net connection. Building a fresh machine and pulling in updates for a release that has been around for a while [and this is thoroughly patched] takes *forever*.

2. My ISP comes from the Stone Age and is unimaginably tight; I'm on a metered tariff and I would like to avoid having to re-download stuff I've already got cached locally. 



Wait for it, weird gets weirder:

In addition to these two lightweight workstations, I also have a bit of a monster machine running 12.04 64-bit. This also has multiple copies of ubuntu working on it, but in this case I use removable hard drive caddies and swap between bootable /dev/sda images each time I want to re-task my server for different things... 

In this 64-bit setup, like the 32-bit versions, I have soft-linked from /var/cache to a common, central copy of the apt folder. The only significant difference in this case is that the shared 64-bit apt folder is actually stored local to the machine, on an internal HDD drive [I have space for 2 removable drives, but also 2 fixed, internal drives on this machine.]

I have never had a moment's trouble with the 64-bit "internal" softlinking to the apt cache, but clearly I have had issues with the 32-bit version. 

I am tempted to throw together another build on the 64-bit system and put a copy of the apt cache on the QNAP NAS, just to see what happens. 

I would be very interested for any comments, suggestions, thoughts [ other than, "You're trying to do something that's really rather silly" - I already know that...] as to how I might be able to make apt a little bit more reliable or robust. 

Oh, one more thing...

When I bought this QNAP NAS back in Jan/Feb this year, I had endless trouble trying to get it to connect using CIFS. This forum kindly helped me switch to an NFS solution, which has been absolutely brilliant. Then, about 3 weeks ago, I updated the QNAP Firmware to 3.7.1, and my NFS mapping just stopped working. 

With a lot of help from Patrick over at the QNAP forums, I reverted my connection from NFS to CIFS and got connectivity restored. The previously broken CIFS connection string now seems to work correctly. 

*There is no relation between connection methodology and this APT issue - at least none that I am aware of*. Timings are such that these do not seem to be related.

---

### Post by cwalter on 2012-08-08
ytene,

I have been searching to solve the exact problem you describe. A distribution upgrade could take 1 or 2 Gig per workstation and if you have a home network with 4 or more computers, then this can quickly eat up the bandwidth CAP common from many ISPs.  

Your solution is simple and elegant.  I am unable to describe the cause of the errors that you are receiving.  However, they indicate a loss of the caching benefit, if it is downloading the desired files again and attempting to over-write your cache.  

I found a procedure describing a package called apt-cacher which does exactly what you need, on the second half of the article linked below. 

[http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher]("http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher")

I also have a QNAP NAS on my network and would like to install apt-cacher directly on the QNAP.  However, I have not yet found the way to do that...this will be a question for the qnap forums.  

I hope this helps.

---

