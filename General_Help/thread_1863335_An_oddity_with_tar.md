---
title: "An oddity with tar"
date: 2011-10-17
forum: General Help
---

### Post by sideburns on 2011-10-17
I have to make an emergency backup of my sister's home folder on her Ubuntu 10.10 box before upgrading.  The folder is about 9.4 Gig.  I tried tarring it to a directory I'd made, /backup, and it came out at about 24 Gig.  Weird!  I deleted it again, and did this to get a compressed archive:

sudo tar -cjvf marcia.tar.bz2 /home/marcia

Now, it's "only" 14.1 gig.  Some compression!  Does anybody know why a compressed archive is almost 50% bigger than the original?

---

### Post by TeoBigusGeekus on 2011-10-17
Now that's odd!
Are you sure the folder is only 9.4gb?

---

### Post by syntr on 2011-10-17
> **sideburns said:**
> I have to make an emergency backup of my sister's home folder on her Ubuntu 10.10 box before upgrading.  The folder is about 9.4 Gig.  I tried tarring it to a directory I'd made, /backup, and it came out at about 24 Gig.  Weird!  I deleted it again, and did this to get a compressed archive:

sudo tar -cjvf marcia.tar.bz2 /home/marcia

Now, it's "only" 14.1 gig.  Some compression!  Does anybody know why a compressed archive is almost 50% bigger than the original?

Why are you using sudo?
How are you determining the size of the folder? Try:

```
du -chs /home/marcia
```

---

### Post by sideburns on 2011-10-17
Right-click, Properties, wait for the numbers to stop changing.

---

### Post by syntr on 2011-10-17
> **sideburns said:**
> Right-click, Properties, wait for the numbers to stop changing.
Did you try the command in my post? What was the output?

---

### Post by sideburns on 2011-10-17
I'm having to do this by ssh, because her box won't accept any DNS numbers.  your command returns 20 G, compared to the 9.4 I got the other way.  OK, that's why the tarball's so big.  Now, the question is why the discrepancy, but that's the subject for a different thread.

---

### Post by syntr on 2011-10-17
> **sideburns said:**
> I'm having to do this by ssh, because her box won't accept any DNS numbers.  your command returns 20 G, compared to the 9.4 I got the other way.  OK, that's why the tarball's so big.  Now, the question is why the discrepancy, but that's the subject for a different thread.

No need for another post, I'm pretty sure the GUI omits hidden files and directories when finding the size of a directory. :)

---

