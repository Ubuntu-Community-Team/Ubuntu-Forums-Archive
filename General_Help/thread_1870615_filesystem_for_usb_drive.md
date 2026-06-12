---
title: "filesystem for usb drive"
date: 2011-10-27
forum: General Help
---

### Post by switzel on 2011-10-27
This question is not new, but I have not seen a satisfactory answer yet:

What is a good filesystem to use on an external hard disk?

* vfat used to be good but today it is out of the question because of the file size limitation.
* ext* would be great, but the permissions will cause confusion (no, I don't have root access on all computers I want to connect the drive to so as to adjust the uids, and no, I don't want to adjust the file permissions of every newly created file manually to 777)
* ntfs is good in principle, but it's not native and therefore support is not really great (I mean it is good for everyday usage, but there are consistency checks one can only do out of windows)
* ...?

Am I missing something or is this really still an issue? Someone suggested a wrapper around ext2 which automatically adjusts the file permissions. I would be happy with that, does it exist? Thanks for any suggestions!

---

### Post by 11jmb on 2011-10-27
ntfs is probably your best bet.

Do you plan on changing ownership and permissions? I believe that is one of the only real problems with ntfs in linux

---

### Post by switzel on 2011-10-27
No, I don't care for ownership and permissions as long as they don't get in my way.
The reason why I'd rather not use ntfs is that I vaguely remember having had to fix some ntfs disk (not mine) with a consistency problem. After trying for a while, the solution turned out to be to connect it to a windows computer which did "something" to it during boot time and that was it. And I think that I couldn't have done "something" with the linux tools I had, because otherwise it would have been one of the things that I had tried before.

---

### Post by 11jmb on 2011-10-27
It certainly is not perfect but here are your alternatives:

ntfs: not native on linux, wrapper is not perfect, any consistency issue that may arise has to be fixed on windows

ext: I assume that you are asking this because you want a drive to work well on linux and windows. If this is the case ext is out IMO

fat: file size limit

I guess you will just have to pick what is the least of those evils

---

### Post by viperdvman on 2011-10-27
I hope Linux starts supporting exFAT soon... though I'm not sure how good exFAT compared to NTFS.

I've had no problems with my NTFS volumes on either of my computers. Then again, all my NTFS volumes are internal.

---

### Post by 11jmb on 2011-10-27
> **viperdvman said:**
> I hope Linux starts supporting exFAT soon... though I'm not sure how good exFAT compared to NTFS.

I've had no problems with my NTFS volumes on either of my computers. Then again, all my NTFS volumes are internal.

Its a bit more of a problem for external drives, because the consistency errors are often caused by premature unplugging

---

### Post by switzel on 2011-10-27
edit: this replies to #4
No! I don't care about working on windows. I want it only to work on linux. That's what surprises me so: even in a pure linux context should ntfs be my only option?! In my opinion ext is out because I don't see a way to solve the problem with the permissions.
(A filesystem for an external drive should not have permissions unless it is encrypted, because anyone could override them anyway.)

---

### Post by 11jmb on 2011-10-27
Sorry about that, i missed your initial point, then.

I was under the impression that you could just mount your external drive and then

```
chmod -R 777 external_drive_location
```

I'm not 100% on that tough, but if thats the case, ext would be your best choice

---

### Post by switzel on 2011-10-28
Yes, but the thing is, I would have to do it every time before I disconnect the drive. And if I forget it once, I can't read the new files before getting to a computer where I have root access (or to the computer, where I wrote them). Also, I would have files by all sorts of owner-uids (which is not really a problem, just strange).

@viperdvman: yes, I guess exFAT is very much in spirit what I'm looking for: a modern filesystem but at the same time simple. But for example the computer I am writing this on is running a 2.6.18 kernel, so it's anyones guess when this will support exFAT. (And of course, it's again not native, though I imagine it wouldn't be as much of a problem as for ntfs).

---

### Post by switzel on 2011-11-07
If someone with the same problem happens to read this thread, here is my workaround:
I put this skript

