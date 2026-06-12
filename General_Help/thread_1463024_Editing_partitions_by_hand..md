---
title: "Editing partitions by hand."
date: 2010-04-26
forum: General Help
---

### Post by Scunnered on 2010-04-26
I am looking to set up a separate /home partition and am getting somewhat confused.  On an old system I practised resizing the partitions and feel reasonably confident in the mechanics.

Currently my drive is /dev/sda1 an ext4 file system with a mount point of / ;
/dev/sda2 and extended partition and /dev/sda5 a linux swap.

I propose to reduce the sda1 to about 10GiB for Karmic and allocate the bulk of the remainder to /home.  It is this point that I start to have difficulty.  I have seen screen shots which show a mount point of /home and for the life of me I have been unable so far to see how this is created. This has been further confused when looking at the subject in my latest copy of Linux Format (132) where it shows an example where dev/sda1 if NTFS, sda2 as ext3 and a mount point of /home, sda3 as ext4 and mount point of / finally sda4 being a Linux swap.

I wish at the end of the day to have Karmic as my OS with a separate /home partition with the view that once Lucid has settled down that I adopt it.  

What I would like to know is how having reduced sda1 do I proceed. As sda1 is an ext4 file system should the /home be also ext4 or like the example in the magazine of ext3?  How is the mount point for /home named?  Finally should I attempt to have /dev/sda number sequentially or let things stick as at present  I imagine that if I delete the current extended and swap before reducing the /dev/sda1 then that should get things to run in sequence.

I intend to use a live DVD to let me work with the partitions as this should be safer than messing about with my current partitions when mounted.

Just when I think that I am getting the hang of things someone yet again throws a curved ball.  

Your patience and kind assistance in the matter will be most appreciated.

---

### Post by srs5694 on 2010-04-26
> **Scunnered said:**
> I am looking to set up a separate /home partition and am getting somewhat confused.
...
What I would like to know is how having reduced sda1 do I proceed. As sda1 is an ext4 file system should the /home be also ext4 or like the example in the magazine of ext3?

You can mix-and-match filesystems however you like. My personal preference is to use ReiserFS for root (/) and most other system partitions, and either ReiserFS or XFS for /home or other user data partitions, depending on the typical file size -- XFS works better with files of hundreds of megabytes or more.

