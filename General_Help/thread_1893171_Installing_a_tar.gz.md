---
title: "Installing a tar.gz"
date: 2011-12-09
forum: General Help
---

### Post by ubunwhat on 2011-12-09
I know this is considered a bad thing.  The issue is that I have gone insane trying to find a program in the software center that will convert an xvid to a dvd quality .avi.  I'm getting little to no love in multimedia forum so that's no help.  Everything I see online says that the best program for this is mandvd.  Ok, great.  But it's not in the software center.  I did download a tar.gz for it, but have absolutely how to install from one.  Any help would be appreciated.

---

### Post by collisionystm on 2011-12-09
> **ubunwhat said:**
> I know this is considered a bad thing.  The issue is that I have gone insane trying to find a program in the software center that will convert an xvid to a dvd quality .avi.  I'm getting little to no love in multimedia forum so that's no help.  Everything I see online says that the best program for this is mandvd.  Ok, great.  But it's not in the software center.  I did download a tar.gz for it, but have absolutely how to install from one.  Any help would be appreciated.


extract the file

look at its contents

look for an install or make file

or just an executable file to run it

---

### Post by haqking on 2011-12-09
There are .debs for it see here [http://linuxappfinder.com/package/mandvd](http://linuxappfinder.com/package/mandvd) and scroll towards bottom for links.

As for tar.gz for future reference:

First of all always search in the Software Centre or Synaptic Package manager to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)

You can also use Gdebi package installer or look at dpkg.

If you have to download it as a package it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

These are analogous to windows .zip files but with varying compression denoted by the .xx after the .tar such as .tar.gz where .gz is the compression. A .tar file means Tape Archive which is legacy from UNIX when things were backed up to tape drives. The 2 or 3 letters after the .tar refer to the type of compression used to pack down the archive.

See here for dealing with these files [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

It is often just a simple case of right clicking in your GUI on the file and choosing extract then it will be unpackaged to a directory.

The contents might simply be a .deb file as i said for easy installation see here:

[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If the contents is source code then you need to compile this, this is where people often get stumped and is dependant on the developer and the documentation provided, once unpackaged there is often a README text file or a INSTALL file which you should read as it will often contain clear and concise instructions on what to do.

If not then you need to figure it out, see here for information on compiling from source:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

then you should be set 

Have fun

Regards

haqking

---

### Post by ubunwhat on 2011-12-09
@haq

I followed the first link you posted.  They had a link on how to add their repositories to synaptec.  Unfortunately I can't figure that one out.  I go to synaptec, open settings and repositories.  From there I click Add.  Unlike the screenshot, there is just one line for input in synaptec.  It asks for the complete type and url.  I tried putting in deb [http://mirrors/kernel/debian/](http://mirrors/kernel/debian/)  in different variations but the result is always the same.  It doesn't allow me to click add.  The only option is cancel.  It's as if I haven't entered enough info or have entered it improperly.  Do you know the exact format for this?

---

### Post by oldos2er on 2011-12-09
Just download the deb file, either [http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mandvd/mandvd_2.6-1-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mandvd/mandvd_2.6-1-0ubuntu1_amd64.deb) or [http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mandvd/mandvd_2.6-1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mandvd/mandvd_2.6-1-0ubuntu1_i386.deb) and double-click it to install. It's really not a good idea to add debian kernel repository to Ubuntu.

---

### Post by haqking on 2011-12-09
> **oldos2er said:**
> Just download the deb file, either [http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mandvd/mandvd_2.6-1-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mandvd/mandvd_2.6-1-0ubuntu1_amd64.deb) or [http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mandvd/mandvd_2.6-1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mandvd/mandvd_2.6-1-0ubuntu1_i386.deb) and double-click it to install. It's really not a good idea to add debian kernel repository to Ubuntu.

+1

Not sure where the debian kernel repo came from, all the links are to the archive.ubuntu.com/multiverse

Edit: oh i see you clicked on the how to add repo link, seeing as you are using Ubuntu then follow the Ubuntu links ;-)

---

### Post by jonobr on 2011-12-09
> I know this is considered a bad thing. The issue is that I have gone insane.....

Going insane is always a bad thing.....:-)

---

