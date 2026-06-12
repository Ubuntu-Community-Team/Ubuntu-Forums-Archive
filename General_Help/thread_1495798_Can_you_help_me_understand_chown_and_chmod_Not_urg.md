---
title: "Can you help me understand chown and chmod? Not urgent."
date: 2010-05-28
forum: General Help
---

### Post by kansasnoob on 2010-05-28
For quite some time I've been multi-booting (sometimes as many as 10 or 12 OS's) and I discovered long ago that symlinking to separate data partitions is a great way of always having access to the newest Documents, Downloads, etc.

Like if I'm playing around in Squeeze or Maverick and something suddenly goes south I can boot into my stable OS and everything I've been working on is right there. That's also helpful when I start first thing in the AM as I don't have to remember which OS I was using last :)

Anyway I know how to do everything needed to complete that process now using only the command line, basically either "rm" or "mv" the old directories if they exist, then:

gksudo gedit /etc/fstab

and add:

#/dev/sda5    /mnt/sda5 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda5       ext3    defaults          0       2
#/dev/sda6    /mnt/sda6 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda6       ext3    defaults          0       2     
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda8       ext3    defaults          0       2

Then create the directories:
               
sudo mkdir /mnt/sda5 && sudo mkdir /mnt/sda6 && sudo mkdir /mnt/sda7 && sudo mkdir /mnt/sda8

And create the symlinks:

ln -s /mnt/sda5 /home/lance/Backups && ln -s /mnt/sda6 /home/lance/Pictures && ln -s /mnt/sda7 /home/lance/Downloads && ln -s /mnt/sda8 /home/lance/Documents

**[COLOR="Red"]Now, here's the catch![/COLOR]** So far I've always failed with the chown and chmod process :(

After completing all of the above successfully I've just been using the GUI to correct ownership and privileges as such:

[ATTACH]158561[/ATTACH]

While that works perfectly and can hardly be considered difficult I have the desire to learn how to complete that final step using the CLI :)

Any advice will be appreciated.

---

### Post by jobix on 2010-05-28
Why don't you open up a terminal (Applications->Accessories->Terminal) and execute these commands:
> man chmod
man chown

That should get you started and when you run into trouble, you can always come back and post here.

---

### Post by Elfy on 2010-05-28
I found this page on chmod particularly helpful as you can see an easy representration of what you are doing 

