---
title: "Wubi GNU Grub 1.97"
date: 2011-06-23
forum: General Help
---

### Post by h1123 on 2011-06-23
I know there are loads of "solution" threads out there, but I have tried all of the replacing the wbu... file in the c:/ to no avail. I have 4 assigmnets due in next week on my wubi desktop, so:

A) Either I need a solution to fix the install
B) I need a way to get to my desktop VIA Windows!

Thanks

---

### Post by h1123 on 2011-06-23
Come on guys i really need a solution

---

### Post by h1123 on 2011-06-23
> **h1123 said:**
> I know there are loads of "solution" threads out there, but I have tried all of the replacing the wbu... file in the c:/ to no avail. I have 4 assigmnets due in next week on my wubi desktop, so:

A) Either I need a solution to fix the install
B) I need a way to get to my desktop VIA Windows!

Thanks

Also my Ubuntu folder in the C: only has folders called winboot and install..............

---

### Post by dandnsmith on 2011-06-23
You haven't really stated the problem.
Which version of Ubuntu are you talking about, have you done a wubi install, what went wrong with what you did, what 'desktop' are you talking about here, and what do mean about VIA Windows?
I'm not being obstructive, it's just that the while situation is unclear - I can envision all sorts of possibilities, but you need to describe the start point, the current state, and the desired end state.

---

### Post by h1123 on 2011-06-23
> **dandnsmith said:**
> You haven't really stated the problem.
Which version of Ubuntu are you talking about, have you done a wubi install, what went wrong with what you did, what 'desktop' are you talking about here, and what do mean about VIA Windows?
I'm not being obstructive, it's just that the while situation is unclear - I can envision all sorts of possibilities, but you need to describe the start point, the current state, and the desired end state.

Ubuntu 9.10

Shutdown laptop last night, rebooted it this morning tried to open my wubi install and its keeps coming up with a GNU Grub 1.97beta screen.

I am talking about accessing my ubuntu desktop, which has all my files on it, through windows some how........ my desired end state isn't even saving my wubi install its just getting myfiles from the documents folder and desktop of wubi!

---

### Post by bcbc on 2011-06-23
9.10 is not supported anymore. Also, if you haven't already, you need to [replace the wubildr]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10") for this release.

But you have a bigger problem if your ubuntu directory doesn't have the disks folder. You need the root.disk file specifically - then you can recover your data. If it's not there, then you need to change windows to show hidden files and folders, and go looking for it. Start with C:\FOUND.000 and sometimes there's a folder under that with the root.disk within that. The root.disk may also have been renamed chk0000.chk (something like that) so look on the size of the file as well (it will be about as big as the install size you chose for Wubi - between 4 and 30GB).

Once you find it, you can use [this]("http://ext2read.blogspot.com/") to view it from windows and copy off your data. Restoring it back to the \ubuntu\disks\ folder should allow booting (after you fix the C:\wubildr)

---

### Post by dandnsmith on 2011-06-23
OK, that's a lot clearer, thanks.
I think you're saying you can still boot into Windows, so you'd achieve your aims if you could repair the bit which invokes the wubi install. A search suggests that it may have been an update which caused the damage - unfortunately, although I've seen a good many posts on this sort of topic, I'm not competent to direct you in the repair.

There is a tool, under linux, called LVPM which could get to the files you want directly - I've no experience here either.

Have a look at [url=http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer)]this explanation of wubi[/ur], which may help your thinking.

---

### Post by h1123 on 2011-06-23
> **bcbc said:**
> 9.10 is not supported anymore. Also, if you haven't already, you need to [replace the wubildr]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10") for this release.

But you have a bigger problem if your ubuntu directory doesn't have the disks folder. You need the root.disk file specifically - then you can recover your data. If it's not there, then you need to change windows to show hidden files and folders, and go looking for it. Start with C:\FOUND.000 and sometimes there's a folder under that with the root.disk within that. The root.disk may also have been renamed chk0000.chk (something like that) so look on the size of the file as well (it will be about as big as the install size you chose for Wubi - between 4 and 30GB).

Once you find it, you can use [this]("http://ext2read.blogspot.com/") to view it from windows and copy off your data. Restoring it back to the \ubuntu\disks\ folder should allow booting (after you fix the C:\wubildr)

Hardley any of that made any sense! I tried looking throug hidfiles/folders nothing there either. no clue what this chk....... file is and where i could locate it........ if it is an update issue then that is really annoying because its nothing ive done and i stand to lose a couple of weeks worth of assigments!

---

### Post by bcbc on 2011-06-23
I'll try to explain a little better....

Wubi installs Ubuntu on a virtual disk which is the file root.disk. This is stored within the disks folder. So, e.g. if you installed Wubi to C: then you'll see:
C:\ubuntu\disks\root.disk

That file contains your entire Ubuntu install, including the OS, programs you installed, your settings and your data. If that is missing you need to find it.

Why would it go missing? Sometimes the file can become corrupted (maybe due to a forced power-off) and Windows will sometimes automatically "clean" it up by running chkdsk. This removes dirty files and places then in hidden folders e.g. C:\FOUND.000

Since you said your whole \ubuntu\disks folder is missing, it's likely that the folder was removed. Therefore you might find a folder under C:\FOUND.000 called chk0000 (or something generic like that) and within that folder you'll probably find the root.disk and swap.disk (the swap.disk is useful for running Ubuntu but not required and does not contain your data).

---

### Post by h1123 on 2011-06-23
Ahh right ok! Well I've had a look everywhere and again no luck! I have no idea why it would do something like that.................

---

### Post by bcbc on 2011-06-23
> **h1123 said:**
> Ahh right ok! Well I've had a look everywhere and again no luck! I have no idea why it would do something like that.................

Try windows search for "root.disk"

---

### Post by h1123 on 2011-06-23
> **bcbc said:**
> Try windows search for "root.disk"

No items match your search.................

---

### Post by bcbc on 2011-06-23
> **h1123 said:**
> No items match your search.................

That doesn't look good. The only other thing I would suggest is booting from an Ubuntu CD/USB (select "Try it" without installing) and then mount and search your windows partition. Sometimes you can see things that windows doesn't show.

Not sure what else you could do.

Also search for *.CHK (and look for any file that's about the same size as the root.disk would have been)

---

### Post by h1123 on 2011-06-23
Any of those look promising?

---

### Post by bcbc on 2011-06-23
No, how about *CHK*

---

### Post by h1123 on 2011-06-23
> **bcbc said:**
> No, how about *CHK*

5000 hits on this occasion, none though seem to be what we are after. 1 is called "disk" but its a file rather than a folder

No root_disk files....

---

### Post by bcbc on 2011-06-23
> **h1123 said:**
> 5000 hits on this occasion, none though seem to be what we are after. 1 is called "disk" but its a file rather than a folder

No root_disk files....

The file might have been renamed. Look for a match on size as well. e.g. if you picked a 10GB wubi install, look for a 8.8GB file. (1 GB goes toward the CD and the swap file).

---

### Post by h1123 on 2011-06-23
> **bcbc said:**
> The file might have been renamed. Look for a match on size as well. e.g. if you picked a 10GB wubi install, look for a 8.8GB file. (1 GB goes toward the CD and the swap file).

Nope all the files together equate to 2.5 GB (I had at least 15GB on my Wubi) so it can not be any of these! :-(

---

