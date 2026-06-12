---
title: "a full system bacckup, HOW?"
date: 2006-05-31
forum: General Help
---

### Post by Isoss on 2006-05-31
I need to get a backup copy for the whole system with every package installed ... just as it is right now, so if I had to format the whole thing I can easily use the backup in minutes to restore my system so I won't be spending a day installing and downloading my packages and managing my desktop and system and everything.

So simply, I am looking fo the right software, with a HOWTO on how to restore the system back. 

Thanks

---

### Post by sparty2809 on 2006-05-31
Try this: 
[http://ubuntuforums.org/showthread.php?t=35087&highlight=Backup+restore+system](http://ubuntuforums.org/showthread.php?t=35087&highlight=Backup+restore+system)

---

### Post by aysiu on 2006-05-31
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by Fatjoint on 2006-05-31
[QUOTE=Isoss]I need to get a backup copy for the whole system with every package installed ... just as it is right now, so if I had to format the whole thing I can easily use the backup in minutes to restore my system so I won't be spending a day installing and downloading my packages and managing my desktop and system and everything.

So simply, I am looking fo the right software, with a HOWTO on how to restore the system back. 

Thanks[/QUOTE]


You could use tar to do that, but your options would be either:

1) backup to floppies (hah, how many disks in 5-10 GB??!)
2) backup to tape and use the M option for multi-span if a single tape doesn't have enough capacity
3) backup to a partition you've created that's large enough, maybe a /backup?

[edit] beaten like a red-headed step child...  The links above have the info you want.

---

### Post by d4ndy on 2006-06-02
I'm right in the middle. I want to backup to a different partition, on the slave drive, so partimage would be great. Except I have a Conexant modem, whose drivers are not on the Live CD, so I can't go online and download unless I'm running the Ubuntu installation on the hard drive, which installs it on the hard drive, not in ram. But while the partition is mounted, I can't image it. :-k 

Is there some way to make a live partimage CD, or perhaps even easier, how can I get the backup.tgz method to create the backup onto another partition instead of the root. I've tried copying the backup.tgz elsewhere (too easy?), but it is resistant.

Any advice would be appreciated. I think I'll go look over that section on permissions, which, to be honest, completely baffled me.

---

### Post by aysiu on 2006-06-02
[QUOTE=d4ndy]
Is there some way to make a live partimage CD[/QUOTE] There already is one:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by Isoss on 2006-06-03
Hey, excuse me, but I was reading the partimage tutorial and then when I came to the installation I stopped at the ```
sudo aptitude update && sudo aptitude install partimage
```

What is aptitude?
I ran this command and I got partimage installed. but I need to know what is that? cuz first I thought it's like apt-get but when I didn't with apt-get it didn't work so it seems different!

I hope you'd explain this to me please.

---

### Post by Isoss on 2006-06-03
Another question concerning the compress level
if I chose "None", and I have 11GB used space of ubuntu and all the programs and  files, how much of free space will I need for backing up the 11GB? I have another partition of 30GB and 6.75GB of free space, is it possible for the 11GB of the ubuntu system and everything to be compressed to a file of not more than 6GB if I chose None for the compress level?

---

### Post by Isoss on 2006-06-03
[EDIT]: Sorry, this was posted accedently!!

---

### Post by Mustard on 2006-06-03
[QUOTE=Isoss]Hey, excuse me, but I was reading the partimage tutorial and then when I came to the installation I stopped at the ```
sudo aptitude update && sudo aptitude install partimage
```

What is aptitude?
I ran this command and I got partimage installed. but I need to know what is that? cuz first I thought it's like apt-get but when I didn't with apt-get it didn't work so it seems different!

I hope you'd explain this to me please.[/QUOTE]
Aptitude is like an improved version of apt-get, to put it simply.  Some people prefer to use it instead of apt-get, and for some tasks it works much more effectively than apt-get ie installing a large number of dependencies, then allowing the removal of all those dependencies when uninstalling.  I'm not sure why the same command didn't work with apt-get.  That should not have occured.  I would guess that it could have been a syntax error in your command when you converted it to using apt-get.

