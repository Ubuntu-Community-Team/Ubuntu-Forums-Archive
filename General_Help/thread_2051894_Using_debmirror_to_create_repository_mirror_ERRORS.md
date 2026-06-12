---
title: "Using debmirror to create repository mirror ERRORS!"
date: 2012-09-02
forum: General Help
---

### Post by cainram on 2012-09-02
Hi,
I've used this exact method in the past to create a local repo mirror. Here is the command I'm using:

debmirror /home/cainram/ --nosource -m --passive --host=ftp.usf.edu --root=ubuntu/ --method=ftp --progress --dist=precise --section=main,universe --arch=i386ubuntu/ --ignore-release-gpg

Here's what I get...

Mirroring to /home/cainram/ from [ftp://anonymous@ftp.usf.edu/ubuntu//](ftp://anonymous@ftp.usf.edu/ubuntu//)
Arches: i386ubuntu/
Dists: precise
Sections: main,universe
Pdiff mode: use
Veriftying checksums.
Passive mode on.
Will clean up after mirroring.
Attempting to get lock ...
cwd to /ubuntu/ failed at /usr/bin/debmirror line 846.
WARNING: releasing 1 pending lock...

I've looked all over and can't really get a good answer. Like I said, I've used this utility before and had no trouble... I'm sure it is something simple I'm just not seeing... Any help would be great, Thanks!
I'm running Ubuntu 12.04 Precise i386.

Ramsey

---

### Post by will177 on 2012-09-05
I use this in Precise 12.04 and it seems to work still for me:

arch=amd64
section=main,restricted,universe,multiverse
release=precise,precise-security,precise-updates,precise-backports,precise-proposed
server=gb.archive.ubuntu.com
inPath=/ubuntu
proto=http
outPath=/mirror


# Start script
#
debmirror       -a $arch \
                --no-source \
                -s $section \
                -h $server \
                -d $release \
                -r $inPath \
                --progress \
                --cleanup \
                -e $proto \
                $outPath


HTH

Will

---

