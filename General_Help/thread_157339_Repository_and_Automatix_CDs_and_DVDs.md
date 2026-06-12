---
title: "Repository and Automatix CDs and DVDs"
date: 2006-04-08
forum: General Help
---

### Post by Shampyon on 2006-04-08
There are DVD and CD images for the Main, Universe and Multiverse repositories ([here]("http://www.ubuntuforums.org/showthread.php?t=78549")), as well as the all the software for Automatix ([here]("http://www.ubuntuforums.org/showthread.php?t=145889")).

For people on dial-up, or people who have low download limits, these discs are very hard to get. I was wondering if anyone would be willing to make themselves available to distribute these discs, in return for full reimbursement for their disc and postage costs. Once I have the discs, I am more than willing to offer the same service.

So have many people gotten these discs? And are you willing to help out all those who are unable?

---

### Post by trent dillman on 2006-04-09
If you send me dvds and a self-addressed stamped envelope, I'll do it...

---

### Post by Shampyon on 2006-04-09
So there are three of us willing to do this. Sweeeeet. erik_boi over in [this]("http://www.ubuntuforums.org/showthread.php?t=78549&page=2") thread is in the process of dl'ing the discs, a massive task for a dial-up user. Thanks to erik for being such a trooper. I'm gonna try and get the automatix CD. Hopefully that'll lighten his load.

I'm surprised, though, that none of the people who have already dl'd the discs have come forward to help out too. Maybe seeing us getting on the task will help get the ball rolling :)

---

### Post by trent dillman on 2006-04-09
I'm in the US, so...

Anyone in the boonies here? Like, WV?

---

### Post by Shampyon on 2006-04-09
Comparitively speaking, I'm in the boonies, despite living in a city.
I'm in Australia :P

---

### Post by Shampyon on 2006-04-12
Well, I've finished downloading the Automatix 1.0rc1 CD. 
I've gotten the torrents for the Ubuntu repo discs, and I'm getting a pretty steady dl rate of 10kbps. I'll let y'all know when that's done (it may be a week or two), and we can start arranging for discs to be sent out.

---

### Post by erik_boi on 2006-04-27
I have finished downloading the packges for breezy but I have several questions.


1. When using the dvds to install things will it always say that the packages are not authenticated or is this a problem related to my next question?

2. At first when I was downloading I didn't have any problems but later... (possibly when I upgraded my computer to dapper, I am not sure exactly when it started) it gave me some key errors. 

I followed the wiki regarding the errors I was getting and did

```

sudo gpg --keyserver subkeys.pgp.net --recv 437D05B5 
sudo gpg --export --armor 437D05B5 | sudo apt-key add - 

```

and then I got a different error that I can't find information about.

```

Mirroring to /backups/ubuntu from ftp://anonymous:archive.ubuntulinux.org/ubuntu//
Arches: i386
Dists: breezy
Sections: main,multiverse,universe
Passive mode on.
Checking md5sums.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Keeping: dists/breezy/Release
[0%] Keeping: dists/breezy/Release.gpg
[COLOR="Red"]gpg: Signature made Thu 13 Oct 2005 02:34:54 PM CDT using DSA key ID 437D05B5
gpg: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.[/COLOR]
Primary key fingerprint: 6302 39CC 130E 1A7F D81A  27B1 4097 6EAF 437D 05B5
Get Packages and Sources files and other miscellany.

then it continues to download the packages

```

If I am going to be sending these to people and it is possible I would like them to be done right; so if you know how to fix this please let me know. On the other hand, if all of the dvds say that the packages arent authenticated then I suppose it really isnt a problem...

Anyways, if you want a set of these dvds let me know

```

man debmirror
.
.
.
MOTTO
       Waste bandwith -- put a partial mirror on your laptop today!

```

Which is what I did.....

---

