---
title: "Moving one users home folder to other disk..."
date: 2011-05-29
forum: General Help
---

### Post by ragtag on 2011-05-29
Hi,

 How would you go about moving one users home folder to a different partition, while maintaining other users home folder on the current one. Will simply running "usermod -dm /path/to/new/home username" on one of the users do the trick.

 I want to run one of the users of an SSD, while the other runs of a bigger SATA disk.

---

### Post by dandnsmith on 2011-05-29
[this page](http://www.computerhope.com/unix/usermod.htm) seems to think so.

---

### Post by ajgreeny on 2011-05-29
I don't think you can do that, as the /home folder or partition can only be in one place, you can't split it in the way you would need to to do what you've asked about.

Or at least you can't with a partitoned setup; I'm not sure about LVM, perhaps that can do it?  I don't think dandnsmith's link will help you as it is not dealing with different partitions/disks, just the folders within /home.

---

### Post by linkageless on 2011-05-29
There is nothing stopping you from setting any particular user's home dir to any path you desire.

If the user has many GB of data, it would probably be advisable to rsync -axH (do a man rsync for more options) then delete the old tree once the transition (using usermod -d) is complete.

---

### Post by ajgreeny on 2011-05-29
> **linkageless said:**
> There is nothing stopping you from setting any particular user's home dir to any path you desire.

   Are you sure?  They can be in different folders, I agree, but not on different disks or partitions, surely.  All the users' /home/username folders have to be in the same /home folder or partition.  I don't know any way out of that.  The mount requirements of fstab will not allow anything else, as far as I can see.

---

### Post by wildmanne39 on 2011-05-29
> **ragtag said:**
> Hi,

 How would you go about moving one users home folder to a different partition, while maintaining other users home folder on the current one. Will simply running "usermod -dm /path/to/new/home username" on one of the users do the trick.

 I want to run one of the users of an SSD, while the other runs of a bigger SATA disk.
Hi, I have a link that tells you how to have home folder on a different partition, but You need to read it carefully I also do not know that they can be split up.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by dandnsmith on 2011-05-30
That page only tells how to set the /home on a different partition.

To move just one user home to a different partition/disk it is necessary to:
- set up the users data in the new location
- create a link from the original location to the new
- arrange for the new location to be mounted before the user tries to log in

It seems to me that it should also be possible to arrange it by jiggering the entry in the password file - but I'd want to check that before asserting that it really would work.

There's nothing particularly magic about the location of the home for a user.

---

### Post by Irihapeti on 2011-05-30
I think it should be possible to use a symlink to do what you want.

I run a webserver on my home PC. The root partition is quite small, so I have setup /var/www to point to a directory on another drive.

The second drive is actually mounted on /srv. Therefore, /var/www points to /srv/www. The rest of /var is on the root partition.

I see no reason why you couldn't do something similar with an individual's home directory. The important thing is to have the permissions set correctly so the user can write to it. I don't think you'd need to run usermod, either. As far as the system is concerned, it's still in the same place.

---

### Post by linkageless on 2011-05-31
Just to be clear, there is normally no requirement to have any particular user's home dir within /home/

However, to make things work smoothly, I absolutely agree that the path should be available after boot (so if it's not in / that filesystem should be included in /etc/fstab to auto mount). Also, permissions & ownership should be set identical (or at least similar) to how it would be in /home/, this includes the directories above.

As Irihapeti righly suggests, symbolic link from within /home/ is actually a very convenient way of achieving this without having to go through /etc/passwd changes, but is possibly a kludge to the eye of the purist. You still of course need to be sure that the filesystem that dir is in is mounted and available permissions-wise when needed.

/home/ is just the conventional place to keep home directories in linux. Its not so unusual to have users home dirs in other places like /export/home/ or even a non-existent location in special cases. Another special case is /root/.

Anyway, the short answer is as already suggested:
sudo usermod -m -d /path/to/newfredhome fred

or

sudo mv /home/fred /path/to/newfredhome && sudo ln -s /path/to/newfredhome /home/fred

Be sure the user is logged out, all of '/path/to/' has similar permissions to /home/ (I'd use 'sudo chmod 755' on those) and be prepared to wait a while for the move if the existing contents are large. See man usermod for more details.

Advanced users may want to use tools like 'vipw', 'rsync -aHx' or 'cp -rp'. As is often the case with linux, we have many choices to achieve our goals and personal preference often comes into it.

---

### Post by ragtag on 2011-06-01
Thanks for the replies. Moving the user with usermod worked perfectly. :)

---

