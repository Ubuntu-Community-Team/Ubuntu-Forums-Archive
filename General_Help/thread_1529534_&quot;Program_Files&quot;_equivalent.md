---
title: "&quot;Program Files&quot; equivalent"
date: 2010-07-12
forum: General Help
---

### Post by Apolyonn on 2010-07-12
Hey all,

I'm using Ubuntu 10.04.  I love it but I'm still very new to it.  I downloaded FileZilla recently from their main site because it's not available for download from the Software Center or by entering the sudo apt-get command to get it.  I wanted to put it with all the other programs, but I have no idea where they're located.  Windows' Program Files is pretty straightforward.  

So, where are they located?

Thanks.

---

### Post by mikewhatever on 2010-07-12
Strictly speaking, there is no equivalent of Program Files in Linux. A somewhat far fetched one would be /usr, but don't expect to find the same directory structure there.
If you downloaded the Debian binaries from [http://filezilla-project.org/](http://filezilla-project.org/), I'd suggest putting them in /opt/filezilla/.

---

### Post by mortalapeman on 2010-07-12
Ubuntu Doesn't organize its programs like that. Linux has something like dedicated folders for each part of each program. Executables or programs go in /usr/bin, settings for that program go in /home/username/.program, log files go in /var/logs, etc.  (Don't quote me on that last one)
 
Something that might make you happy would be to make a special hidden folder (all hidden folders "." at the beginning of the name) called .Filezilla and put the downloaded folder for filezilla into it and make a symbolic link from /usr/bin to that folder so that when you use the "Run" command it will search there also.
 
You can also add a menue entry through the main menue editor in system>preferences. Just go into the folder that you downloaded and find the path to the executable, add that, find the path to the icon, and add that to menue under Internet.
 
If this sound like something that will work for you, come back later. I'll post my detailed instructions later. I'm at work currently and have only windows machines surrounding me.

---

### Post by mortalapeman on 2010-07-12
> **mikewhatever said:**
> Strictly speaking, there is no equivalent of Program Files in Linux. A somewhat far fetched one would be /usr, but don't expect to find the same directory structure there.
If you downloaded the Debian binaries from [http://filezilla-project.org/](http://filezilla-project.org/), I'd suggest putting them in /opt/filezilla/.
 
 
oh ya /opt would make sense also, I forgot about that folder.

---

### Post by 3rdalbum on 2010-07-12
> **Apolyonn said:**
> I downloaded FileZilla recently from their main site because it's not available for download from the Software Center or by entering the sudo apt-get command to get it.

Well, yes it is. It's in the Universe repository, which should be enabled by default on Ubuntu. Check that you have all repositories enabled in System > Administration > Software Sources. Then update your package list (the Reload button in Synaptic) and do a search for Filezilla.

Also, note that the best way of installing software from outside the Ubuntu repositories is to use a PPA. A PPA is basically a third-party repository maintained by someone from the community, and they often package up software that is not in the Ubuntu repositories, or is only available in an older version from the normal Ubuntu repositories.

In this case, a fairly recent Filezilla is in Ubuntu 10.04 and should be good enough. There are several PPAs with later versions - one of the PPAs I have enabled on my system contains a later Filezilla, although I didn't enable it for that.

Just do a Google search for "filezilla ppa".

---

