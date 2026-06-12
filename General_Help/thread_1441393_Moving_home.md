---
title: "Moving home"
date: 2010-03-28
forum: General Help
---

### Post by pgk on 2010-03-28
Hi all,

My (40b SSD) netbook is configured with Ubuntu 9.10 installed on the 8Gb partition and the 32Gb currently unused (and unmounted). I'd like to change this as I've almost filled the 8Gb.

I'm thinking of moving my home directory onto the 32Gb partition. I've done this before, but there's one question I have. Here are my steps:

1. Mount the 32Gb partition.
2. Copy the contents of my home dir to the 32Gb partition.
3. Unmount the 32Gb partition.
4. Alter /etc/fstab to mount the 32Gb partition, and use the copy of my home dir on it.
5. Restart.

The thing I like about stage 2, is that as I'm only copying the files, if anything goes wrong, I can just revert things to the way they were. But, assuming things go well, how can I free the space that was used by the old home dir? There's no handle to it right?

Cheers,
Graham

---

### Post by m4tic on 2010-03-28
you could always resize the partitions, burn gparted to a cd or use your ubuntu live cd

---

### Post by srs5694 on 2010-03-28
Your procedure is basically sound; however, you're missing two steps, which collectively answer your question:

3.5 - Rename /home to something else, such as /home-orig

6 - After you've verified everything is working, delete /home-orig

This assumes you copy all of /home to the new partition, not just your own personal home directory (/home/pgk or whatever it's called on your system).

One possible complication is with permissions in step #2. When I do this sort of thing, I use tar because it can preserve permissions. For instance, if I've mounted the to-be-/home partition at /mnt/foo, I'd type:

```

cd /home
sudo tar cpf - ./ | (cd /mnt/foo; sudo tar xvpf -)

```

There are other commands that will work, too, but I'm familiar with using tar for this, so that's what I personally use. I *think* that "sudo cp -a /home/* /mnt/foo/" would work, too, for a /home directory, but I'm not positive of that.

---

