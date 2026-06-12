---
title: "rsync thinks all of my symlinks are &quot;unsafe&quot;"
date: 2011-01-19
forum: General Help
---

### Post by soulspit on 2011-01-19
Hey everyone,

I'm trying to use rsync to make a simple backup of my home directory, and I'm having trouble with symlinks.  Broadly speaking, I would say there are two types of symlinks in my home directory:

1: Symlinks that point to a separate partition, since I dual-boot Windows and have Linux on a small partition. For example, my music, pictures, etc. folders are simply symlinks to my those folders on my Windows drive.  These point outside of my home directory, so I when backing up my home directory I would call these "unsafe" according to the definition in the man page for rsync.
2: Symlinks that point to directories and files on the Linux partition, that are mainly there to aid in organization.  Since these point to places inside my home directory, I'd think they were "safe"

Since I'd like a backup of my home directory to backup all of my stuff without making me dig into my Windows drive and specify specific folders to copy, I would like rsync to copy the referent of all symlinks of type 1, and recreate symlinks of type 2 as symlinks.  I have experimented with all of the various symlink behaviors in the man page, but all I can get is either for all symlinks to be recreated, or for all symlinks to have the data they refer to copied.

I tried this on a simple example.  Here is the source folder I am trying to backup:```
~/ ls -lhF /home/toby/src
total 8.0K
drwxr-xr-x 2 toby toby 4.0K 2011-01-19 17:50 dir/
lrwxrwxrwx 1 toby toby   18 2011-01-19 17:54 link a -> /home/toby/src/dir/
lrwxrwxrwx 1 toby toby   81 2011-01-19 17:55 link b -> /media/Cabbage/Users/Toby/Pictures/test/
```As you can see, it has one directory, a (rather redundant) link to that same directory, and then a link to somewhere completely unrelated.  Using rsync with --links (implied by --archive) I would expect all links to be recreated.  Using, in addition, --copy-unsafe-links, I would expect links pointing outside of the folder-to-be-backed up (eg the link "link b") to be copied.

You'd think my problem would be solved, but it's not:```
~/ rsync -av --copy-unsafe-links /home/toby/src/ /home/toby/dest/                                                      
sending incremental file list
./
dir/
dir/picture.jpg
link a/
link a/picture.jpg
link b/
link b/goblin marauders with clubs.jpg
```It correctly copies from the source the files that link b pointed to, since that was outside of the copied tree.  However, it *also *copied "link a" and its contents, thinking that link a is an unsafe link.  rsync specifically tells me that it thinks it's unsafe if I specify it to ignore unsafe links:```
~/ rsync -av --safe-links /home/toby/src/ /home/toby/dest/                                                      
sending incremental file list
./
ignoring unsafe symlink "/home/toby/dest/link a" -> "/home/toby/src/dir"
ignoring unsafe symlink "/home/toby/dest/link b" -> "/media/Cabbage/Users/Toby/Pictures/test"
dir/
dir/picture.jpg
```What?!  How is -> "/home/toby/src/dir" unsafe?

Of course, if I don't specify any special treatment for symlinks other than the default copying of symlinks implied by -a, I get:```
~/ rsync -av /home/toby/src/ /home/toby/dest/                                                                 
sending incremental file list
./
link a -> /home/toby/src/dir
link b -> /media/Cabbage/Users/Toby/Pictures/test/
dir/picture.jpg]
```I've experimented thoroughly with many combinations of not using --links (ie, -a --no-l), using --keep-dirlinks, using --copy-dirlinks, and various other options.  I may not have exhaustively tried every single combination of every relevant option, but I think that nothing is going to work if rsync considers "link a" to be "unsafe".  It looks safe to me!

I hope that made sense.  I just don't want to have duplicate data that would cause restoring my data to be a huge pain.  But I do want data from other drives to be copied.  Please ask if anything didn't make sense or if I can give any more info.  I appreciate any help or advice you can give!

Maybe there is some solution obtainable by running rsync twice, once to recreate all symlinks and then again with different options to replace only those symlinks that are unsafe?  Once symlinks exist on the destination will rsync be better able to determine what is safe and what is not?  I don't really get how this works.  Thanks for your help.

---

### Post by soulspit on 2011-01-19
Bump please!

Maybe I can work around this issue by making those few folders that link to my WIndows drive (music, pictures, videos, etc.) into hard links instead of symlinks?  Then, presumably, rsync will copy them into the backup as expected, and I can leave all other symlinks to simply be recreated as symlinks.  How about it?

Although, will I have any problems having hard links on an ext4 partition point to stuff on an ntfs partition?  I guess that's another topic.

Edit: Scratch that, you can't make hard links that link to other volumes, and it seems like making hard links to directories is deemed to be a Bad Idea.  There's got to be a way to get rsync to recognize what is actually a safe link and what is unsafe, come on fellas, help me out...

---

### Post by soulspit on 2011-01-28
Another bump, if I may.  Come on guys, right now, in order to back my stuff up, I have to run this clunky mofo in order to exclude the safe symlinks rsync should by all means know are safe:```
rsync -auhh --delete --copy-unsafe-links --exclude=.google/picasa/3.0/dosdevices/ --exclude=.google/picasa/3.0/drive_c/ --exclude=.wine/dosdevices/ --exclude=.wine/drive_c/ /home/toby/ /media/amber/homebackup/
```I mean, it works of course, but this would be a lot worse if I actually had lots of symlinks organising my stuff, which I used to, but this is a new machine.  There must be a more elegant way!

Or, maybe someone can confirm this is probably a bug and I'll go report it without feeling like I'm making a newb mistake?

---

### Post by Irony on 2011-01-28
Just use copy like this;

```
sudo cp -ax /home/yourname/. /newhome/yourname/.
```

---

### Post by soulspit on 2011-01-28
I was about to respond "but I want to use rsync so I can do regular backups and not have to copy 400gb to an external hard drive over and over again" until I realised that cp has an --update flag that mostly accomplishes everything I wanted to use rsync for.  I guess using rsync for this is like using a swiss army knife to spread butter.

I'll give this a go when I'm my home computer and make sure it does what I want it to do with symlinks, but it looks good to me, so thanks!

---

