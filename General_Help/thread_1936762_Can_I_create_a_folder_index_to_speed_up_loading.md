---
title: "Can I create a folder index to speed up loading?"
date: 2012-03-06
forum: General Help
---

### Post by Kissell on 2012-03-06
This is using Ubuntu 11.10 amd64 with XFS file system.

I have a folder that has about 4000 items.  It takes forever, literally several seconds to open the folder...  maybe up to a half a minute sometimes.

Is there anything I can do to speed this up, short of moving files out of that branch of the tree?  I don't want to create subfolders, I want all these files to exist in the same folder.  But I want it to be faster opening the folder.

Can I create some sort of file system index for this folder on the server, or I normally access it across a samba share, can I create a folder cache on the workstation?

---

### Post by sanderj on 2012-03-06
I cannot reproduce this on my Ubuntu 11.10 with ext4; I created 4000 files in one directory with the python script below.

Access from the terminal to all the files is instantly.
Access with Nautilus will take 2 seconds to show all files.

So: is it caused by your filesystem XFS? 
Just checking: you're talking about a local file system, right? Or about a remote file system accessed via a network?


```
import os

for x in range(1000,5000):
	cmd = 'echo "hello this is just some text" > ' + str(x) + '.txt'
	print cmd
	os.popen(cmd)

```

---

### Post by Kissell on 2012-03-06
Actually, yeah, that's an important point...  I just tried to do an "time ls" from the terminal on the machine itself, and it takes 0.039 seconds to list all the contents...

I'm having trouble accessing it quickly through a samba share.

The other machines are mostly linux, but it takes too long to open that folder...  the network is a LAN running at gigabit speed.

---

