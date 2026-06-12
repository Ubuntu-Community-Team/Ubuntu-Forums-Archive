---
title: "Cannot access USB drive in Ubuntu"
date: 2009-10-06
forum: General Help
---

### Post by DeanoCeltic on 2009-10-06
Hi everyone. I'm an Ubuntu newbie so please be patient! I have a usb drive that is formatted (elsewhere) in Ext3 and my computer can't write to it. When I inserted it, it shows up and I can read from it but cannot copy files to it. The Properties->Permissions page is blank, no info at all.

I've been searching through the forums and went through some things before posting so here's what I have done. I unmounted the drive and ran **sudo fsck /dev/sbd1**. It came back 'clean' with the number of files & blocks. I mounted the drives and attempted to paste to them but still could not.

The big difference now is that in the Permission tab of the Disc Properties, there is some information (this was completely blank before). It shows -
Owner: 1001 - user #1001 Create and delete files
Group: 1001 - Access Files
Others: Access files
SELinux context: unknown

Everything is greyed out and - "You are not the owner so you cannot change these permissions".

Also, the output for **sudo mount** gives -
[B]/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodevuhelper=hal)

[/B]Any help greatly appreciated. Thanks! [B]:)
[/B]

---

### Post by unmole on 2009-10-06
do a 
```
sudo chown -R username /dev/sdb1 
``` replase username with your username

---

