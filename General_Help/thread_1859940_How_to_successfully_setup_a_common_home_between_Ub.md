---
title: "How to successfully setup a common /home between Ubuntu and Fedora?"
date: 2011-10-14
forum: General Help
---

### Post by fantab on 2011-10-14
I have been dual booting Ubuntu and Fedora. I love 'em both. I usually have a separate '/' and '/home' for each distro. One of the disadvantage, for me, of having separate '/home' is that I have to look everywhere (Ubuntu /home and Fedora /home) for any file I have created or downloaded. The size of /home on both is more than 100 Gb. This has become a huge PITA of late.

I am thinking of **dual booting Ubuntu and Fedora with a common and shared '/home' partition**. I have been searching around for a possible solution for doing this with ZERO CONFLICTS, which I am made aware of by reading around. Some reading has suggested that I use different Usernames for each distro sharing a common '/home' and some have suggested exactly the opposite. Some suggest that instead of a common '/home', both distros should be installed with only '/' and have an independent shared data partition mounted and accessible from both distros. And some say I will have to use separate '/etc'.

As we can see all these suggestions have me confused.

Before I request forum's help I would like to breifly explain my needs and expectations with a shared '/home'

[LIST]
[*]I will be using same set of applications on both Distros with same configuration and prefrences. For instance, LibreOffice Writer or Gimp will be installed on both distros and when I create a file and save it to documents or pictures folder I want it to be accessible to either distro whichever I might be using at that time.
[/LIST]

[LIST]
[*]I am afraid that if I use separate Username I will end up with two directories, say /meubuntu and /mefedora does this mean i will have, say two Documents folder one in Ubuntu and one in Fedora? I don't want this as I will be back to same searching for files in different directories.
[/LIST]
Well those are my Primary expectations from a shared /home.

I request the forum (esp. those who have used a common, shared '/home') to **help me set up a common, shared, and trouble free '/home'.**

Thank you for your time.

---

### Post by aeiah on 2011-10-14
it'll probably work, but you might find it better to keep the homes seperate so they have different configs, and just share the same Documents, Pictures, Music, Downloads directories etc through mount --bind or symlinks

---

### Post by WorMzy on 2011-10-14
What I would do (and in fact, actually do *do*) is leave each /home folder on it's respective / partition, and simply have a dedicated partition for "shared" files (Documents, Pictures, Music, etc). I automount this dedicated partition under /media (using fstab), and then bind the respective folders over the home folder's equivalents.

e.g.

Bind /media/Terastore/Documents onto /home/wormzy/Documents
/media/Terastore/Pictures onto /home/wormzy/Pictures

etc.

All the binding is handled by fstab too, so it's all pretty simple.

Here's what the relevant parts of my fstab looks like:

```
UUID=a4e192bc-6c21-4617-9550-3342392ccf6f /home/wormzy/Videos     xfs     defaults                        0 0
UUID=7A5C94995C94522D                     /media/Terastore        ntfs-3g auto,uid=1000,gid=100,umask=002 0 0
/media/Terastore/Collection/              /home/wormzy/Collection none    bind                            0 0
/media/Terastore/Users/WorMzy/Pictures/   /home/wormzy/Pictures   none    bind                            0 0
/media/Terastore/Users/WorMzy/Documents/  /home/wormzy/Documents  none    bind                            0 0
/media/Terastore/Downloads/               /home/wormzy/Downloads  none    bind                            0 0
```

(I have my videos on a separate partition to everything else, and my storage partition is NTFS so I can share with Windows.)

---

### Post by fantab on 2011-10-14
> **WorMzy said:**
> What I would do (and in fact, actually do *do*) is leave each /home folder on it's respective / partition, and simply have a dedicated partition for "shared" files (Documents, Pictures, Music, etc). I automount this dedicated partition under /media (using fstab), **and then bind the respective folders over the home folder's equivalents.**

e.g.

Bind /media/Terastore/Documents onto /home/wormzy/Documents
/media/Terastore/Pictures onto /home/wormzy/Pictures

etc.

All the binding is handled by fstab too, so it's all pretty simple.

