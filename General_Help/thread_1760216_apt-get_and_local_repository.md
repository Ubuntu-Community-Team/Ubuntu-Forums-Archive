---
title: "apt-get and local repository"
date: 2011-05-16
forum: General Help
---

### Post by BobvanderPoel on 2011-05-16
I'm completely braindead on this ...

I've copied a number of deb files from my ubuntu Natty dvd to /home/bob/Natty-DVD/pool

And I ran

sudo dpkg-scanpackages . /dev/null | gzip -c9 > Packages.gz

Which created the nesc. Packages.gz file.

Then I edited my /etc/apt/sources.list and added the line:

deb file:///home/bob/Natty-DVD ./

and did a sudo apt-get update

But, the list of repos doesn't include my /home/bob/Natty-DVD. 

Any idea how to either debug this ... or what is the magic I'm missing?

This is on a fresh install of natty.

Thanks.

---

### Post by gsmanners on 2011-05-16
I think you may have that deb line wrong. 

```
deb file:/home/bob/Natty-DVD ./
```

See: [https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

---

### Post by BobvanderPoel on 2011-05-16
I've tried it again with the suggested line

deb file:/home/bob/Natty-DVD ./

The difference being a single / instead of ///. 

Still no luck. The command

sudo apt-get update

Spews out a number of http upateds, but the only ones with 'file' are:

bob@Mellowood:~/Natty-DVD$ sudo apt-get update | grep -i file
Ign file: ./ InRelease
Ign file: ./ Release.gpg
Ign file: ./ Release
Ign file: ./ Translation-en_CA
Ign file: ./ Translation-en

No idea what this means :)

But, synaptic doesn't seem to be grabbing files from my HHD.

---

### Post by gsmanners on 2011-05-16
I think what you're running into is that apt always prefers "official" sources. If you want to install packages locally, you might want to disable the other repos temporarily. Then enable them again once you're done installing packages from your local repo.

---

### Post by BobvanderPoel on 2011-05-16
Okay. That appears to work. Unchecked the std stuff leaving only my locals.

Only "problem" I see is that my packages (well, the stuff off the official DVD) is not authenticated.

Seems to be a bit of a backwards way to do this. Is there nothing easier .... it'd be nice if apt would check the stuff on disk and only go to the 'net if the 'net package was newer.

BTW, I'm doing  all this 'cause i'm on a ISP with very limited bandwidth caps.

---

### Post by gsmanners on 2011-05-16
I think the decision to make online official repos higher priority was because of security concerns. People who don't know what they're doing could install malicious software too easily, and people who know what they're doing could easily authenticate their own repos (or easily ignore the warning about their packages not being authenticated).

---

### Post by BobvanderPoel on 2011-05-16
I'm sure that makes sense.

The reason I'm doing this at all is that I can't seem to get synaptic to recognize the DVD that I used to install in the 1st place.

I can click on <add CD> etc. ... but the dvd is not recognized. I get the following error message ... even though the DVD is mounted and available.

.....

Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download. They have been ignored, or old ones used instead.

.....

I've tried using apt-cdrom, but that doesn't help either. Using that I get:

bob$ apt-cdrom  -d /media/Ub*  add
Using CD-ROM mount point /media/apt/
Identifying.. [148a70b0241aac8945b2f083898a9e55-2]
Scanning disc for index files..

Using CD-ROM mount point /media/apt/
Identifying.. [148a70b0241aac8945b2f083898a9e55-2]
Scanning disc for index files..

E: Unable to stat the mount point /media/Ubuntu\04011.04\040i386/ - stat (2: No such file or directory)
E: Unable to stat the mount point /media/Ubuntu\04011.04\040i386/ - stat (2: No such file or directory)
E: Unable to stat the mount point /media/Ubuntu\04011.04\040i386/ - stat (2: No such file or directory)

..............

Seems I'm going in circles. And, yes, there is a mounted DVD in /media!

bob$ ls /media/Ub*
autorun.inf  cdromupgrade  install     pics     README.diskdefines  wubi.exe
boot         dists         isolinux    pool     ubuntu
casper       doc           md5sum.txt  preseed  usb-creator.exe

........

I'm more and more confused :)

---

### Post by gsmanners on 2011-05-16
Yeah, it probably has to do with mount points, and there was some progress, but the devs were lacking info.

see [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/602945](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/602945)

---

### Post by mc4man on 2011-05-17
As far as your orig. - a local repo in ~/
A few things you did were off, though the best use of a local repo is for packages versioned higher than same in ubuntu repos and or packages not available in your normal sources.

The sources.list entry should be more like
```
deb file:///home/bob Natty-DVD/
```
and you also need to do 2 lines - dpkg-scanpackages and dpkg-scansources

Here's Ex of how I do here, very simple - works fine with apt-get and synaptic.
For update-manager or Software-center the local repo must be authenticated - I've found that to be more of a hassle than just repackaging apt-daemon to allow unauthenticated source (plus mainly use synaptic or apt-get or gdebi

[http://ubuntuforums.org/showthread.php?p=7606998](http://ubuntuforums.org/showthread.php?p=7606998)

---

### Post by BobvanderPoel on 2011-05-17
> **mc4man said:**
> 
For update-manager or Software-center the local repo must be authenticated - I've found that to be more of a hassle than just repackaging apt-daemon to allow unauthenticated source (plus mainly use synaptic or apt-get or gdebi


I think I used your original post as a guide to get this working on my system when I started this. The main problem is with the authentication ... and I think you're right that it's not worth the effort.

However, on the good news side of life, I think I have managed to mount the DVD so that apt/synaptic likes it. Here's what I did:

1. Add to /etc/fstab a line for for the cdrom/dvd:

/dev/cdrom     /media/cdrom udf,iso9660  owner,ro   0   0 

(do this with your favorite editor as root. And make sure there is a LF at the end of the line).

2. Create an empty dir in /media as a mount point. Again, as root:  mkdir /media/cdrom

3. Insert DVD in drive. I get an error about needed to be root to mount (I think my fstab line could use help). So, again as root, type mount /media/cdrom

Now the dvd is mounted. Start up synaptic and go to the edit->add cdrom and follow the prompts. Click <Reload> and you should have the packages available.

I _think_ this works here. But, it's pretty convoluted! And easier solution would be helpful. And to make life more interesting ... I just checked the /media mountpoints. My DVD is NOT mounted at /media/cdrom ... it's mounted at /media/apt.

I'm totally confused at this point. But, it's working enough to install the big packages and avoid using a lot of bandwidth.

---