### Post by DeanoCeltic on 2009-10-06
Thanks for the suggestion unmole. I ran the command **sudo chown -R ubuntu /dev/sdc1** and nothing happened (cursor went to new line. I tries this with both the drive mounted and unmounted.

I still cannot get write access to the disc and the Permissions tab is greyed out again - "The permissions of disc-1 could not be determined."

Is there anything else I can try?

---

### Post by DeanoCeltic on 2009-10-06
Oh - BTW, there is no info on this drive so I am open to reformatting it in Ubuntu if that will give me access. This was originally formatted on another machine for media use and the command **tune2fs -m 0 /dev/sdb1** was run to give maximum capacity.

I guess I could reformat and run this command again?

---

### Post by DeanoCeltic on 2009-10-06
Reformatted the drive in Ext3 and still cannot write to it. Aaagh! Please help :(

---

### Post by nothingspecial on 2009-10-06
> **DeanoCeltic said:**
> Oh - BTW, there is no info on this drive so I am open to reformatting it in Ubuntu if that will give me access. This was originally formatted on another machine for media use and the command **tune2fs -m 0 /dev/sdb1** was run to give maximum capacity.

I guess I could reformat and run this command again?

You need to mount it before you can chown it.
```

sudo mkdir /media/drive/
```
```

sudo mount -t ext3 /dev/sdb1/ /media/drive/
```

```
sudo chown -R username:username /media/drive/
```

---

### Post by DeanoCeltic on 2009-10-07
[COLOR=Black]Thanks nothingspecial - I'm in work and I'll try that when I get home.

I would have thought though that completly re-formatting a disc would automatically give me full access? :confused:
[]("http://ubuntuforums.org/member.php?u=491516")[/COLOR]

---

### Post by Zimmer on 2009-10-07
Extra tip, when you have write access to the drive create a folder on it and then alter permissions on the folder to allow acces to everyone.... because if you don't quite get the permissions on the root of the drive correct you may discover you have a problem writing to the drive if it is plugged into a different machine.  (I know this is not best practice, but, hey, it works for me...)

---

### Post by DeanoCeltic on 2009-10-07
> **Zimmer said:**
> Extra tip, when you have write access to the drive create a folder on it and then alter permissions on the folder to allow acces to everyone.... because if you don't quite get the permissions on the root of the drive correct you may discover you have a problem writing to the drive if it is plugged into a different machine.  (I know this is not best practice, but, hey, it works for me...)

Thanks Zimmer - access to everyone will work fine.  The drive will only contain non-sensitive data.

---

### Post by DeanoCeltic on 2009-10-07
> **nothingspecial said:**
> You need to mount it before you can chown it.

```
 sudo mkdir /media/drive/
``` **sudo mkdir /dev/sdc1/newfolder **resulted in
nkdir: cannot create directory 'dev/sdc1/newfolder': Not a directory

```
 sudo mount -t ext3 /dev/sdb1/ /media/drive/
```Would not work because of the above

```
sudo chown -R username:username /media/drive/
```. Mounted the drive and ran **sudo chown -R ubuntu /dev/sdc1**. This just resulted in a carriage return and I still cannot get access. In your code username:ubuntu comes back with an invalid user.

:(

---

### Post by DeanoCeltic on 2009-10-07
> **Zimmer said:**
> Extra tip, when you have write access to the drive create a folder on it and then alter permissions on the folder to allow acces to everyone.... because if you don't quite get the permissions on the root of the drive correct you may discover you have a problem writing to the drive if it is plugged into a different machine.  (I know this is not best practice, but, hey, it works for me...)

I don't have write access Zimmer - that's the problem. :(

---

### Post by DeanoCeltic on 2009-10-07
I am happy to reformat the disc if this will give me access. I tried this already but it failed to give me access. The format seemed to work fine using 
```
sudo mkfs.ext3 /dev/sdc1 
```

I'm still getting 'The permissions of "1500.3GB Media" could not be determined in the Permissions tab.

I'm happy to start again from scratch if someone can help me.

Thanks

---

### Post by nothingspecial on 2009-10-07
> **DeanoCeltic said:**
> ```
 sudo mkdir /media/drive/
``` **sudo mkdir /dev/sdc1/newfolder **resulted in
nkdir: cannot create directory 'dev/sdc1/newfolder': Not a directory

```
 sudo mount -t ext3 /dev/sdb1/ /media/drive/
```Would not work because of the above

```
sudo chown -R username:username /media/drive/
```. Mounted the drive and ran **sudo chown -R ubuntu /dev/sdc1**. This just resulted in a carriage return and I still cannot get access. In your code username:ubuntu comes back with an invalid user.

:(

You can`t create a directory in /dev/sdc1

Create it in /media (or anywhere else ...... except /dev)


```
sudo mkdir /media/newfolder
```

```
sudo mount -t ext3 /dev/sdb1/ /media/newfolder/
```

The contents of /dev/sdb1 will now be in /media/newfolder

---

### Post by DeanoCeltic on 2009-10-07
> **nothingspecial said:**
> You can`t create a directory in /dev/sdc1

Create it in /media (or anywhere else ...... except /dev)


```
sudo mkdir /media/newfolder
``````
sudo mount -t ext3 /dev/sdb1/ /media/newfolder/
```The contents of /dev/sdb1 will now be in /media/newfolder

Thanks for your continuing help Nothingspecial!

I ran those two commands and I can now see a folder called newfolder in the media folder.

Just to be clear, I could always read the contents of /dev/sbd1, the problem is when I try to write to it. the above commands do not help unfortunately.

---

### Post by nothingspecial on 2009-10-07
Now

```
sudo chown -R your_username:your_username /media/newfolder/
```

That makes you the owner

Then

```
chmod -R 777 /media/newfolder/
```

This sets the permissions on the drive. Please note that -R 777 will let any user on your system read, move, delete, run any file in any folder on it. If you are unhappy with that (maybe it is your media drive and your missus has an account) post back with the permission variation you want.

If that doesn`t work I`m at a loss.

I`ve always used gparted although I know about mkfs. I`m guessing if you _sudo_ mkfs, which I suppose you have to, then root will own the drive, you just have to get root (sudo) to make it yours. 

I`d love to be corrected on this if I am wrong.

---

### Post by bigboy_pdb on 2009-10-07
I've had the same problem before and I tried doing what Zimmer suggested (back then) and it works.

If you can't change the permissions for the root directory of the drive, you can create a folder/folders as root and change the permissions so that you have access to the folder/folders.

---

### Post by nothingspecial on 2009-10-07
Guess , it doesn`t matter after seeing the next post. 


Post deleted

---

### Post by DeanoCeltic on 2009-10-07
NS - I don't understand what you walked me through but I now have access! Just when I was ready to throw the towel in! :redface:

Thanks a million for your help! =D>

---

### Post by nothingspecial on 2009-10-07
I`ll try and put it simply if I can.

/dev/sd?? is not a directory as such, it is the location of a device.

To use that device you have to mount it.

You have to mount it to a location in the linux file system.

You were trying to modify the permissions/ownership of a device ,which you cannot do unless it is mounted.

So the first step was to mkdir blah (make a directory)

Then to mount it mount (mount) -t ext3 (ext3 filesystem) /media/blah (where you want to mount it to)

When you create a file or directory (folder), you own it. Because you had used sudo (meaning you act as root) mkfs, root owns the directory (I`m still not sure of this).

So, you have to use sudo (act as root) to change the owner to you (chown) and once you own it, you can then chmod (change permissions) without sudo.

I hope that makes sense.

But, I`m sure, after all this, you probably couldn`t give a monkeys. :P

Now the bad news. Although Ubuntu is very nice at mounting external media (usually). In your case, I`m afraid you might have to manually mount this device every time you boot - AFAIK (it always used to be that way - maybe it`s changed)

To overcome this you`re going to have to have a go at [[COLOR="Magenta"]fstab[/COLOR]]("https://help.ubuntu.com/community/Fstab")

---

### Post by Zimmer on 2009-10-07
Perhaps a look at some Tuxfiles might help .... (in the fstab area, maybe..)
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

[http://www.tuxfiles.org/linuxhelp/dirs.html](http://www.tuxfiles.org/linuxhelp/dirs.html)

---

### Post by DeanoCeltic on 2009-10-08
Thanks guys. I'm determined to give Linux a try and after a frustrating start, I'm in no rush. I even bought an Ubuntu book today :P

---

