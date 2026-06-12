---
title: "Want to make a backup image, but I dual boot"
date: 2010-10-01
forum: General Help
---

### Post by Bramkaandorp on 2010-10-01
I have decided to remove Windows from my disk, but I want to keep my current install of Ubuntu.

One possibility that sprang to mind was to make an image out of my Ubuntu install.

Since I dual boot, the disk is numbered "SDA2" (extended) "SDA5" (root) and then there is Swap. (Windows is the first part of the disk)

One question sprang to mind:

If I make an image out of it, what happens to the numbers? Will there be any conflicts? Not to mention the question of which program would be best (and easiest to use, preferably with a GUI, since I want to save time, not learn code).

And if I would go for a binary dump to an external disk (to put it back when the destination disk is empty), would the same problems arise? Or would that bring even more problems, like the issue of the swap partition, which I would have to receate, since it wouldn't fit on the "dump disk"?

This is all because the whole thing sounds very similar to placing the ubuntu partition to the front of the disk, which, as I have been told, is not a good idea.

I hope I make sense.

---

### Post by Rubi1200 on 2010-10-02
Take a look at Clonezilla and see if it will do what you want:
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Bramkaandorp on 2010-10-02
An impressive track record. I will seriously check that out.

If I don't respond within a week, expect the worst.

Thanks for the tip.

---

### Post by Quackers on 2010-10-02
You need to be careful with it, but Clonezilla has worked perfectly well for me. I dual boot on 2 hard discs and clone each disc seperately. I have successfully restored the second drive with it once already.

---

### Post by Bramkaandorp on 2010-10-02
A real concern for me is that the system will not work properly because it was configured as a "second" part of the disk. Will it work as it should if it becomes the "first" part of the disk?

---

### Post by Quackers on 2010-10-02
I wouldn't think that would be a problem. It may be, however, that grub will object when the Windows partition goes missing. (It may be looking for a partition that no longer exists). If that happens you may need to re-install grub to the MBR of sda (maybe by booting from the Ubuntu live cd).

---

### Post by Bramkaandorp on 2010-10-02
That does sound like a problem. Why would I want a Grub menu if I only have one OS, right?

Apart from that, how big will the image usually be? I would have removed all my music, videos and all other personal files from the home directory (apart from the hidden files of course).

And apart from that (again), will the image be a complete copy (with my fireflox settings, liferea settings and feeds etc.), or just an edited "lucid" iso with my programs on it? That's the part i don't really know.

---

### Post by Bramkaandorp on 2010-10-02
additionally: Do I choose the extended partition, or just the root partition?

---

### Post by randoer on 2010-10-02
If you use Clonezilla, it will be a bit by bit exact copy of everything on the disk....including the trash and unused space.

---

### Post by Quackers on 2010-10-02
Bramkaandorp, you don't particularly want the grub menu, but you do need grub to boot Ubuntu.
randoer is correct, if you make the choice to clone the disc. It will be a true copy of everything on your disc, bit, by bit, partition by partition. All programs, setting etc would be included.

---

### Post by Bramkaandorp on 2010-10-03
@Quackers: I understand. I actually meant the menu you get when you have a dual boot machine. That will not show up afterwards, right?

@Randoer: Do I have to choose the extended file system, or just the part with ubuntu on it, minus the swap? That is the only thing I am not certain about. All else is pretty much clear to me.

---

### Post by Quackers on 2010-10-03
> **Bramkaandorp said:**
> @Quackers: I understand. I actually meant the menu you get when you have a dual boot machine. That will not show up afterwards, right?

@Randoer: Do I have to choose the extended file system, or just the part with ubuntu on it, minus the swap? That is the only thing I am not certain about. All else is pretty much clear to me.

That may happen and it may not. If it does you will need to re-install grub.
With regard to your second question, if you choose the clone disc option all partitions on the chosen disc will be backed up one by one but the output will be one image. You don't need to choose which partitions to back up.
It is also possible to back up a single partition as well.

---

### Post by Bramkaandorp on 2010-10-03
> **Quackers said:**
> That may happen and it may not. If it does you will need to re-install grub.
With regard to your second question, if you choose the clone disc option all partitions on the chosen disc will be backed up one by one but the output will be one image. You don't need to choose which partitions to back up.
It is also possible to back up a single partition as well.

Which begs the question (I wonder Why I never thought of it): Will the empty space at the end (or at least the empty space on the partition) of the partition also be included, or is there some other way in which this is resolved?

---

### Post by Quackers on 2010-10-03
> **Bramkaandorp said:**
> Which begs the question (I wonder Why I never thought of it): Will the empty space at the end (or at least the empty space on the partition) of the partition also be included, or is there some other way in which this happens?

All I can say to you is that the backup image that is produced is approximately the size of the data on the disc (not the size of the disc). I do not have masses of data on the disc involved but I can say that the clone disc option only took about 15 minutes to run.

---

### Post by Bramkaandorp on 2010-10-03
> **Quackers said:**
> All I can say to you is that the backup image that is produced is approximately the size of the data on the disc (not the size of the disc). I do not have masses of data on the disc involved but I can say that the clone disc option only took about 15 minutes to run.

Well, that seems to answer all my questions (to date),

And now, I will seriously start the process of making the backup

Thanks for all advise, and I hope to be back with good news.

---

### Post by Quackers on 2010-10-03
You're welcome :-)
I hope so too!

---

### Post by Bramkaandorp on 2010-10-04
Bad news (though not of a disk screwed up magnitude).

In the set-up, the first disk you have to choose is the disk you want to save the image to. No problem.

The second disk is the disk you want to backup. I could only use the entire disk, not just the Ubuntu partition. The option to choose a partition only offered me the entire disk.

