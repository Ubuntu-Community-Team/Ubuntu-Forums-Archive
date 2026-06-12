---
title: "How to go about RPM files?"
date: 2010-05-19
forum: General Help
---

### Post by javierdl on 2010-05-19
Hi guys!
I just downloaded this RPM file containing a program I need. It expanded a folder called "usr", which holds 2 subfolders: bin & share. Am I supposed to put the files from these folders into the equivalent folders found in my own File System/usr folder? I tried but I wasn't allowed.

I could really use some pointers here, totally lost :(

Thanks in advance guys :)

JDL

---

### Post by themusicalduck on 2010-05-19
RPM is a format that is used on distros that use the RedHat packaging manager. You can't really use them on Ubuntu. The right file type to use for Ubuntu is deb, so use that if it's available.

It's possible to convert an rpm to a deb with Alien. You can install it with ```
sudo apt-get install alien
``` then use ```
sudo alien -d /path/to/rpm
```
It doesn't always work though.

---

### Post by snowpine on 2010-05-19
What is the application? Is it available in the Ubuntu repositories through the Software Center or Synaptic? (If so, that should be your 1st choice.)

---

### Post by javierdl on 2010-05-20
[SIZE=3]Thank you for the info and advise TMD :)
I downloaded and installed Alien via the Ubuntu Software Centre. Then I used the command line you typed. And it worked, now I was able to install the newly created deb file :)

Snowpine, the program is called Plucker Desktop. I was able to find just Plucker in the software centre as I mentioned above, but [/SIZE][SIZE=3]Plucker Desktop was not found there. I found it here though:[/SIZE][SIZE=3]
"http://desktop.plkr.org"

I am glad you mentioned Synaptic Package M., because I hadn't tried it, and now I can see why it's so important to know about it :)

Thanks again guys :)

JDL
[/SIZE]

---

