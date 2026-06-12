---
title: "Netbook hard-drive was formatted; recovery?"
date: 2012-02-20
forum: General Help
---

### Post by 0011235813 on 2012-02-20
Hello forum!
I have a major problem; I've installed Ubuntu on one of my friends Netbook; however, there was an error which forced the (USB) Ubuntu installer to format the drive and "erase" all data. Since the data wasn't shredded, I know that it is possible that I might be able to recover the data. Does anyone know if this is possible, and if so, how?
It is very important that I do this, as my friend is quite in a panic. Any help would be much appreciated.

---

### Post by Grenage on 2012-02-20
There is hope, have a look here:

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

There are plenty of excellent guides on its use (a google search), and I've had plenty of success.  If you go through them and get stuck, post back and we'll help where we can.

---

### Post by 0011235813 on 2012-02-20
> **Grenage said:**
> There is hope, have a look here:

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

There are plenty of excellent guides on its use (a google search), and I've had plenty of success.  If you go through them and get stuck, post back and we'll help where we can.
OK, I've downloaded the  archive for the app, how do I install it?
EDIT: I've installed the photorec app, and now I'm trying to recover the lost data. It seems to be working (it's a command app so it's a bit confusing) but I won't know for sure until it's done.

---

### Post by Grenage on 2012-02-20
Good luck; I hope you get back all you can.

---