I am at a loss here.

Also, in contrast to the tutorial, I didn't get any option to choose an image to use, even though I had the lucid image on the "save to" disk. How do I "fix" that?

Too bad I don't know anyone personally who is familiar with clonezilla.

---

### Post by Quackers on 2010-10-04
I have only used the clone disc option but I would suspect that you need to select the second option when you get to the screen pictured.

---

### Post by Bramkaandorp on 2010-10-04
Why would I want that? Isn't the purpose of this whole exercise to get an image, which I can use to restore my ubuntu installation afer I have removed Windows? All so that I can put the image on a disk which is smaller than the Ubuntu partition.

I have no disk available which is larger than the Ubuntu partition, so a disk-to disk filedump is hardly an option.

---

### Post by Quackers on 2010-10-04
oops!
If you choose the option above the one that is highlighted in this screenshot you should be able to back up a partition.
I'm not sure I understand your last line. The disc or partition you restore an image to must be the same size or larger than the image you are restoring.

---

### Post by Bramkaandorp on 2010-10-04
> **Quackers said:**
> oops!
If you choose the option above the one that is highlighted in this screenshot you should be able to back up a partition.
I'm not sure I understand your last line. The disc or partition you restore an image to must be the same size or larger than the image you are restoring.

What I mean is: The image itself is smaller than the partition I used to make the image, right?

Since a binary dump also transfers the empty space, the temporary disk for storing the dump would have to be the same size or bigger. I don't have that ready, so a dump is out of the question.

I do know that the disk I want to install the image to should be at least as big as the original disk, but since the image itself is smaller, the disk I store the image (temporarily) doesn't have to be that large.

---

### Post by Quackers on 2010-10-04
Yes, the actual backup image is smaller than the disk/partition it came from.

---

### Post by Bramkaandorp on 2010-10-04
> **Quackers said:**
> Yes, the actual backup image is smaller than the disk/partition it came from.

Which is why I want to use that option. The problem is that I can not "only" backup the ubuntu partition, I can only backup the entire disk, including Windows.

If there is any workaround, I would love to hear it.

If not, I will just start anew with a fresh install, installing everything I have at the moment.

Either way, I won't discard Clonezilla, because I do see the importance of the program.

---

### Post by Quackers on 2010-10-04
If you use the "saveparts" option in the screenshot in post 20 you should be able to backup the Ubuntu partition.

---

### Post by Bramkaandorp on 2010-10-04
Then why did I need the Ubuntu iso file I downloaded on beforehand?

As far as I can tell, it is either not necessary, or I just don't get any notification for some reason.

Before it becomes needlessly complicated (with things like "unable to install, no install program available, because it was not in the backed up partition in the first place), I think I will just start with a clean install, unless the problem can satisfactorily be solved.

---

### Post by Quackers on 2010-10-04
What Ubuntu iso file?
If you are thinking of starting from scratch why not try Clonezilla anyway?

---

### Post by Bramkaandorp on 2010-10-04
> **Quackers said:**
> What Ubuntu iso file?
If you are thinking of starting from scratch why not try Clonezilla anyway?

If you look through the walkthrough on the clonezilla homepage, you will see a moment where you can choose which image to use as "something".

[http://clonezilla.org/clonezilla-live/doc/fine-print.php?fullmode=0&path=./04_Create_Recovery_Clonezilla/09-select-options-then-create.doc#09-select-options-then-create.doc]("http://clonezilla.org/clonezilla-live/doc/fine-print.php?fullmode=0&path=./04_Create_Recovery_Clonezilla/09-select-options-then-create.doc#09-select-options-then-create.doc")

You know what, Even though I understand the underlying mechanics batter than before, I have reached the point where I just don't care anymore.

Not because of this forum, you have been very patient. It just bugs me how a website can be so bad at just explaining stuff (clonezilla).

---

### Post by cottfcfan on 2010-10-04
I'm struggling to understand this thread.
Clonezilla is a handy and effective tool, it gives you the option to clone the entire disk or a partition.
Just find out what your Ubuntu partition is "sdaX" and clone it.
Wipe your disk and restore the cloned partition.
If you have any extra space on the disk, just extend your partition with gparted.
Job done.

---

### Post by Bramkaandorp on 2010-10-04
> **cottfcfan said:**
> I'm struggling to understand this thread.
Clonezilla is a handy and effective tool, it gives you the option to clone the entire disk or a partition.
Just find out what your Ubuntu partition is "sdaX" and clone it.
Wipe your disk and restore the cloned partition.
If you have any extra space on the disk, just extend your partition with gparted.
Job done.

And I will not have the problems I would have if I would do the following: remove Windows, move Ubuntu to the beginning.

Because the last time I did that, I got error messages that boiled down to "just do a clean install".

---

### Post by Quackers on 2010-10-04
I agree that the help info on the Clonezilla is a bit limited, but you have to bear in mind that it is a free program. To be honest, I for one, am glad somebody took the time to write the program and make it available at no cost.
I wish you the best of luck in whatever you decide to do with your system.

---

### Post by Bramkaandorp on 2010-10-04
I have just done what I wanted to, which is reducing the size of my Windows partition even further.

After having decided that giving up the ability to play "Frontlines: Fuel Of War" was just not worth it.

I could buy Crossover Linux(or Games), but why would I if I had already paid for a Windows license when buying the pc in the first place?

Don't get me wrong, I will remove Windows someday, just not yet. First I want to be absolutely sure I can play all my games via Crossover, and I think it would have to be at least a year in the future (something about making the Windows money worthwhile), but I will rid my life of Windows someday.

For now, I am content that I've been able to free up 50 GB of space (It's all about space).

Cheers

---