Ubuntu's installer favors ext3 or ext4 (depending on Ubuntu version). IMHO, ext4 isn't quite stable enough yet, although there are those who disagree. (I'm very conservative about filesystem choice, given that all my data is dependent upon a filesystem's reliability.) Certainly ext3fs has proven itself to be reliable over the years. (I prefer ReiserFS for a number of minor reasons, but ext3fs is certainly a fine filesystem and I wouldn't hesitate to use it if ReiserFS were inconvenient or unavailable to me.) The main advantage of ext4fs is that it handles big files better than ext3fs, although ext4fs also has speed advantages.

> How is the mount point for /home named?

The mount point for /home is /home -- that is, it's an empty directory called /home. Since you've already got a non-empty directory called /home, you need to copy its contents to the new to-be-/home partition, rename /home to something else, create a new empty /home directory, and mount the new partition at /home. For details, try a Web search. When I did that, I turned up quite a few tutorials, including these: [one]("http://www.psychocats.net/ubuntu/separatehome"), [two]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/"), [three.]("http://linuxtipstricks.wordpress.com/2008/10/05/how-to-create-a-separate-home-partition-in-linux-ubuntu-opensuse-mandriva-gentoo-fedora-and-so-on/") Note that I've not read any of these guides in detail, so I can't recommend one over another.

Note that there are three distinct issues that you may be confusing:


[LIST]
[*]Creating a partition
[*]Creating a filesystem
[*]Mounting a filesystem
[/LIST]


The GParted program does the first two things as one operation, but under the GParted surface they're actually different, and you can do them separately with various text-mode tools, such as fdisk and mkfs. Mounting a filesystem is done temporarily with the mount command or permanently by editing /etc/fstab.

> Finally should I attempt to have /dev/sda number sequentially or let things stick as at present  I imagine that if I delete the current extended and swap before reducing the /dev/sda1 then that should get things to run in sequence.Don't get too hung up on this. It's less confusing to a human if the order of partition numbers matches the order of partitions on the disk, but this isn't necessary for Linux, and re-ordering the partitions can cause its own problems in some circumstances. Also, be aware that the Master Boot Record (MBR) partitioning system that you're using supports just four primary partitions. An extended partition may be used in place of one of the primaries in order to support an arbitrary number of logical partitions. Primary and extended partitions are given numbers 1-4, while logical partitions are numbered from 5 up. Thus, if you have fewer than four primary/extended partitions along with logical partitions, there will be at least one gap in the sequence. If any primary partitions come after your extended partition (and therefore all the logical partitions) on the disk, those primary partitions will necessarily have numbers that are out of order, relative to their on-disk locations.

---

### Post by Scunnered on 2010-04-26
**srs5694**

Many thanks for your guidance. As I am still relevantly new to Ubuntu I think that as 9.10 & 10.04 are using ext4 I shall stick with that.  As a home user I can live with that. 

I have had a look at the links you posted and had previously looked at 2 of them and again I suppose that my inexperience put me off them as they were terminal based.  Revisiting them again it looks a bit clearer what I should be doing.  However before I do too much damage can you guide me on the creation of the partition that I want to use as home.

When I went via the live DVD and used GParted to create a new partition I left the partition as a primary one and entered the file system as ext4 and finally marked the label as /home.  It is the use of the label that I am worried about, should I have labelled it or is this done when the instructions are entered via the terminal?

If you could please advise on this I hope that it will be possible to resolve this matter.

Thanking you in anticipation

---

### Post by srs5694 on 2010-04-27
> **Scunnered said:**
> When I went via the live DVD and used GParted to create a new partition I left the partition as a primary one and entered the file system as ext4 and finally marked the label as /home.  It is the use of the label that I am worried about, should I have labelled it or is this done when the instructions are entered via the terminal?

Don't worry about the filesystem's label. Linux ignores it for most purposes. (You *can* use a label to identify a partition in /etc/fstab, but Ubuntu uses UUIDs for this purpose instead.)

---

### Post by dino99 on 2010-04-27
you can use an easy and powerfull tool: partedmagic  :P

[http://partedmagic.com/](http://partedmagic.com/)

of course, always resize partitions that are not used. Better to boot on a cd or usb OS like partedmagic

---

### Post by Scunnered on 2010-04-27
Many thanks for your responses.  What prompted the question was that when I attempted to follow the guides my system gave up the ghost.  I had to again go back to square one and re-install 10.04 RC.

Again I imagine that it is down to my stupidity as having looked again at the 3 guides offered I note that in example 2 there is a "**$**" before the instructions.  I just copied what I saw and if my assumption is right the $ was my downfall.

I will have another attempt and see how it goes and report back.  I will give it an hour or two just in case my assumptions are wrong and you know better.

Again my thanks for your kind assistance

---

### Post by srs5694 on 2010-04-27
> **Scunnered said:**
> Again I imagine that it is down to my stupidity as having looked again at the 3 guides offered I note that in example 2 there is a "**$**" before the instructions.  I just copied what I saw and if my assumption is right the $ was my downfall.

A "$" symbol is the default text-mode prompt for a user-mode shell in many distributions (including Ubuntu, unless I've changed mine and forgotten that I've done so). A "#" symbol, by contrast, normally indicates a root shell. Thus, authors (myself included, in my books) often use these symbols to indicate when you need root privileges, as in:

```

$ ls
# fdisk /dev/sda

```

The first command can be typed by anybody, but the second requires root privileges. Ubuntu doesn't support direct root logins, so in Ubuntu, you'd use "sudo" before any command that requires root privileges. (The sudo command activates root privileges for that one command.) Books sometimes describe their conventions in an introduction, but Web pages often skip that.

If you include the "$" in an on-line guide, you'd get an error message, as in:

```

$ $ ls
$: command not found

```

It's not really clear from the code block alone, but I typed "$ ls" and then got back the message "$: command not found"; the second line was the shell's output.

Whenever you follow *any* instructions that involve commands given to the computer, you *must* be alert to error messages. This is true whether it's commands typed at a shell or point-and-click instructions for a GUI program. If something unexpected happens, pay attention to it! If you don't understand it, stop the procedure until you do understand it.

That said, sometimes terminating a procedure mid-way can be dangerous. For instance, you don't want to shut down a filesystem resize operation when it's half done. Even stopping between steps can be unsafe if the early steps create a temporarily out-of-balance system that's fixed by later steps. Ultimately, you should have at least a basic understanding of what you're doing or you will get yourself into trouble. If you don't understand what a procedure is doing and why it's specifying that you use certain tools or do certain things, research those tools or steps. You can use the Linux man pages (for instance, "man fdisk" to learn about fdisk) or Google to look up specific commands or programs. Linux books in book stores or libraries may also be useful, depending on what's giving you problems.

---

### Post by Scunnered on 2010-04-27
**srs5694**

Many thanks for the explanation. So often I find myself caught where I am given more credit than my experience level.

Since I last posted I prepared things by re-sizing dev/sda1 to 10Gib and saving that. Once I confirmed that this operation had completed as expected I then established a new partition as a Primary one and ext4 also labelling it /home. I duly saved this and found that this partition now showed data as being entered yet I had made no attempt to follow any of the examples.  I am assuming that this is the small amount of data that I copied from my backup prior to establishing the partitions.

I will now follow the example given and see where this leads me and report back. I hope that there will be a smooth passage from here on in.

---

### Post by Scunnered on 2010-05-03
I appeared to get my self into such a mess that no matter what I tried the hole got deeper.  Paying attention to the strong advice of **"when in a hole stop digging"** I gave up. 

In the end I was offered else where guidance of [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome) and following this found the solution to my problem.

My sincere thanks for all your kind assistance in the matter.

---

