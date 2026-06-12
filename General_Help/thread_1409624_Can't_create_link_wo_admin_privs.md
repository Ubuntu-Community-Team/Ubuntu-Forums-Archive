---
title: "Can't create link w/o admin privs"
date: 2010-02-17
forum: General Help
---

### Post by jamesisin on 2010-02-17
I am working out a problem in library access for Rhythmbox and am using (on other machines with other users) a link to .gvfs/share in the user's Music folder:

/home/[username]/.gvfs/name of share

The problem that I run into is that when I attempt to do that for a non-priv'ed user I get a link to / (what?).  Anything under .gvfs (or .gvfs itself) behaves this way.  I tried drag/drop a link and right-click &#8212;> Make Link with the same results.

Then I tried just running Nautilus as a priv'ed user (su [username], gksudo nautilus) but nautilus was not able to spawn (I had my doubts about that one).

So, I guess next I'll try creating the link manually.  Can someone confirm this syntax?

```
ln /home/[username]/.gvfs/share\ on\ server /home/[username]/Music/LinkName
```

---

### Post by jamesisin on 2010-02-17
I read the ln man page and am confused concerning hard and soft links.  I then read both articles at Wikipedia (interesting enough), but that didn't clear up the confusion.

Which is the kind of link I create when I drag/drop a file/folder (with ctrl-shift)?

---

### Post by linuxman94 on 2010-02-17
Did you try
```
sudo ln /home/[username]/.gvfs/share\ on\ server /home/[username]/Music/LinkName
```?

---

### Post by jamesisin on 2010-02-17
Yeah.  (I just didn't mention sudo.)

I ended up using the -s argument, but I still have no idea if a symbolic link is a 'normal' link or if I should in fact be using a hard link.

I'm still a little confused why the un-priv'ed user could not create a link from one item under their /home directory to another.

---

### Post by Bakerconspiracy on 2010-02-18
You can't create a hard link to a directory. A hard link is like having the same file in two different places. If you delete a hard link then you delete the file in memory too.

You can only soft link a directory.

I'm pretty sure you are doing everything right

---

### Post by jamesisin on 2010-02-18
It was the comments (at Wikipedia) about the recursive problem with hard links which made me choose the soft link.  It has the correct link symbol, so that's a good sign.  (I understand it is *possible* to create hard links to directories but ill advised.)

---

### Post by Bakerconspiracy on 2010-02-18
> **jamesisin said:**
> (I understand it is *possible* to create hard links to directories but ill advised.)

I was accidentily trying to do that earlier, and 'ln' was spitting back an error. You are probably right though, maybe with the correct flags.

But as far as I know (as you probably already know), creating a hardlink is a pointer to memory, whereas a sym link is reference to an absolute path. So this gets kind of weird when you start hard linking directories.

I might be reiterating the same thing you have said.

---

### Post by jamesisin on 2010-02-18
Yeah, I don't know how to do it.  I just remember reading along the way that it was possible but not recommended.

I still don't know what the difference between "a pointer to memory" and a "reference to an absolute path" might actually mean.  I understand the words, but what are they trying to get at?

---

### Post by jamesisin on 2010-02-18
And if anyone can answer me why an un-priv'ed user can not create a link from one item under their /home directory to another location in their /home directory, my life would be complete.

---

