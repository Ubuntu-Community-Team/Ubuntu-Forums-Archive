---
title: "unrar slow - Common problem?"
date: 2009-10-25
forum: General Help
---

### Post by mac666 on 2009-10-25
Hey
I Use "File Roller", the regular archivehandler, to unrar files. But its slow, too slow.
4.7 GB (Aka DVD :)) file takes about 30 min.

If i google this i only find threads from 2-3 years back.  Is there no fix for this? Or do i need to get something else? 
Some threads suggest WinRar... But surely there should be a linux naitve way (none terminal:P)?

Thanks

---

### Post by zvacet on 2009-10-26
```
sudo apt-get install p7zip p7zip-full p7zip-rar
```

You can do same from synaptic.

---

### Post by mac666 on 2009-10-26
How would i use p7zip?
Is it an extension or program? Do i need to make something else? :)


> **zvacet said:**
> ```
sudo apt-get install p7zip p7zip-full p7zip-rar
```You can do same from synaptic.

---

### Post by DeMus on 2009-10-26
> **mac666 said:**
> Hey
I Use "File Roller", the regular archivehandler, to unrar files. But its slow, too slow.
4.7 GB (Aka DVD :)) file takes about 30 min.

If i google this i only find threads from 2-3 years back.  Is there no fix for this? Or do i need to get something else? 
Some threads suggest WinRar... But surely there should be a linux naitve way (none terminal:P)?

Thanks

Have you watched what your processor is doing while using archive manager?
Open a terminal and type top to see the most active processes on top of the list.
To end the program top type q

It can also be that your hard-disk(s) are not fast enough to handle the large amount of data fast enough. I had that. Now I installed Jaunty on a RAID 0 configuration placing both disks parallel to each other making each disk read and write only half of the data so they are twice as fast. That really helped.

---

### Post by alphaniner on 2009-10-26
If you are going to go the 7z route you really only need to install p7zip-full and p7zip-rar:

```
sudo apt-get install p7zip-full p7zip-rar
```
This will install the executable **7z**.  It has a man page you can read if you install it.

---

### Post by mac666 on 2009-10-27
Its not my processor nor my harddrive. 
How can i launch p7? Gnome-do doesnt find it :)

---

### Post by zvacet on 2009-10-27
Just right click on file an d you will see option **extract here**.

---

### Post by GiveLove on 2009-10-27
Hello mac666, :)

One possibility that occurs to me is that there are two versions of RAR programs in the Ubuntu software repositories:

"unrar"

and 

"unrar-free"

The unrar-free package says:
> Unrar can extract files from .rar archives. Can't handle some archives in the RAR 3.0 format, only the non-free "unrar" package can do that.
Perhaps this is the package you have installed, and you are running into problems with opening newer versions of RAR formats. I've been using the non-free unrar package for many versions of Ubuntu with no problems. Check and see which one you have installed. And consider experimenting by uninstalling one, and installing the other. 

GiveLove

---

### Post by jakslev on 2009-12-21
I have the same issue with unrar. However I am running it from my computer unraring files on a network attached storage location (PopCorn Hour). Could that be the same thing that my fellow movie torrent posters are doing? 

I will try and copy a rar archive over locally and redo the rar to see how that goes..

Will post back!

Update: I just set another machine to start un-raring using a Windows Virtualbox session. So far this one expects that a similar job will be done in 1,5 hour. That is basically the same as I am looking at using the Linux built-in unrar. In other words - it seems that it takes extra long time because I am unraring over a network :s

---

### Post by mac666 on 2009-12-23
It do take extra time if you unrar over network. 
Did you install the packages as describe earlier in the thread?

---

### Post by lavinog on 2009-12-23
> **mac666 said:**
> Hey
I Use "File Roller", the regular archivehandler, to unrar files. But its slow, too slow.
4.7 GB (Aka DVD :)) file takes about 30 min.

If i google this i only find threads from 2-3 years back.  Is there no fix for this? Or do i need to get something else? 
Some threads suggest WinRar... But surely there should be a linux naitve way (none terminal:P)?

Thanks
Are you trying to unrar a rar archive directly from a dvd?
if so copy the file to your hard drive first.

Did you create the archive?
Did you archive it on maximum settings...How much ram do you have.  Sometimes the maximum setting requires a lot more memory...when you use up your memory, your system starts using your swap...which is a billion times slower.  You can watch for this by looking at system monitor.

Edit: Just noticed this thread was hijacked.

---

### Post by jakon on 2009-12-24
I also see this. And i think it's not unrar that is slow, the problem is that the file is *terribly* fragmented. Was it downloaded with transmission?

Please check filefrag output in a terminal, that's what i get:
```
$ filefrag /path/to/the/file.rar
file.rar 223539 extents found, perfection would be 1 extent
```
223539 fragments - that's terrible.

There is a transmission bug entry about this: [http://trac.transmissionbt.com/ticket/849](http://trac.transmissionbt.com/ticket/849)

Workaround (for the next download) in short: set preallocation to 2 instead of 1 in /home/YOURNAME/.config/transmission/settings.json

To "fix" the .rar file you have now: Create a copy, delete the original. Or just wait for unrar to finish and delete the rar.

---

### Post by mac666 on 2009-12-24
> **jakon said:**
> I also see this. And i think it's not unrar that is slow, the problem is that the file is *terribly* fragmented. Was it downloaded with transmission?

Please check filefrag output in a terminal, that's what i get:
```
$ filefrag /path/to/the/file.rar
file.rar 223539 extents found, perfection would be 1 extent
```
223539 fragments - that's terrible.

There is a transmission bug entry about this: [http://trac.transmissionbt.com/ticket/849](http://trac.transmissionbt.com/ticket/849)

Workaround (for the next download) in short: set preallocation to 2 instead of 1 in /home/YOURNAME/.config/transmission/settings.json

To "fix" the .rar file you have now: Create a copy, delete the original. Or just wait for unrar to finish and delete the rar.

After the recommended packages the extracting process took about 1/5 of the time. Its OK now

---

### Post by GiveLove on 2009-12-26
Great post jakon! Thank you so much!

That's sounds like exactly the issue I ran into with large torrent files downloaded with Transmission. I just assumed it was my old slow CPU (AMD Athlon XP 1800+ 1.53Ghz), but now I know better. It's kind of amusing that without changing the preallocation setting in Transmission before downloading, you can simply defragment the file just by copying(not moving) it to another location on your hard drive.

---

### Post by varkey on 2010-05-25
Thanks for the info! I had the same issue, filefrag reports large number of fragments for all my transmission downloads. :(  Have about 700 GB of data downloaded through transmission. Copying to another location on the drive is also taking lot of time. :(

Anyway have set 'preallocation' to 2, from next download the files will be proper.

---

