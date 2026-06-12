---
title: "Recovering Win98 Files HELP!"
date: 2010-07-17
forum: General Help
---

### Post by smerdyakov on 2010-07-17
Hi all, 

I am working a friend's ancient windows 98 pc. When the pc boots up, they get a message saying "verifying DMI pool" and a hang. I figured out the problem seemed localized in the drive, so I decided to fire up a 10.4 partition I had on another computer and mount the old drive in it. The problem is that 10.4 will not mount the drive. I can see the drive (with 0 partitions! oh no!) in disk management. 

So, I am using test disk, and I see 2 fat 32 partitions when I analyze it. As well as invalid boot sector. 

I am not really sure how to proceed safely, without destroying my friend's valuable data. Is there anyway I can make a wholesale copy of the drive before I try to repair partitions? Any tips on recovering individual files (perhaps with photorec) before I proceed? A lot of the files are wordperfect files (they showd up as .f) and I am having trouble seeing them. I would like to return the disk to a mountable state and they just do a wholesale copy. 

I am a bit of a noob here, so please forgive me for not giving enough information. I am more than happy to fill you in if you have questions!

Thanks,
Smerdyakov

---

### Post by linuxman94 on 2010-07-17
You can use cloneilla to make a bit for bit copy of his hardrive onto another hardrive of equal or greater size.

[http://www.clonezilla.org]("http://www.clonezilla.org")

---

### Post by WorMzy on 2010-07-17
If the disk is as old as his OS, then it could be on it's last legs. If the disk is spinning fine, but the laser's running out of fuel then understandably you'll get mixed results while trying to read the contents of the disk. I don't think there's much you can do in that circumstance.

EDIT: I think I'm confusing hard drives with CD drives. Ignore the above.

---

### Post by smerdyakov on 2010-07-17
Thanks for the replies! I will check out clonezilla. 

I have been using test disk. My initial results look like this 

[[IMG]http://i816.photobucket.com/albums/zz84/frostyrootbeer/th_1ststeppng.png[/IMG]](http://s816.photobucket.com/albums/zz84/frostyrootbeer/?action=view&current=1ststeppng.png)


When I analyze i get this: 
[[IMG]http://i816.photobucket.com/albums/zz84/frostyrootbeer/th_Screenshot-1.jpg[/IMG]](http://s816.photobucket.com/albums/zz84/frostyrootbeer/?action=view&current=Screenshot-1.jpg).


Then when I do a deeper search I am presented with the option to write the partition here: 
[[IMG]http://i816.photobucket.com/albums/zz84/frostyrootbeer/th_Screenshot-2.jpg[/IMG]](http://s816.photobucket.com/albums/zz84/frostyrootbeer/?action=view&current=Screenshot-2.jpg)

What should I do? Should I go ahead and just write the partition? It seems like the correct structure, but I don't know what the disk looked like before and don't want to risk erasing everything. Is that where clonezilla can come in and help me? (Will clonezilla clone if the disk won't mount?)

Thanks again, I really want to get the data to these friends of mine. It is of immense value to them!

Edit: is it possible to mount these file systems without rewritting the partition values? [see the middle of [this]("https://help.ubuntu.com/community/DataRecovery") post under section header "https://help.ubuntu.com/community/DataRecovery"]?

---

### Post by Joe of loath on 2010-07-17
Firstly, DD an image of the disk, with the command:

```
dd if=/dev/hd(letter here) of=/(path for image).dd
```

It will take a while, but you will have a BLOCK BY BLOCK copy of the drive. If you screw up when repairing it, reverse the command and it'll bring it back to how it started. Clonezilla will do the same thing, but I prefer dd.

---

### Post by smerdyakov on 2010-07-17
Joe, 

I just want to double check that I am have the right idea (and commands). 

The drive (which won't mount normally) is at /dev/sdb in disk manager. 

So to DD the drive i would input 
```
dd if=/dev/sdb of=/backup.dd
```

Correct? Thanks for bearing with my inexperience.

---

### Post by Joe of loath on 2010-07-17
You'll want to put it in a directory. For example, I would put it in /home/joe/image.dd. I suggest you do something similar.

Just make sure you have as much disk space spare to fit the whole drive in, as a 20gb drive (for example) will give a 20gb image.

You've got to do it as root (so using sudo) IIRC too.

---

### Post by smerdyakov on 2010-07-17
Thanks Joe. I think it is working? Is there any visual feedback in terms of progess for DD? 

This was the code: 
> sudo dd if=/dev/sdb of=/backup.dd

---

### Post by Joe of loath on 2010-07-17
I'm not sure if it will work copying it into /, although it might.

There's no visual progress, you just have to wait. It'll take a while, too.

---

### Post by smerdyakov on 2010-07-17
Okay, got it! I copied both a .dd file and an .img file. 
What should I do if I want to restore in the future? 

Now that I have it backeed up, should I go ahead and write the partition in test disk? Or are there anyother ways that I can get at the files? What about force mounting the sectors?

Thanks again!

---

### Post by Joe of loath on 2010-07-17
did you cancel one command and re-run it after changing the extension? One of them will be the size of the disk, that's the finished one that you'll want to keep safe.

Do whatever to the disk now, if it screws up run the command so that the if= argument points to the image, and the of= to the disk and it'll all be back as it was. You can also copy the image and mount it directly, so you can keep the disk as it is.

---

### Post by smerdyakov on 2010-07-17
Well, test disk worked its magic. The drive now mounts under ubuntu and XP, but the drive name is just a series of numbers. All the program files are seemingly intact, but I can't find the documents that my friends need. Could this be because of writing the wrong partition data?

The drive itself won't boot; it sticks at "verifying dmi pool" when I try to boot it in its original machine. 

That's more of a windows 98 problem then an ubuntu one, but I figured ya'll might know of a way to fix it from ubuntu : )

---

### Post by smerdyakov on 2010-07-18
I think I am going to DD the image back; my only problem is that I don't want to screw up whatever data I have recovered. 
I think the filesystem that I want is the fat 16 one originally scene in the first screencap. 

Can I just dd the file that I originally took on to another IDE drive? If the drive is significantly bigger will that matter?

---

### Post by smerdyakov on 2010-07-22
Any idea why certain documents and folders show up in test disk and ubuntu (the win98 ones) but other DOS documents on the same partition do not? I have not heard of partial corruption like that. Of course the things that don't show are things I need.

---

