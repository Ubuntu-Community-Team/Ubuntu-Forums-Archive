---
title: "No local files in unity lenses"
date: 2012-05-14
forum: General Help
---

### Post by dougleduck on 2012-05-14
Perhaps I've mis-understood how the lenses are meant to work, but I find that local files or folders never show up in any of the lenses unless I've previously opened them. This is true for the file and the video lenses. 

For background I've upgraded from 11.10 to 12.04 recently. My ~/Video and ~/Documents are on a seperate partition which mounts on boot.

I've tried some related fixes from jfgi

zeitgeist-daemon --replace
rm -rf ~/.local/share/zeitgeist
rm ~/.local/share/zeitgeist/activity.sqlite

but to no avail.

Thanks for any help in advance.

---

### Post by philinux on 2012-05-14
It's only meant to show recently opened activity. As logged by zeitgeist.

---

### Post by dougleduck on 2012-05-14
Can that really be true for the video lens? 

It's the videos that I haven't already watched that are interesting to see. I thought the point was to reduce searching around for documents; if I have to remember where everything is and click through the folder tree everytime, I'm not sure I understand the point.

Is this logic documented anywhere? Perhaps it might reveal a workaround.

Thanks.

---

### Post by dougleduck on 2012-05-14
What counts as zeitgeist activity? It it just opening files, is downloading a moving them meant to be logged?

---

### Post by dougleduck on 2012-05-15
So I stumlbed across a bug report from a while ago which seems suggest that a fix has already been released for zeitgeist a long time ago

[https://bugs.launchpad.net/unity/+bug/646724](https://bugs.launchpad.net/unity/+bug/646724)

unity-lens-files (5.6.0-0ubuntu1) precise, but isnt in 12.04 apparently (I'm still on unity-lens-files 5.10.0-0ubuntu1).

The bug is described here,

[http://www.omgubuntu.co.uk/2012/03/how-to-help-test-an-improved-unity-files-lens/](http://www.omgubuntu.co.uk/2012/03/how-to-help-test-an-improved-unity-files-lens/)

including how to update to latest file lens.

---

### Post by philinux on 2012-05-15
> **dougleduck said:**
> Can that really be true for the video lens? 

It's the videos that I haven't already watched that are interesting to see. I thought the point was to reduce searching around for documents; if I have to remember where everything is and click through the folder tree everytime, I'm not sure I understand the point.

Is this logic documented anywhere? Perhaps it might reveal a workaround.

Thanks.

I just got back and opened the video lens. It shows 2 recent and under My Videos it shows the 11 that are in my Videos folder and for online shows 3 with a further 22. I can search for files fine too by typing in part of a file name.

For the files lens it shows quite a few in Recent and quite a few folders that I've browsed. Similarly I can search for files.

---

### Post by dougleduck on 2012-05-15
Not sure I follow what you're saying here, do you find all video files are searchable or only opened ones? Like you said before it currently only shows activity in zeitgeist (whatever 'activity' means), some of the testing ppa's for this include locate as a workaround to fill in those gaps apparently.

I've not been able to actually install from the testing ppa yet, not sure why yet.

---

### Post by philinux on 2012-05-15
> **dougleduck said:**
> Not sure I follow what you're saying here, do you find all video files are searchable or only opened ones? Like you said before it currently only shows activity in zeitgeist (whatever 'activity' means), some of the testing ppa's for this include locate as a workaround to fill in those gaps apparently.

I've not been able to actually install from the testing ppa yet, not sure why yet.

I would forget the testing ppa as 12.04 is now released.

The video lens search searches all my vids from the folder Videos in home.

A partial file name will do.

---

### Post by dougleduck on 2012-05-15
I don't get that behaviour, only recently opened videos are shown. Also searching for these doesn't seem to work very well. Of six files I just opened with file name of the format "The Wire *", they appear in recently viewed, none appear when searching for "wire" or "The Wire" in the video lens, and only 2 appear in the files and folders lens. 

Is there more specific information I can provide?

Thanks.

---

### Post by philinux on 2012-05-15
> **dougleduck said:**
> I don't get that behaviour, only recently opened videos are shown. Also searching for these doesn't seem to work very well. Of six files I just opened with file name of the format "The Wire *", they appear in recently viewed, none appear when searching for "wire" or "The Wire" in the video lens, and only 2 appear in the files and folders lens. 

Is there more specific information I can provide?

Thanks.

I would try this again but in this order.

```
rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace
```

Also update the database used by locate

```
sudo updatedb
```

---

### Post by dougleduck on 2012-05-15
When I do zeitgeist-daemon --replace I get a series of errors of the form 

** (zeitgeist-datahub:3061): WARNING **: recent-manager-provider.vala:133: Desktop file for "sftp://me@someserver.uk/disk/Systematics.cxx" was not found, exec: kdevelop, mime_type: text/x-c++src

all relating to files I previously edited using kdevelop (I currently have the folder 'mounted' using sftp, so they are accesible). It doesnt return so I end up having to terminate the process.

---

### Post by philinux on 2012-05-15
Try a reboot.

---

### Post by dougleduck on 2012-05-16
Reboot affects nothing.

Can I ask what version of unity-lens-files is installed?

---

### Post by philinux on 2012-05-16
> **dougleduck said:**
> Reboot affects nothing.

Can I ask what version of unity-lens-files is installed?

```
apt-cache policy unity-lens-files
unity-lens-files:
  Installed: 5.10.0-0ubuntu1
  Candidate: 5.10.0-0ubuntu1
  Version table:
 *** 5.10.0-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages

```

Did you try a unity reset. You would loose any tweaks.

```
unity --reset
```

---

### Post by dougleduck on 2012-05-16
Reset doesn't change the behaviour.

---

### Post by philinux on 2012-05-16
> **dougleduck said:**
> 

For background I've upgraded from 11.10 to 12.04 recently. My ~/Video and ~/Documents are on a seperate partition which mounts on boot.


I'm guessing that the location of the files might be the problem.

Try copying a small selection to your home directory folders of Documents and Videos.

I assume that Nautilus can search this separate partition for your files.

---