Not exactly what I wanted but sounds interesting. **Could you please elaborate on "bind the respective folders over the home folder's equivalents, and if possible with steps to follow?**

Thanks

---

### Post by oldfred on 2011-10-14
I believe Fedora is changing so the UID is 1000 which will greatly simplify any sharing issues. See the posts by Morbius1 as he is really good at mounting and configuring fstab.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)

Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)
HowTo: Create shared directory for local users (with bindfs). - sisco311
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by collisionystm on 2011-10-14
Just pick a distro to change your home folder location and edit the /etc/passwd file 

your home directory is defined in there. Once thats done, log out and back in

---

### Post by ajgreeny on 2011-10-14
> **collisionystm said:**
> Just pick a distro to change your home folder location and edit the /etc/passwd file 

your home directory is defined in there. Once thats done, log out and back in
/etc/passwd?  Are you sure about that?  Edit it in what way; change the UUID?

This is something I have never heard of before and just wanted to double check that you have got it right.

---

### Post by collisionystm on 2011-10-14
Mine


> charles:x:1000:1000:Charles,,,:/home/charles:/bin/bash


NOTE: It says Charles,,, because of the way users are setup in the system.

When type adduser in the terminal it always asks for first name last name phone number address. If you dont put this in, it just uses commas...

ANYWAYS


charles:x:1000:1000:Charles,,,:/home/charles:/bin/bash

Change this part /home/charles:/bin/bash

charles:x:1000:1000:Charles,,,:/newhome/username:/bin/bash

If that does not work, just reverse it.

It should.

i use that to designate default entry points on ssh sessions. In theory it should work for a regular login because it always updated the home path in the gui.

---

### Post by WorMzy on 2011-10-14
> **fantab said:**
> Not exactly what I wanted but sounds interesting. **Could you please elaborate on "bind the respective folders over the home folder's equivalents, and if possible with steps to follow?**

Thanks

Well, after you've set up the partition (using gparted or whatever your preferred partition editor is), get it's UUID by running

```
sudo blkid -c /dev/null
```

Then add an entry in /etc/fstab for it, like I have shown you above.

You'll probably need to make the mount point before you can successfully mount it, so run

```
sudo mkdir /media/Terastore
```

