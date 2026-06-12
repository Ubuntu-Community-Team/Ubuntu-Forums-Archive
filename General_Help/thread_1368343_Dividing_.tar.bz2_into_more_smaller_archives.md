---
title: "Dividing .tar.bz2 into more smaller archives"
date: 2009-12-30
forum: General Help
---

### Post by gabe17 on 2009-12-30
Hi! I have one big .tar.bz2 archive (more than 20GBs) and I need to divide it into more smaller parts (I need them to burn on DVDs, but later I need to be able to unite them together and make again one big archive). How can I do this? 

One more question...how can I make an archive with a password, or other way how to protect them not to be opened without password?

Thanks.

---

### Post by phillw on 2009-12-30
> **gabe17 said:**
> Hi! I have one big .tar.bz2 archive (more than 20GBs) and I need to divide it into more smaller archives (I need them to burn on DVDs). How can I do this? 

One more question...how can I make an archive with a password, or other way how to protect them not to be opened without password?

Thanks.

Hi & welcome to the forums,

I've not looked too much at this yet, it is on my list of things 'to do' for a How To I'm writing.

```
     -L, --tape-length NUMBER
           change tape after writing NUMBER x 1024 bytes


```
So, 1024 bytes = 1kB - So, you'd be looking for 4,300 for 4.3 GB - again, you may need to fine tune the number.

I've not tried this yet. You *should* be able to pipe the output to /tmp/backup then, when prompted to change tape, you could use your dvd-burner programme to burn that file to dvd, or copy the file over somewhere adding an index number to it. -- I'd be grateful if you'd PM me with how you get on - I've been too busy with other stuff to sit down and play with this.

As for passwords, tar does not natively support passwords. But, you can use ```
sudo gpg -c *filename*
```

To encrypt the backup segments, then use ```
sudo gpg *filename*.gpg
``` to un-encrypt them.

Mine complained that there was no agent, but still did the job :)

Hoping that points you in the general direction

Regards,

Phill.

---

### Post by Leppie on 2009-12-30
Phill, I've tried the links in your signature, but get errors with your blog (one is: "PhillW has no blog entries to display.").

---

### Post by phillw on 2009-12-30
> **Leppie said:**
> Phill, I've tried the links in your signature, but get errors with your blog (one is: "PhillW has no blog entries to display.").


Hi - Read the **top** line of my Sig ;-)

vBulletin's tech services managed to not only delete the forum, but also the backup of the forum. The rebuilding of it has been going on for some 4 weeks now. The owner has had some family stuff to attend to &, of course, a little thing called christmas. It's gradually getting there - but will be about another 2 weeks before all the old postings are back on.
Along with those in my Sig, are the ones for 9.04 --> 9.10 Upgrade and ext3 --> ext4 file system change.
And, all my blooming bookmarks for people to use as a one stop shop for common problems (the majority of them point right back here, but it was building into a good little resource for those new to Ubuntu).

The owner is now keeping a backup of the forum on my file server - well beyond the reach of the idiots at their Tech Svcs. We're not going through all this again !!!!

So, be patient :-)

/edit altered my Sig

Regards,

Phill.

---

### Post by gabe17 on 2009-12-30
Hi phillw, 

I've tried to make the divided archive using this command:
```

tar cvpjf archive.tar.bz2 folder/ -L 10

```

But I got this error:
```

tar: Cannot use multi-volume compressed archives
Try `tar --help' or `tar --usage' for more information.

```

What I'm doing wrong?

---