### Post by 0011235813 on 2012-02-20
> **Grenage said:**
> Good luck; I hope you get back all you can.
How much data do you think can be recovered (keeping in mind the HDD wasn't very fragged) ?
It's creating the files in all sorts of numbered directories that belong to root, in your experiences, will the files belong to me after it's done? Or else how do I change the permissions (gksu nautilus doesn't find them).

---

### Post by Grenage on 2012-02-20
> **0011235813 said:**
> How much data do you think can be recovered (keeping in mind the HDD wasn't very fragged) ?
It's creating the files in all sorts of numbered directories that belong to root, in your experiences, will the files belong to me after it's done? Or else how do I change the permissions (gksu nautilus doesn't find them).

I have no way of knowing, unfortunately; it's usually best to be pessimistic, and be elated with what you get back. ;)

Permissions are very easy to change, so that part is simple.  If you want to change ownership, it'll be something like:

```
chown -R *username directoryname*
```

-R makes it recursive, so that all subdirectories are also affected.

---

### Post by 0011235813 on 2012-02-20
> **Grenage said:**
> I have no way of knowing, unfortunately; it's usually best to be pessimistic, and be elated with what you get back. ;)

Permissions are very easy to change, so that part is simple.  If you want to change ownership, it'll be something like:

```
chown -R *username directoryname*
```

-R makes it recursive, so that all subdirectories are also affected.
I've gotten a couple of thousand so far, so I think I'm doing OK.

Can I use this to change several directories at the same time?

EDIT: I'm getting a lot of .txt files. Is this normal?

---

### Post by Grenage on 2012-02-20
Generally you'd use it on the top directory and let to propagate down, but we can work with whatever your end result is.

You are going to get a lot of stuff, and on a well-used drive, I imagine you will recover more than you were expecting.

---

### Post by 0011235813 on 2012-02-20
> **Grenage said:**
> Generally you'd use it on the top directory and let to propagate down, but we can work with whatever your end result is.

You are going to get a lot of stuff, and on a well-used drive, I imagine you will recover more than you were expecting.

Let's just hope that includes all those important documents.

---

### Post by Mark Phelps on 2012-02-20
The more you use the netbook, the greater the chance that you will be able to retrieve NOTHING!

What you need to do NEXT is attempt to make a copy of the reformatted drive on another PC so that you can work at recovering the data without touching the original.

You could look into using Testdisk to recovery data:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

If Photorec and/or Testdisk don't find the files, then you need to look into using MS Windows recovery apps:

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

There's also a FREE MS Windows file system recovery app known as Recuva.  You could try that first -- but my experience in MS Windows is you get what you pay for.

Your data ... your money ... your choice.

---

### Post by 0011235813 on 2012-02-20
> **Mark Phelps said:**
> The more you use the netbook, the greater the chance that you will be able to retrieve NOTHING!

What you need to do NEXT is attempt to make a copy of the reformatted drive on another PC so that you can work at recovering the data without touching the original.

You could look into using Testdisk to recovery data:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

If Photorec and/or Testdisk don't find the files, then you need to look into using MS Windows recovery apps:

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

There's also a FREE MS Windows file system recovery app known as Recuva.  You could try that first -- but my experience in MS Windows is you get what you pay for.

Your data ... your money ... your choice.
Test disk has obtained a large number of root directories containing various files. I've ran it for a couple of hours and I've extracted about 60-70GB of information from it. Once it's completely finished, I will un-root the directories and see what files have been recovered.

If all else fails, I'll go to an IT professional. In any case, If  I am going to bring out cash, I might as well ask for professional help, not buy an app which I have no idea how to really use.

---

### Post by MIRAAN Baloch on 2012-02-20
Good



> **Grenage said:**
> There is hope, have a look here:

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

There are plenty of excellent guides on its use (a google search), and I've had plenty of success.  If you go through them and get stuck, post back and we'll help where we can.

---

### Post by 0011235813 on 2012-02-20
I have opened some of the directories, and I successfully managed to open a presentation. Currently, the directories belong to root, the program hasn't yet finished though.
My question is; will the program make me the owner of the after it's finished? Or do I have to do it manually?

---

### Post by Grenage on 2012-02-21
> **0011235813 said:**
> I have opened some of the directories, and I successfully managed to open a presentation. Currently, the directories belong to root, the program hasn't yet finished though.
My question is; will the program make me the owner of the after it's finished? Or do I have to do it manually?

I honestly don't recall, but suspect it will leave the permissions to that of the user that ran Testdisk.

---

### Post by 0011235813 on 2012-02-21
> **Grenage said:**
> I honestly don't recall, but suspect it will leave the permissions to that of the user that ran Testdisk.

Ah well, I'll just have to spend nearly an hour un-rooting them all :(
But hopefully, once it's completely done, un-rooted, I can get to work moving docs to Documents and PNG's to Images, and hopefully most, if not everything, will be found. 

I don't know what to do with these .exe and .txt and .elf files. Are they from the previous Windows partition?

---

### Post by Grenage on 2012-02-21
> **0011235813 said:**
> Ah well, I'll just have to spend nearly an hour un-rooting them all :(
But hopefully, once it's completely done, un-rooted, I can get to work moving docs to Documents and PNG's to Images, and hopefully most, if not everything, will be found.

Are all of the files and directories not in one output directory?

> **0011235813 said:**
> I don't know what to do with these .exe and .txt and .elf files. Are they from the previous Windows partition?

Most likely; remember that until the area a file inhabited is overwritten, it's never really gone. ;)

---

### Post by 0011235813 on 2012-02-21
> **Grenage said:**
> Are all of the files and directories not in one output directory?



Most likely; remember that until the area a file inhabited is overwritten, it's never really gone. ;)

Nope, there are several. And I have to look through 'em all. Is there any way to filter them? Like, search for .pdf and .docx etc?

---

### Post by Grenage on 2012-02-21
When you several, are we talking 5-10?  It's chown can be used recusively, so it would affect all subfolders.  Filtering is certainly possible with the *find* tool; it's a very powerful and useful program, and you can specify a lot of criteria.

---

### Post by 0011235813 on 2012-02-21
> **Grenage said:**
> When you several, are we talking 5-10?  It's chown can be used recusively, so it would affect all subfolders.  Filtering is certainly possible with the *find* tool; it's a very powerful and useful program, and you can specify a lot of criteria.

I'm talking directories within my home, not sub-directories.

---

### Post by Grenage on 2012-02-22
Assuming that there are subtantially less non-recovered directories than recovered directories, you could select all, deselect the non-backup directories, then move them to a single directory.  A bit low tech ;)

Your home folder would have particular permissions as its *your* home folder, so if you simply set those permissions on your /home/*user* directory recursively - it will affect everything (including your restored files).

---

### Post by 0011235813 on 2012-02-23
Thanks guys, I was able to recover a good portion of data. I estimate I got about 60-70GB. I am now searching for useful files like docs and images. 
I will update you on how much I've been able to find. I was quite pleased to find that I could recover important documents so easily (well, relatively speaking).

---

### Post by Grenage on 2012-02-24
Glad to hear that you had some luck!

---