```

#!/bin/bash

dir=`dirname $0`
chmod -R go=u $dir
if [ $EUID -eq 0 ]
then
  chown -R 1000:1000 $dir
fi

```on the disk and (hopefully) run it before every unmount to adjust the file permissions. Whenever possible I run it as root to adjust the ownership.
Still (especially with flash memory in mind) I think there should be an open filesystem specially for external media. If someone feels to be up to such a project (which I don't) I am ready to assist as far as I can.

---

### Post by coffeecat on 2011-11-07
> **switzel said:**
> Yes, but the thing is, I would have to do it every time before I disconnect the drive.

No, you don't. :)

It seems to be a little understood fact that you can actually chown and chmod the ext filesystem itself by chowning and chmodding the mountpoint while it is mounted. 

In a system where you have admin access, mount the drive to /media/mountpoint. Then:

```
sudo chown 1000:1000 /media/mountpoint
sudo chmod 777 /media/mountpoint
```

No -R option - no recursion necessary.

What you are doing is chmodding and chowning the filesystem itself, not the mountpoint, which you can prove to yourself by doing a "ls -l /media" before and after every stage of the process.

Once you've done the above, you will be able to write from any system without root access. The reason for doing the chmod is that some distros set the UID for the first user to 500, not 1000. Of course, this will cause you permissions problems when reading some files if you run such a distro.

---

### Post by switzel on 2011-11-07
That would be interesting, but it seems this fact is even unknown to my linux system:
```

$ sudo chmod 777 /media/fs/
$ sudo touch /media/fs/test
$ touch /media/fs/test
touch: kann &#8222;/media/fs/test&#8220; nicht berühren: Keine Berechtigung

```What the ls -ld /media/fs proves is just that the root folder of the filesystem has the expected permissions (ownerships).

---

### Post by coffeecat on 2011-11-07
You need to chown as well.

---

### Post by switzel on 2011-11-07
```

$ sudo chown 1000:1000 /media/fs/
$ sudo chmod 777 /media/fs/
$ sudo touch /media/fs/test
$ touch /media/fs/test 
touch: kann „/media/fs/test“ nicht berühren: Keine Berechtigung

```

---

### Post by coffeecat on 2011-11-07
> **switzel said:**
> ```

$ sudo touch /media/fs/test
$ touch /media/fs/test 
touch: kann &#8222;/media/fs/test&#8220; nicht berühren: Keine Berechtigung

```

You're trying to touch a file as an ordinary user, overwriting a root owned one. That won't work. Either delete the root-owned test file with sudo rm first, or:

```
touch /media/fs/test1000
```

---

### Post by switzel on 2011-11-08
Either you don't understand what my problem is or I don't understand what you are claiming to be able to do.
The point is that what you propose just changes the rights for the root folder of the filesystem. So if some other user (me on a different computer) creates files and folders in that filesystem, I won't generally be able to read/write/execute them (even if I own the root folder and all permissions are set). In my example I used root as the "other user" but the same would happen for any other user.
In other words the whole point here would be to be able to do "touch /media/fs/test" as one user and then as another. But that's not possible as explained above.

---

### Post by coffeecat on 2011-11-08
> **switzel said:**
> Either you don't understand what my problem is or I don't understand what you are claiming to be able to do.
The point is that what you propose just changes the rights for the root folder of the filesystem. So if some other user (me on a different computer) creates files and folders in that filesystem, I won't generally be able to read/write/execute them (even if I own the root folder and all permissions are set). In my example I used root as the "other user" but the same would happen for any other user.
In other words the whole point here would be to be able to do "touch /media/fs/test" as one user and then as another. But that's not possible as explained above.

OK - I see what you are saying, but trying to overwrite a root-owned file is a special case. I think that's why I got distracted.

I agree that if you create files and folders with an account with (say) UID:GID of 1000:1000 and your second machine has an account with 1001:1001 (say) you will run into problems if your saved files do not have an "other" permission of 7 (or 6 if you don't need execute). 

If I create a file in my home folder it typically has 664 permissions. I tried a GUI copy to an ext4 partition I had previously chowned and chmodded as above, and the 664 permissions remained, which means of course that I would have read-only access to that file from an account with different UID/GUI. You are right - I agree.

In short, I don't know a way around checking and modifying the permissions of all saved files if you need to use them from systems where your account has different UID/GIDs. Apologies for misreading your original question.

Nevertheless, being able to chmod and chown a filesystem does seem to be little-known, so do pass that small and useful nugget around. Good luck!

---

