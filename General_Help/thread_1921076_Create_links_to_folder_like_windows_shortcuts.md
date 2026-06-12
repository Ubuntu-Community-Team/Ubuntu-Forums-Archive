---
title: "Create links to folder like windows shortcuts?"
date: 2012-02-06
forum: General Help
---

### Post by ljl16 on 2012-02-06
Hi there, 
 I would like to create a shortcut to a folder in the sense that windows does it: Once you enter, you are there, instead of just inside the link. Let me get my point across by an example: 

```

main-folder:~$
main-folder:~$ cd shortcut
main-folder:~/shortcut$ pwd
main-folder:~/shortcut$ main-folder/shortcut

```

When the result I want is it's real location, for example: main-folder/music/stars/shortcut. Why? Because I usually want to do a "cd .." at some point, instead for looking for the route of the file all the way back again.

Any suggestions?

Thanks!

---

### Post by mlentink on 2012-02-06
You might want to look at this:
[http://manpages.ubuntu.com/manpages/lucid/man7/symlink.7.html](http://manpages.ubuntu.com/manpages/lucid/man7/symlink.7.html)

---

### Post by Mosome on 2012-02-06
You can create a link to a file/folder by using ln, with something like:

ln "file" "shortcut name" -s

This will take you directly to the location or access the file.  You can safely remove the link without losing the original when you want because of the "-s" option.

---

### Post by ljl16 on 2012-02-06
> **Mosome said:**
> You can create a link to a file/folder by using ln, with something like:

ln "file" "shortcut name" -s

This will take you directly to the location or access the file.  You can safely remove the link without losing the original when you want because of the "-s" option.

That command just has the same effect than right clicking and making the link for the file. If I enter I still am where the link is located, not the path where the link points to.

> **mlentink said:**
> You might want to look at this:
[http://manpages.ubuntu.com/manpages/lucid/man7/symlink.7.html](http://manpages.ubuntu.com/manpages/lucid/man7/symlink.7.html)

Thanks, but I couldn't really understand everything that was being said there.

**In any case, my solution (for now, although I'm pretty sure there must be another way:**
Consists on creating a launcher and putting "nautilus /home/path" in the command. That provides the result I wanted to get. Isn't there any simpler way and one that I can use with the command line? (this one only works using the GUI & its windows).

Cheers,

---

### Post by Mosome on 2012-02-06
What you are basically looking for then is a hard link, but hard links aren't typically allowed on directories:

man ln

Another method you can try as an alternate work around is maybe use an alias.  Adding to the .bash_aliases in the home folder you could try:

Folder='/path1/path2/'

Then from the command line you could access it by typing:

cd $Folder

note that you'll have to use the dollar symbol, but it'll be usable as you want.

---

### Post by ljl16 on 2012-02-06
> **Mosome said:**
> What you are basically looking for then is a hard link, but hard links aren't typically allowed on directories:

man ln

Another method you can try as an alternate work around is maybe use an alias.  Adding to the .bash_aliases in the home folder you could try:

Folder='/path1/path2/'

Then from the command line you could access it by typing:

cd $Folder

note that you'll have to use the dollar symbol, but it'll be usable as you want.

Thanks! Exactly what I was looking for. I don't mind using the $ at all, this will make my work much more pleasant.

Just for curiosity sake's: Why aren't links hard links to begin with? From what I understood in the link posted before on this thread, hard links would be exactly the same as the folder it points to (so if you delete the link you delete the folder, I guess). But going around it would be as simple as: make the link just be the equivalent to a "cd /path/". I don't get it, either I'm really dumb or as superior as ubuntu is to windows sometimes, others they implement the weirdest things (...that I'm sure will make total sense when I understand the reason why :]). I will start looking my shortcuts in windows with respect and fear now!

---

### Post by Vaphell on 2012-02-06
Soft links are more convenient and safer. They are non-destructive and you can easily fix stuff when you point to the wrong place. You can unbind simply by removing it. Hard link on the other hand is physically connected to the same node in filesystem. When you delete it, the original content is also gone (you delete physical filesystem object, not fake pointer). For the same reason hardlinks don't work between partitions.

besides **cd -P** does what you want
by default cd stays where the symlink is in directory tree, but -P makes cd command to teleport to the real deal.

```
$ mkdir slink1
$ ln -s slink1 slink2
$ ls -l
<stuff> slink1
<stuff> slink2 -> slink1
$ cd slink2
$ pwd
/home/me/**slink2**  (symlink)
$ cd -P ../slink2
$ pwd
/home/me/**slink1**  (real deal)
```

---

### Post by Mosome on 2012-02-06
Hard links would be risky to manage.  If you delete the hard link, you are deleting the actual folder itself.  To avoid confusion, it was probably best left avoided.  If you hard link an external drive and forget that it's not a simple folder and delete it during a cleanup you wiped your entire hard drive by doing so.  Basically a hard link is like a dual pointer to the same location on the hard drive.  This also makes it confusing on the system, because you basically would have 2 FAT entries but pointing to the same 1 data segmentation.

I believe some time ago hard links were allowed, but for safety it was best left avoided.  A hard link wouldn't be like a shortcut, such as with soft links.  A shortcut on Windows is just a file that specifies some information and actions to perform, much like a soft link.

---

### Post by ljl16 on 2012-02-07
> **Vaphell said:**
> Soft links are more convenient and safer. They are non-destructive and you can easily fix stuff when you point to the wrong place. You can unbind simply by removing it. Hard link on the other hand is physically connected to the same node in filesystem. When you delete it, the original content is also gone (you delete physical filesystem object, not fake pointer). For the same reason hardlinks don't work between partitions.

besides **cd -P** does what you want
by default cd stays where the symlink is in directory tree, but -P makes cd command to teleport to the real deal.

```
$ mkdir slink1
$ ln -s slink1 slink2
$ ls -l
<stuff> slink1
<stuff> slink2 -> slink1
$ cd slink2
$ pwd
/home/me/**slink2**  (symlink)
$ cd -P ../slink2
$ pwd
/home/me/**slink1**  (real deal)
```

WOW! An even better solution :). These forums will never stop surprising me, thank you very much.


> **Mosome said:**
> Hard links would be risky to manage.  If you delete the hard link, you are deleting the actual folder itself.  To avoid confusion, it was probably best left avoided.  If you hard link an external drive and forget that it's not a simple folder and delete it during a cleanup you wiped your entire hard drive by doing so.  Basically a hard link is like a dual pointer to the same location on the hard drive.  This also makes it confusing on the system, because you basically would have 2 FAT entries but pointing to the same 1 data segmentation.

I believe some time ago hard links were allowed, but for safety it was best left avoided.  A hard link wouldn't be like a shortcut, such as with soft links.  A shortcut on Windows is just a file that specifies some information and actions to perform, much like a soft link.

Thanks for the clarification, now I know the difference. So the windows shortcut are just soft links, too. I know it may seem like I'm joking, but... once I have understood what hard links are... why did they implement it if it was so dangerous? I mean, is there an application that benefited from it?

Cheers,

---

### Post by Vaphell on 2012-02-07
yes, windows .lnk are soft links too

They implemented it because it may prove useful if you know exactly what you are doing. Unixy systems give you unlimited power but also plenty of rope to hang yourself with :)
Also hindsight is 20/20. Basic system tools are over 30 years old and there were plenty paradigm shifts.

I read i little and it appears that hardlinks are not as dangerous as I claimed, and only deletion of last pointer kills the content, but i am not too eager to test :-) You simply never see anyone using hlinks and most people forgot the specifics (if they ever knew).
[http://en.wikipedia.org/wiki/Ln_%28Unix%29#Hard_link](http://en.wikipedia.org/wiki/Ln_%28Unix%29#Hard_link)

---

### Post by pqwoerituytrueiwoq on 2012-02-07
there is a even more powerful (100% transparent) feature that is similar to a symbolic that uses fstab ([FONT=Courier New]/etc/fstab[/FONT]) to do this
```
/home/me/target /home/me/origin bind defaults,bind 0 0
```
[FONT=Courier New]/home/me/target[/FONT] should contain files
[FONT=Courier New]/home/me/origin [/FONT]should be empty

to apply changes to fstab without a reboot [FONT=Courier New]sudo mount -a[/FONT]

---

### Post by redmk2 on 2012-02-07
> **Vaphell said:**
> yes, windows .lnk are soft links too

They implemented it because it may prove useful if you know exactly what you are doing. Unixy systems give you unlimited power but also plenty of rope to hang yourself with :)
Also hindsight is 20/20. Basic system tools are over 30 years old and there were plenty paradigm shifts.

I read i little and it appears that hardlinks are not as dangerous as I claimed, and only deletion of last pointer kills the content, but i am not too eager to test :-) You simply never see anyone using hlinks and most people forgot the specifics (if they ever knew).
[http://en.wikipedia.org/wiki/Ln_%28Unix%29#Hard_link](http://en.wikipedia.org/wiki/Ln_%28Unix%29#Hard_link)

When you delete a file all you are doing is unlinking the alias (somefile) from its inode.  When you "hard link" a file you are really just supplying a second link.  This is why the inode is not released until the last link is deleted.  If you want to see the inode to file mapping in one directory make a file then add a hard link to it and then use ls -i to see the inode with the files.

Since each partition has its own set of inodes you can't hard link across partitions.

If you use *rsnapshot* you are using hard links.  The original idea was used with  *rsync* in a script by Mike Rubel.  His web page is [here]("http://www.mikerubel.org/computers/rsync_snapshots/").  Later this idea became the basis of the rsync wrapper called [rsnapshot]("http://rsnapshot.org/").

---

### Post by ljl16 on 2012-02-08
Thanks to everybody for the awesome answers. I can't believe the amount of knowledge I'm learning from these forums :p

---

