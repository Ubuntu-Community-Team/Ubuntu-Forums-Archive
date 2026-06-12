---
title: "Backing up, with an eye to future installations..."
date: 2010-02-07
forum: General Help
---

### Post by cfogelberg on 2010-02-07
Hello all,

I am looking into backup solutions for my current installation of Ubuntu. To date I've been a little bit haphazard. Ideally I'd write a simple script that used rsync. There are two things that seem to make this hard. 

Firstly, not everything in my home directory is owned by me (some stuff in .cpan is owned by root?). This causes all kinds of issues (e.g. it breaks rsync's --delete option) and just seems weird. Is it weird and do I need to start chowning? If not how should I work around it?

Secondly, in a couple of months time I want to change my set up. Currently I'm dual booting 9.04 and Vista, and my music and media are on a shared NTFS partition. When 10.04 is released I want to use that as a host instead, with virtual box images for Vista and a 10.04 install that I'd use for my daily work. Music and media would live in folders on the host that I'd share to the virtual machines. When I back up my home directory and /etc, I'm worried that the permissions won't transfer nicely to the new install, even if I use the same username. Is this something I need to be worried about? If so, what should I do?

Unrelatedly, but thirdly, what should I backup? I keep a change log, and obviously I'll back that up along with all my other personal files and home directory. I also think I should back up /etc. Is there anything else?

Any advice and help you can offer would be much appreciated! Thanks :)

Christo

---

### Post by labinnsw on 2010-02-13
[This link should have all the information you need.]("http://ubuntuforums.org/showthread.php?t=1383329")

---

### Post by bhencetotozo on 2010-02-13
> **cfogelberg said:**
> Hello all,

I am looking into backup solutions for my current installation of Ubuntu. To date I've been a little bit haphazard. Ideally I'd write a simple script that used rsync. There are two things that seem to make this hard. 

Firstly, not everything in my home directory is owned by me (some stuff in .cpan is owned by root?). This causes all kinds of issues (e.g. it breaks rsync's --delete option) and just seems weird. Is it weird and do I need to start chowning? If not how should I work around it?

Secondly, in a couple of months time I want to change my set up. Currently I'm dual booting 9.04 and Vista, and my music and media are on a shared NTFS partition. When 10.04 is released I want to use that as a host instead, with virtual box images for Vista and a 10.04 install that I'd use for my daily work. Music and media would live in folders on the host that I'd share to the virtual machines. When I back up my home directory and /etc, I'm worried that the permissions won't transfer nicely to the new install, even if I use the same username. Is this something I need to be worried about? If so, what should I do?

Unrelatedly, but thirdly, what should I backup? I keep a change log, and obviously I'll back that up along with all my other personal files and home directory. I also think I should back up /etc. Is there anything else?

Any advice and help you can offer would be much appreciated! Thanks :)

Christo
[B]
Step 1) Empty Trash
Step 2) su (password)
Step 3)cd / (to go to root folder)
Step 4)(Creating backup.tgz)[/B]

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt /

The step above, is not for EXTRA HIGH compression. I use it because its a bit faster.

**Step 5)(Restoring backup.tgz backup you just created)**

 tar xvpfz backup.tgz -C /


****NOTE: Read the steps below to make you understand why it does what it does. I found this article many years ago, and I am passing it to  you.**


The 'tar' part is the program we're going to use.
 
'cvpfz' are the options we give to tar, like 'create archive' (obviously),
'preserve permissions'(to keep the same permissions on everything the same), and 'gzip' to keep the size down.
 
Next, the name the archive is going to get. backup.tgz in our example.
 
Next comes the root of the directory we want to backup. Since we want to backup everything; /
 
Now come the directories we want to exclude. We don't want to backup everything since some dirs aren't very useful to include. Also make sure you don't include the file itself, or else you'll get weird results.
You might also not want to include the /mnt folder if you have other partitions mounted there or you'll end up backing those up too. Also make sure you don't have anything mounted in /media (i.e. don't have any cd's or removable media mounted). Either that or exclude /media.
 
EDIT : kvidell suggests below we also exclude the /dev directory. I have other evidence that says it is very unwise to do so though.
 
Well, if the command agrees with you, hit enter (or return, whatever) and sit back&relax. This might take a while.
 
Afterwards you'll have a file called backup.tgz in the root of your filessytem, which is probably pretty large. Now you can burn it to DVD or move it to another machine, whatever you like!
 
EDIT2:
At the end of the process you might get a message along the lines of 'tar: Error exit delayed from previous errors' or something, but in most cases you can just ignore that.
 
Alternatively, you can use Bzip2 to compress your backup. This means higher compression but lower speed. If compression is important to you, just substitute
the 'z' in the command with 'j', and give the backup the right extension.
That would make the command look like this:
 
Code:
 
tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys /
 
2: Restoring
 
Warning: Please, for goodness sake, be careful here. If you don't understand what you are doing here you might end up overwriting stuff that is important to you, so please take care!
 
Well, we'll just continue with our example from the previous chapter; the file backup.tgz in the root of the partition.
 
Once again, make sure you are root and that you and the backup file are in the root of the filesystem.
 
One of the beautiful things of Linux is that This'll work even on a running system; no need to screw around with boot-cd's or anything. Of course, if you've rendered your system unbootable you might have no choice but to use a live-cd, but the results are the same. You can even remove every single file of a Linux system while it is running with one command. I'm not giving you that command though!
 
Well, back on-topic.
This is the command that I would use:
 
Code:
 
 tar xvpfz backup.tgz -C /
 
Or if you used bz2;
 
Code:
 
 tar xvpfj backup.tar.bz2 -C /

---