(replacing the /media/Terastore with what ever you've put as your mount point)

Then create a single line for each folder you want to bind somewhere else, writing them like I have in the above example.

---

### Post by fantab on 2011-10-14
> **collisionystm said:**
> Just pick a distro to change your home folder location and edit the /etc/passwd file 

your home directory is defined in there. Once thats done, log out and back in

> **collisionystm said:**
> Mine




NOTE: It says Charles,,, because of the way users are setup in the system.

When type adduser in the terminal it always asks for first name last name phone number address. If you dont put this in, it just uses commas...

ANYWAYS


charles:x:1000:1000:Charles,,,:/home/charles:/bin/bash

Change this part /home/charles:/bin/bash

charles:x:1000:1000:Charles,,,:/**newhome/username:/bin/bash**

If that does not work, just reverse it.

It should.

i use that to designate default entry points on ssh sessions. In theory it should work for a regular login because it always updated the home path in the gui.

I was busy reading all the links suggested by **oldfred** when the above discussion happened.

**collisionystm- **your solution seems to be relatively simple to what I have learned from the above links... Could you please clarify, **"if that does not work, just reverse it**"? Reverse, how? Also what does /newhome mean? will it create a newhome directory?

Q: After editing /etc/passwd will I be able to share '/home' between Ubuntu and Fedora without any conflicts?


Thanks WorMzy...

---

### Post by collisionystm on 2011-10-14
> **fantab said:**
> I was busy reading all the links suggested by **oldfred** when the above discussion happened.

**collisionystm- **your solution seems to be relatively simple to what I have learned from the above links... Could you please clarify, **"if that does not work, just reverse it**"? Reverse, how? Also what does /newhome mean? will it create a newhome directory?

Q: After editing /etc/passwd will I be able to share '/home' between Ubuntu and Fedora without any conflicts?


Thanks WorMzy...

For testing do this.

Create the same username on fedora and ubuntu.

Create a folder in your /home/username directory on either fedora or ubuntu. Whatever one you want to make your temporary HOME FOLDER. 

mkdir /home/username/testhome

edit your /etc/passwd for both Ubuntu and Fedora to point to this folder for their home.

See if it gives your the results you want.

If not, just put the /etc/passwd back to the way it was and reboot.

---

### Post by fantab on 2011-10-14
Thanks **collisionystm,** I will follow your instructions and will post results here.

Fedora 16 will have UID=1000, just like Ubuntu... how much will this help us to share a common home?  Fed16 is due early next month.

---

### Post by dcstar on 2011-10-14
> **fantab said:**
> I have been dual booting Ubuntu and Fedora. I love 'em both. I usually have a separate '/' and '/home' for each distro. One of the disadvantage, for me, of having separate '/home' is that I have to look everywhere (Ubuntu /home and Fedora /home) for any file I have created or downloaded. The size of /home on both is more than 100 Gb. This has become a huge PITA of late.

I am thinking of **dual booting Ubuntu and Fedora with a common and shared '/home' partition**. I have been searching around for a possible solution for doing this with ZERO CONFLICTS, which I am made aware of by reading around.
........

The biggest issue I have found is with different versions of things like Gnome using the same /home.

One version will alter the configuration files in /home and if you then boot back to an earlier version it can get quite confused and cause all sorts of issues.

---

### Post by fantab on 2011-10-15
I had asked in this thread "how to successfully setup a common /home between Ubuntu and Fedora? After much discussion here, and sifting through the search engine results and also reading Fedora Forums about the topic I have come to understand that setting up a common /home for two distros is neither recommended nor practical. There are perhaps too many glitches involved. So **I've decided to have both Ubuntu and Fedora setup within '/' partition only**. This also makes so much sense because I, personally, don't like to do upgrades, I prefer clean installs and having only '/' partition will definitely make things much easier for me than to have a different partitions for '/' and '/home' with all those (dot)files. That basically solves one part of my conundrum.

Now I am faced with the other part. I have a big ext4 Linux Partition (868 Gb) which I want to set up as common storage between Ubuntu and Fedora. I want:

[LIST]
[*]**All the files that I create and download, using either of the Distros, to be stored in this partition.**
[/LIST]

[LIST]
[*]**This Partition should be available to me just as '/home' would be, mounted with all the permissions, available from nautilus and preferably not visible as mounted in both distros.**
[/LIST]
The best solution to this so far seems to be that using **binding** as suggested by WorMzy and others. Again this solution involves using UUIDs. We know that Ubuntu and Fedora are different wrt UID. So **How do I set this up from both distros?**

Is "binding as suggested by WorMzy" same as **bindfs**? I ask this because WorMzy's method only uses **fstab** whereas I have to install **bindfs** to work with it as suggested by [**this thread**]("http://ubuntuforums.org/showthread.php?t=1460472").

Thanks for the patience

---

### Post by WorMzy on 2011-10-15
Bindfs is similar to the bind technique, but it lets you specify ownership and permissions on the mountpoint. It's more useful on NTFS/FAT partitions, which don't support UNIX file permissions. However, if you want to use it, go for it. You'll still need to mount the storage partition somewhere first though.


As for Fedora using UUIDs differently, I don't understand what you mean by that, but you don't have to use UUIDs. You can use the traditional /dev/sd## if you want, but be aware that that form of identity is liable to change. What's /dev/sda1 now, may well be /dev/sdc1 the next time you boot.

If Fedora just doesn't support "UUID=#######" in fstab, then try "/dev/disk/by-uuid/#######" instead. I haven't used Fedora in forever, but I'm sure it'll support mounting by UUIDs in some way.

---

### Post by malspa on 2011-10-15
> **fantab said:**
> I had asked in this thread "how to successfully setup a common /home between Ubuntu and Fedora? After much discussion here, and sifting through the search engine results and also reading Fedora Forums about the topic I have come to understand that setting up a common /home for two distros is neither recommended nor practical. There are perhaps too many glitches involved.

Agreed. I have Ubuntu, Fedora, and other distros installed here, but I keep the /home directories/partitions completely separate, and use a couple of data partitions that can be accessed from each distro. Common /home partitions seem like too much trouble, especially between completely different distros.

---

### Post by fantab on 2011-10-15
> **WorMzy said:**
> Bindfs is similar to the bind technique, but it lets you specify ownership and permissions on the mountpoint. It's more useful on NTFS/FAT partitions, which don't support UNIX file permissions. However, if you want to use it, go for it. You'll still need to mount the storage partition somewhere first though.


As for Fedora using UUIDs differently, I don't understand what you mean by that, but you don't have to use UUIDs. You can use the traditional /dev/sd## if you want, but be aware that that form of identity is liable to change. What's /dev/sda1 now, may well be /dev/sdc1 the next time you boot.

If Fedora just doesn't support "UUID=#######" in fstab, then try "/dev/disk/by-uuid/#######" instead. I haven't used Fedora in forever, but I'm sure it'll support mounting by UUIDs in some way.

Thanks for the clarification about bindfs.

I have manually changed permission in Ubuntu for my /dev/sdb5 (i want to use this partition as common Storage) to make it available to meUser and not just the root. I just mounted /dev/sdb5 by just clicking it from nautilus and it is available for me to read and write. I have not yet used binding.

I logged into Fedora and tried to do the same... in Fedora the ownership belongs to UID=1000 User or something like that and I cannot change the Permissions inspite of trying as root. Nothing. /dev/sdb5 now belongs to Ubuntu and Fedora will have nothing to do with it. 

At this stage I tried what **collisionystm **had suggested and edited /etc/passwd file from Fedora... again nothing... so I undid it. :( 

I am still waiting for response in Fedora Forums. But all the related posts I searched there point to the different UID and the ensuing incompatibility. None offers an applicable solution so far. Meanwhile I will set permissions in Fedora and try to access it in Ubuntu.

Have I run into a wall?:confused:

---

### Post by oldfred on 2011-10-15
See this post and suggestions by Morbius1 on setting up groups:

[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by dcstar on 2011-10-15
> **fantab said:**
> I had asked in this thread "how to successfully setup a common /home between Ubuntu and Fedora? After much discussion here, and sifting through the search engine results and also reading Fedora Forums about the topic I have come to understand that setting up a common /home for two distros is neither recommended nor practical.
..........

You can use a common /home ***if*** you use different user accounts on each system you boot from so the actual file trees under /home used by each OS are different (and therefore are only used by one OS).

If you have different /home top level folders then you can basically "share" the next level of folders between them using links and by setting the permissions correctly - that way you can share common data storage areas. You may have to hack the UID of accounts to get them to match across different Linux OSs.

You may also be able to initially set up accounts on each Linux OS that create individual /home folders, and then rename the accounts to they are all the same across your OSs (but the original name of the /home folders remains). I haven't tried this but it may work.

---

### Post by fantab on 2011-10-18
I installed **FEDORA 16** _*Beta*_ yesterday. 

Wow... the Linux Partition, which I wanted to set up as a common /storage between Ubuntu and Fedora is working out of the box on Fedora 16. FYI** Fedora 16 has changed to UID=1000** and it is great news for someone like me trying to share a common Linux Partition.

I have not applied BINDING or bindfs. What I am doing is** I have just set the save path in, for instance LibreOffice, to the Shared Linux Partition-Documents in both the distros**. All I have do is mount the said Partition before saving and its working. My downloads are also pointed to save in the shared partition. All my data is being saved where I want  it.

So far I have had no problems following this method. :grin:
Lets see if something shows up....

Until then
Thank you all for your help.

---

### Post by WorMzy on 2011-10-19
I only suggested the binding because I thought it'd be easier for you (if, like me, you're used to saving things in ~/Downloads, or making documents in ~/Documents, etc.). It was only ever optional. If you can get by without it, then feel free to do so. :)

Anyway, I'm glad you've got it sorted.

---