---

### Post by Mustard on 2006-06-03
[QUOTE=Isoss]Another question concerning the compress level
if I chose "None", and I have 11GB used space of ubuntu and all the programs and  files, how much of free space will I need for backing up the 11GB? I have another partition of 30GB and 6.75GB of free space, is it possible for the 11GB of the ubuntu system and everything to be compressed to a file of not more than 6GB if I chose None for the compress level?[/QUOTE]

I'd just mention that I have had trouble restoring the compressed images using partimage, so I would try an uncompressed image first.

If you have a read over the partimage forum you can get an idea of some of the problems that people strike.

---

### Post by aysiu on 2006-06-03
[QUOTE=Isoss]Another question concerning the compress level
if I chose "None", and I have 11GB used space of ubuntu and all the programs and  files, how much of free space will I need for backing up the 11GB? I have another partition of 30GB and 6.75GB of free space, is it possible for the 11GB of the ubuntu system and everything to be compressed to a file of not more than 6GB if I chose None for the compress level?[/QUOTE] The partition image will be the same size as the used space, so if you're using 11 GB, the image will be 11 GB also.

I don't believe the compression formats compress to half the size of the original, but you can also break up the image into pieces... you'd need another place to store the second half of the image, though.

---

### Post by aysiu on 2006-06-03
[QUOTE=Mustard]I'd just mention that I have had trouble restoring the compressed images using partimage, so I would try an uncompressed image first.[/QUOTE] Same here. I do uncompressed for simplicity's sake.

When I tried compressing it, I couldn't simply uncompress and use the image with PartImage. I got some weird error (I forget what it was). When I uncompressed it separately and then used the uncompressed image, it worked fine.

And, of course, it works fine if you never compress the image in the first place.

---

### Post by Isoss on 2006-06-03
Back in windows, although I don't miss it, I had something called image ghost or something! it could compress the whole system to aproximately 1.5GB ... Even if the backed up partition was 15GB of used space! So, infact that's what I am exactly looking for. I could backup 2 Or 3systems on a DVD. If partimage can't do that then I don't think I'll need it cuz I don't have much space, cuz in that case I need to buy an external driver or my laptop and that is not cheap. Hmmmm ... I'll try to check the partimage forum and find some answers and solutions for the problem you've encountered with the compressed images.

Thank you guys.

---

### Post by aysiu on 2006-06-03
I have no experience using it, but you can look into this:
[http://freshmeat.net/projects/g4l/](http://freshmeat.net/projects/g4l/)

---

### Post by Isoss on 2006-06-04
[QUOTE=Mustard]Aptitude is like an improved version of apt-get, to put it simply.  Some people prefer to use it instead of apt-get, and for some tasks it works much more effectively than apt-get ie installing a large number of dependencies, then allowing the removal of all those dependencies when uninstalling.  I'm not sure why the same command didn't work with apt-get.  That should not have occured.  I would guess that it could have been a syntax error in your command when you converted it to using apt-get.[/QUOTE]

Thanks a lot, but question! since it's an improved version of apt-get, why don't users here suggest using it instead when talking about installing stuff? I mean when I ask something in the forums all those who answer would suggest running sudo apt-get install *something* so why not aptitude?

Thanks!

---

### Post by Mustard on 2006-06-04
[QUOTE=Isoss]Thanks a lot, but question! since it's an improved version of apt-get, why don't users here suggest using it instead when talking about installing stuff? I mean when I ask something in the forums all those who answer would suggest running sudo apt-get install *something* so why not aptitude?

Thanks![/QUOTE]
Any answer I give to this question is going to cover ground that has been gone over in other threads ( and far more comprehensively than I can explain in one post).  I would have a search for previous threads comparing apt-get to aptitude and read over the debate. :)

---

### Post by matata on 2006-06-06
hi guys :-)  
what about using dd and gzip commands.
to backup: 

```
dd if=/dev/hda1 | gzip -cfv > image.gz
```

to restore:

```
gzip -cdfv iamge.gz | dd of=/dev/hda1
```

:)

---

