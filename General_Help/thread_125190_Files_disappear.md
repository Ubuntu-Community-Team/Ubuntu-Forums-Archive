---
title: "Files disappear"
date: 2006-02-03
forum: General Help
---

### Post by Strife on 2006-02-03
So this morning, I noticed that my desktop wallpaper disappeared and reverted to the standard brown background. Upon some investigation, the file seems to have been myseteriously deleted.

I had just bought a new hard drive, and have several partitions on it. This particular partition was supposed to be for photos (which, thankfully, didn't have a whole lot on it  yet). Even more mysterious, as far as I can tell, there isn't any sign of damage anywhere.

What could have caused this? I've never had such problems with ext3... Is this a sign of more bad things to come?

---

### Post by earobinson on 2006-02-03
sleep typing?

I would keep backups to be on the safe side, but then I keep backups even when no problems are presenting!

---

### Post by Strife on 2006-02-03
Of course backups are nice. I do that with vital files, but unfortunately, being a poor college student, I can't really afford a full backup solution for everything.

And quite honestly, having to backup files because my filesystem may choose to delete files is an unacceptable requirement.

And in response to the "sleep typing" (I know it's a joke, but I want to clarify the original post): Initially this morning, the files (or at least the wallpaper) <i>were</i> there. It wasn't until later that it disappeared.

---

### Post by earobinson on 2006-02-03
are you sure they are gone, try doing an ls of the dir with the terminal? I know that some guis have bugs. Try to give us as much info as you have about what you where doing betweent the two times. It is very hard to make a guess based off "files where here at time x and gone at time y".

In regards to backups I understand that, just and Idea a dvd burner goes for 50$ (cnd) and 50 dvds 15$ (cnd) IMHO that is great for backing up all my pictures, docs and all other info I dont want to lose, just and idea.

This post seems a bit harsh to me, but I dont know how to say what I want to say any other way, It is in no way harsh and should be taken in the spirt that it is ment, a person trying to help.

---

### Post by Strife on 2006-02-03
Oh, they're good and gone. The only remnant is the lost+found directory. This doesn't have any files in it, either.

---

### Post by earobinson on 2006-02-03
Did you do anything funny, see edit above

---

### Post by Strife on 2006-02-03
First off, I didn't take it as harsh. If it seemed I did, I apologize. I really do appreciate your effort.

Anyway, here's the directory listing:

```

mike@crux:~$ sudo ls -alR /mnt/photos/
/mnt/photos/:
total 24
drwxr-xr-x  3 root root  4096 2006-01-25 00:55 .
drwxr-xr-x  7 root root  4096 2006-01-25 00:58 ..
drwx------  2 root root 16384 2006-01-25 00:55 lost+found

/mnt/photos/lost+found:
total 20
drwx------  2 root root 16384 2006-01-25 00:55 .
drwxr-xr-x  3 root root  4096 2006-01-25 00:55 ..

```

Also, I checked my .bash_history (I tend to use the terminal a lot more than the gui tools), and verified that I didn't do anything to the directory. The last thing I did to it was make a symbolic link to one of the photos in it.

---

### Post by vruum on 2006-02-03
are the files still in the locate database, "try sudo locate $name_of_file", you could also try grepping through your logs, open a terminal, go to /var/log and do:
sudo cat * | grep $name_of_file
or
sudo cat * | grep /mnt/photos
it might take a while and eat your cpu, but maybe something will show up

---

### Post by Strife on 2006-02-03
I had tried the locate idea earlier (that was what I did first, actually), but whatever happened weirdly seemed to have happened before the rebuilding of the database.  I say weirdly since my wallpaper was still there (I suppose GNOME has some sort of caching system... it's just odd that it took that long to all of a sudden realize there was a problem).

I also followed your other suggestions, but the only things it showed me were mounting and unmounting commands (as well as a few other similar commands such as e2fsck) that I ran this morning while trying to figure out what was going on.

---

### Post by Mustard on 2006-02-03
Did you view the pictures in any application and do any transforms on them prior to them disappearing?

I have a faint recollection of reading of a bug in an image viewing application that would destroy images when using the rotate option.

---

### Post by steve.horsley on 2006-02-03
Just a thought. The mount command has the effect of replacing an existing directory with the contents of another partition. Now, by mounting and unmounting the partition, you can make the contnents of that directory switch between two different sets of files.

So try looking in /mnt/photos both with and without the partition being mounted.

The bad news is that I don't think lost+found is created until fsck finds a filesystem error. So the existence of this file might mean that some filesystem corruption has lost them all.

---

### Post by Strife on 2006-02-03
steve, you may have solved the problem.

It probably was my mistake entirely. Now that you mention it, I'm not sure that the device was ever actually mounted when I put the files there. Which means that perhaps now they are gone for good.

Now that I think about it more, the "photos" drive was never visible on the Desktop until yesterday when I double clicked on it in Nautilus... I actually just switched back to using GNOME from using Fluxbox for a while, so very likely I just never had it mounted.

I feel quite dumb now, but I'm glad that what was lost was relatively insignificant and exists elsewhere.

Thanks all for the help.

---

### Post by xghstst0riesx on 2007-10-08
I have also had a few files disappear. I was browsing through photos on my SD card using (I think) gThumb and maybe F-Spot too. At some point there was an error in loading one of the photos and then they started disappearing. 
I noticed when looking at the system monitor it says I have 22 MB free and 98 MB used on the disk even though there are only a few directories on it and nothing else. This leads me to believe that they are still there somehow. The filesystem type is vfat. Does anyone have any ideas on how I might be able to recover these? Thanks.

---