[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

This also - [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I guess without knowing why and how it fails for you it's hard to offer anything more concrete than that.

---

### Post by kansasnoob on 2010-05-28
> **jobix said:**
> Why don't you open up a terminal (Applications->Accessories->Terminal) and execute these commands:

That should get you started and when you run into trouble, you can always come back and post here.

Been there and done that. I'd obviously researched this considerably to get as far as I have.

Somehow I simply always get something wrong when I try to correct ownership and permissions using the command line.

---

### Post by Morbius1 on 2010-05-28
I'm a little slow today so let me see if I've got this right:

You're mounting /dev/sda5 to /mnt/sda5
Then you're creating a link from /mnt/sda5 to /home/lance/Backups
Then you're correcting ownership to all enclosed folders and files in /home/lance/Backups so that lance can read and write to them.

Don't you have to do that every time you boot into one of the other 12 OS's. Unless you have a "lance" on every other OS and that lance has the same user number ( i.e., in Ubuntu it's 1000 , in Mandriva it's 500 ), that's kind of awkward.

---

### Post by kansasnoob on 2010-05-28
> **forestpiskie said:**
> I found this page on chmod particularly helpful as you can see an easy representration of what you are doing 

[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

This also - [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I guess without knowing why and how it fails for you it's hard to offer anything more concrete than that.

That second link may be just the ticket :)

How did I manage to overlook that :confused:

Sometimes a second pair of eyes is needed, I'll parse that a bit and see if I can boil it down.

Many thanks.

If I encounter a failure I'll try to post all pertinent info.

---

### Post by kansasnoob on 2010-05-28
> **Morbius1 said:**
> I'm a little slow today so let me see if I've got this right:

You're mounting /dev/sda5 to /mnt/sda5
Then you're creating a link from /mnt/sda5 to /home/lance/Backups
Then you're correcting ownership to all enclosed folders and files in /home/lance/Backups so that lance can read and write to them.

Don't you have to do that every time you boot into one of the other 12 OS's. Unless you have a "lance" on every other OS and that lance has the same user number ( i.e., in Ubuntu it's 1000 , in Mandriva it's 500 ), that's kind of awkward.

Well, so far I've mostly stuck with Debian based distros, but I did once throw Fedora into the mix and encountered no real problems other than having to use the GUI method of correcting permissions/ownership.

No problem so far with permissions changing in one distro after linking to another distro, but anything could happen :P

As I said this is not urgent, just something I'd like to understand better.

---

### Post by Morbius1 on 2010-05-28
But you're in an infinite loop. You correct ownership in Ubuntu, change ownership in Fedora, and then have to change ownership In Ubuntu again. Am I missing something?

---

### Post by Slackware-fan on 2010-05-28
your best be would be to make sure your user id is always the same number as suggested earlier.  I'm guessing you just want to do a recursive chown and perhaps a chmod?  I would imagine chown alone would fix your permission issues so you might not need chmod

sudo chown -R lance /mnt/sda5 /mnt/sda6  /mnt/sda7 /mnt/sda8 

also you might want to include your user group in the command wheras you pass user:group

for example

sudo chown -R lance:users /mnt/sda5 /mnt/sda6 /mnt/sda7 /mnt/sda8

that would recursively change ownership on everything to user lance and group users

if you really want to get creative you could put all of this stuff in /etc/rc.local (assuming that is used in ubuntu) and have it run automatically when the system boots

---

### Post by Morbius1 on 2010-05-28
Since you have 12 OS's and apparently like to tinker I would suggest the following alternative that you might want to try out.

I have a common linux data partition /DATA and use the following two lines in the fstab of every linux OS installed on my system:
```
 LABEL=Data /DATA           ext3    defaults,noatime        0       2
 bindfs#/DATA /home/Shared fuse perms=0666:+X 0 0
```/home/Shared will "bind" to /DATA with all it's content except:

All existing and new files added in /home/Shared will have permissions set to 666 - universal read / write.
All existing and new directories in /home/Shared will have permissions set to 777 so they can be opened.

Conceptually it's exactly the same thing you're trying to achieve with the fstab mount, symbolic link, and chmod.

BINDFS HowTo: [http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

Just an idea.

---

### Post by kansasnoob on 2010-05-28
> **Morbius1 said:**
> But you're in an infinite loop. You correct ownership in Ubuntu, change ownership in Fedora, and then have to change ownership In Ubuntu again. Am I missing something?

So far that's not been an issue. I've never had to correct ownership or permissions after initially setting things.

I see that I didn't bother setting up symlinks in Fedora because I was only doing grub 2 testing ATM:

[http://ubuntuforums.org/showpost.php?p=8893359&postcount=341](http://ubuntuforums.org/showpost.php?p=8893359&postcount=341)

that link brought me here:

[http://ubuntuforums.org/showpost.php?p=8893128&postcount=40](http://ubuntuforums.org/showpost.php?p=8893128&postcount=40)

and the tar.gz shows that I didn't symlink the data partitions (in fact I didn't even deselect the unwanted SWAP):

```
=============================== sdb2/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Sat Feb 27 21:07:49 2010
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1 /                       ext4    defaults        1 1
UUID=dcdced28-c63f-4405-b143-05876492b04d /home                   ext4    defaults        1 2
UUID=2897adb6-b16f-4ba7-901f-2aec9e1c994d swap                    swap    defaults        0 0
UUID=58aec1b2-6dfe-4f02-b77d-207fe6cc5551 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
```

Thanks for the warning though. ATM I have only Ubuntu and Mint:

```
/dev/sda1: LABEL="Maverick" UUID="b7a0df33-53e4-4f0d-856b-0da92ff0d743" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: LABEL="Karmic" UUID="1332b9d0-cf18-4299-9094-12acbdac91ad" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: LABEL="Lucid" UUID="dea3fd63-7af4-4fe9-a923-18baf17dd0eb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: LABEL="Backups" UUID="594c3d40-2791-4c0a-8644-d9812545da2d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="Pictures" UUID="8a3f6c83-cb52-4caf-96b8-5faf2c830453" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="Downloads" UUID="05289ee4-d681-4806-b6fd-aefd784f9323" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="Documents" UUID="571cfad8-68c7-4703-883e-c0baa2a381d4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="9ebb3f20-c774-4547-911f-a5af439aee27" TYPE="swap" 
/dev/sda10: LABEL="Isadora" UUID="f223fe5d-3acb-4d96-950c-62661ad8714b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: UUID="40fc650a-3369-4843-be25-63af8a44d5f2" TYPE="ext2" 
/dev/sda12: UUID="8af37927-9e67-4df7-8e11-1e4b4b455c36" TYPE="ext2" 

```

And I really only care about Debian based distros :)

---

### Post by kansasnoob on 2010-05-28
> **Slackware-fan said:**
> your best be would be to make sure your user id is always the same number as suggested earlier.  I'm guessing you just want to do a recursive chown and perhaps a chmod?  I would imagine chown alone would fix your permission issues so you might not need chmod

sudo chown -R lance /mnt/sda5 /mnt/sda6  /mnt/sda7 /mnt/sda8 

also you might want to include your user group in the command wheras you pass user:group

for example

sudo chown -R lance:users /mnt/sda5 /mnt/sda6 /mnt/sda7 /mnt/sda8

that would recursively change ownership on everything to user lance and group users

if you really want to get creative you could put all of this stuff in /etc/rc.local (assuming that is used in ubuntu) and have it run automatically when the system boots

That looks very helpful.

Of course I'll have to parse everything and give it a trial run.

I really appreciate the suggestions :)

We learn by asking, trying, and quite often failing, but a winner never quits!

---

### Post by kansasnoob on 2010-05-28
> **Morbius1 said:**
> Since you have 12 OS's and apparently like to tinker I would suggest the following alternative that you might want to try out.

I have a common linux data partition /DATA and use the following two lines in the fstab of every linux OS installed on my system:
```
 LABEL=Data /DATA           ext3    defaults,noatime        0       2
 bindfs#/DATA /home/Shared fuse perms=0666:+X 0 0
```/home/Shared will "bind" to /DATA with all it's content except:

All existing and new files added in /home/Shared will have permissions set to 666 - universal read / write.
All existing and new directories in /home/Shared will have permissions set to 777 so they can be opened.

Conceptually it's exactly the same thing you're trying to achieve with the fstab mount, symbolic link, and chmod.

BINDFS HowTo: [http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

Just an idea.

That's also quite helpful.

Since my focus is largely on Debian based distros and I've encountered no problems using the GUI method I think I'll focus just on how to accomplish that using the CLI.

What I really like about my method is being able to follow the "native" path to Documents, Pictures, or Downloads with no other tweaking or searching. It mostly comes down to personal preference.

That's what I love the most about Linux. You can tweak the heck out of it to make it truly your own. And other Linux users are almost always helpful :)

Particularly Ubuntu users :guitar:

---

### Post by kansasnoob on 2010-06-01
Just finally had time to play with this some more and it turned out to be very simple:

```
sudo chown lance:lance /mnt/sda5 /mnt/sda6 /mnt/sda7 /mnt/sda8
```

You'll notice I decided to drop the Recursive bit as it wasn't needed and could be hazardous. I also found I could shorten one command from:

sudo mkdir /mnt/sda5 && sudo mkdir /mnt/sda6 && sudo mkdir /mnt/sda7 && sudo mkdir /mnt/sda8

to:

sudo mkdir /mnt/sda5 /mnt/sda6 /mnt/sda7 /mnt/sda8

Anyway I'm marking this solved and many thanks to all that helped :)

---

