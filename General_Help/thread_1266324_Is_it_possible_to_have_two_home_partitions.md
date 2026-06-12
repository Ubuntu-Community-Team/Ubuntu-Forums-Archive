---
title: "Is it possible to have two /home partitions?"
date: 2009-09-14
forum: General Help
---

### Post by paul-p1988 on 2009-09-14
Hello All,

I am just wondering if it is possible to have two /home partitions, or a work around for doing a similar thing. I could do this on windows (having a 'my documents' for each user assigned to a different partition seemed to do the trick) and i was hoping i could do the same with Ubuntu as i have a whole load of music/films, and my brother has a tendency to download everything possible to it, and i would like for us to have a partition each.

I have 2 HDD's, one 40gb (for the Ubuntu System files), and 1 160gb (partitioned 80gb to each partition, one as /home, the other just as ext3).

Is there a way i can assign each partition to each user?

Thanks

---

### Post by Bachstelze on 2009-09-14
Yes, all you have to do is mount your partition somewhere, for example /mnt/home, and set your home direcory to /mnt/home/username, while your brother's home directory will be /home/username.

---

### Post by jocko on 2009-09-14
> **Bachstelze said:**
> Yes, all you have to do is mount your partition somewhere, for example /mnt/home, and set your home direcory to /mnt/home/username, while your brother's home directory will be /home/username.
Why mount the home directory in /mnt?

@paul-p1988:
Set up your /etc/fstab to mount one of the partitions as /home/[COLOR=Red]username1[/COLOR] and the other as /home/[COLOR=Red]username2[/COLOR], then create the empty folders /home/[COLOR=Red]username1[/COLOR] and /home/[COLOR=Red]username2[/COLOR] to use as mount points (username1 and -2 is of course yours and your brothers usernames).

---

### Post by CatKiller on 2009-09-14
You don't even need to do that. Just mount one as /home/*username1* and the other as /home/*username2*.

Since you've already had one of them mounted as just /home, you'll probably have a bit of tidying up to do first. I'd recommend doing so from a live cd so that you aren't simultaneously copying and using the Home folder for anything.

EDIT: beaten to it! What are the chances?

---

### Post by jocko on 2009-09-14
> **CatKiller said:**
> EDIT: beaten to it! What are the chances?
Great minds think alike...

---

