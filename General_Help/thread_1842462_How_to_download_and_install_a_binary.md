---
title: "How to download and install a binary?"
date: 2011-09-11
forum: General Help
---

### Post by Jeff Root on 2011-09-11
I'm running 64-bit Maverick Meerkat.
 
I have a file archived in rar format that I want to un-archive.
The web says a binary program "unrar-nonfree" can do it.
This binary apparently can be found at:
 
[https://launchpad.net/ubuntu/+source/unrar-nonfree/1:3.9.10-1](https://launchpad.net/ubuntu/+source/unrar-nonfree/1:3.9.10-1)
 
Although the word "source" is in the page name.  I don't need
the source, just the binary.
 
Do I need all three files?
 
Can I download and save it / them on my data drive for later
installation?
 
How do I install it / them?
 
   -- Jeff, in Minneapolis

---

### Post by raja.genupula on 2011-09-11
extract that source folder 
cd to that from terminal 
do this one by one 
```
./configure
```
```
make 
```
```
sudo make install
``` 

these are the three steps for installing from source 

if i remember correctly , 2nd step (i mean make will create a binary for you ).

installing binary is simple 
```
./binfile.bin
```

---

### Post by gandaran on 2011-09-11
> I have a file archived in rar format that I want to un-archive.
why not just install unrar and rar from software center? 
then to extract rar packages right click » extract here.

---

### Post by snip3r8 on 2011-09-11
Choose the binary packages at the bottom of the page

---

### Post by fdrake on 2011-09-11
before doing the commands suggested by raja.genupula (post #2) make sure that you got the build essential packg installed, do:

```

sudo apt-get install build-essential

```

---

### Post by Jeff Root on 2011-09-11
It appears that the info provided by snip3r8 may be the
path to my answer.  I hadn't noticed that the item pointed
out was a link to the binary, not just information.
 
So it looks like I have a choice of downloading the binary
and installing it directly, or downloading the source code,
compiling it into the binary, and installing it.  Although
most of the work would be taken care of for me by Ubuntu,
I see no reason to take the latter path when I could just
download and install the binary itself.
 
Apparently the binary I need is this:
 
[http://launchpadlibrarian.net/48909991/unrar_3.9.10-1_amd64.deb](http://launchpadlibrarian.net/48909991/unrar_3.9.10-1_amd64.deb)
 
which I just downloaded and saved on my data drive.  I found
the link to the file on this page:
 
[https://launchpad.net/ubuntu/maverick/amd64/unrar/1:3.9.10-1](https://launchpad.net/ubuntu/maverick/amd64/unrar/1:3.9.10-1)
 
which says that it depends on:
 
* libc6 (>= 2.7)
* libgcc1 (>= 1:4.1.1)
* libstdc++6 (>= 4.1.1)
 
I just now opened a terminal window and used the command:
 
dpkg --get-selections | grep -i install
 
which I've been told lists all installed packages.
None of the three dependancies are listed.  Does that
mean I need to download and install them first?  Will
the Software Center do that for me if I use it rather
than doing it the way I'm trying to do it?
 
Raja,
 
What does "./configure" do?  Does it act on all the files in
the current folder?  Or what?
 
How does "sudo make install" tell the system what files I
want to install?  Does it use everything in the folder?
 
[quote=raja.genupula]
installing binary is simple
```

./binfile.bin
```[/quote]
I'm guessing that you just mean "Input the filename of the
binary, and the system will install it."
 
But what is the "./" for?
 
   -- Jeff, in Minneapolis

---

### Post by fdrake on 2011-09-11
the first 2 packages should be already in.check with;
```

dpkg --get-selections | egrep 'libc6|libgcc1|libstdc++'

```
if you don't see them listed then do

```
sudo aptitude update && sudo aptitude upgrade
sudo apt-get install libc6 libgcc1 libstdc++*
```

---

### Post by Jeff Root on 2011-09-11
**fdrake**,
 
Thank you.  That listed all three dependancies.
After each is the word "install".  Does that mean
they are installed, or that they can be installed?
 
   -- Jeff, in Minneapolis

---

### Post by fdrake on 2011-09-11
> **Jeff Root said:**
> **fdrake**,
 
Thank you.  That listed all three dependancies.
After each is the word "install".  Does that mean
they are installed, or that they can be installed?
 
   -- Jeff, in Minneapolis
u r welcome.yes they r installed: from "man dpkg"

> 
--get-selections [package-name-pattern...]
              Get list of package selections, and write it to stdout. Without a pattern,  non-installed  packages  (i.e.
              those which have been previously purged) will not be shown.


---

### Post by Jeff Root on 2011-09-11
Okay.  Although I didn't learn a huge amount, I did get
the job done.  I just went ahead and clicked on the .deb
file, and it apparently installed okay.  There was some
kind of hangup that prevented me from unmounting the
drive that the .deb file was on for several minutes, but
it eventually went away and I was able to run unrar and
viewed my archived file.
 
Thank you.
 
   -- Jeff, in Minneapolis

---

