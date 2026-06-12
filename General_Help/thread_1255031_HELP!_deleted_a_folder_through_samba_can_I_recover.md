---
title: "HELP! deleted a folder through samba: can I recover?"
date: 2009-09-01
forum: General Help
---

### Post by morganpatrick on 2009-09-01
This is terrible.

I was trying to copy over my baskets folder, for basket notes, from my laptop to my desktop. i went to delete my desktop baskets and i accidentally deleted my laptop baskets. Then i freaked out, then I noticed that there was a 'baskets' folder in my trash bin so i put it back on the samba share -- only it was another folder called 'baskets'

so basically i deleted a crucial folder on a remote computer through samba and replace it with THE WRONG FOLDER.

I am screwed. Please help me. I had so much information in those baskets i cannot replace that i can't do my job without them, among a ton of other things.

PLEASE HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by morganpatrick on 2009-09-01
...

---

### Post by P4man on 2009-09-01
[http://ubuntuforums.org/showthread.php?t=893048](http://ubuntuforums.org/showthread.php?t=893048)

good luck :s

---

### Post by morganpatrick on 2009-09-01
The problem with using foremost, or most undelete programs, is that it looks at headers and footers to find deleted files. That's fine if it's a jpeg and there's jpeg support -- but .basket files? None of these are going to support that.

I have also heard that in general, it is very difficult to undelete from ext3 partitions. Maybe I can use a live disk or something... I don't know. Any advice would be well, well appreciated, though.

By the way, I'm a big fan of therealnews.com. Thank you for the advice.

I'm googling 'ext3 undelete' now and as soon as I figure out a solution I will post it. thanks again.

---

### Post by morganpatrick on 2009-09-01
...

---

### Post by P4man on 2009-09-01
not even sure what a .basket file is, but you might be right.

Well, first of all, Id advice you to make an image of the drive with dd.
Then you can try some recovery tools on the image. testdisk is a popular one, but a quick look at the documentation suggests it can undelete from ext2 only, not ext3/4 (for ext3/4 it suggests photorec, which has the same problem as foremost). Then again Ext3 can be mounted as Ext2, so perhaps it does work? I dont know. Find out

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

This seems to be another potential solution:

[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

Looks like a lot of reading though. Heh.

In the future, aside from making backups, you know, use something like Unison to sync your files. Avoids making mistakes. Unison is in the repo's and is very easy to use and quite flexible.

---

### Post by morganpatrick on 2009-09-01
yeah here's the bummer: I have unison, and the whole reason i was doing this was to start using it. in the past, when i've used sync programs, it assumes whatever file/folder is newest is what you want to keep. so when i reinstalled ubuntu on my desktop, i was trying to replace all the config files with the ones from my laptop so that i could start using unison with  more-or-less symmetrical folder pairs. that's when i deleted all my basket files.

I found that second link you posted, and I'm going to try it out tomorrow. I might move my files off ext3, though, and onto ext2 if it's this difficult to undelete.

Let me ask you this, P4man: If I'm trying to recover 10 mb of data, and I use dd to make an image of a 200 gb drive, 120 gb of which is filled up, that means I need 200 gb of space to put this image, right? or am I not understanding disk imaging?

Thanks again.

---

### Post by morganpatrick on 2009-09-01
...

---

### Post by P4man on 2009-09-01
No you got it right. You'll need 200GB. Or a bit less if you compress the image (but I doubt those apps can work straight on a compressed image)

. Thing is, you dont know which bits to image, so you need them all ...

---

### Post by morganpatrick on 2009-09-01
one more question before i do this: should I do this from a live cd or just login as root? since my /home folder is on a different partition, I would think that if i was logged in as root then i wouldn't be mounting /home.

---

### Post by P4man on 2009-09-01
Not sure how you planned to log in as root, unless you meant a root terminal from the recovery console, but I would use a livecd anyhow

---

### Post by morganpatrick on 2009-09-01
I've read enought that says you should never login to the gui as root, that I'm going to stop taking risks and actually take your advice in making an image with dd. I don't know anything about dd but I'm assuming I can image my laptop onto a spare hard drive through a crossover cable, and from that point I can keep booting and using my laptop because if my data is there, it's in the image.

Although, it kind of brings up another interesting issue: If I'm making an image on top of an old hard drive, and ext3grep is deep digging for data, aren't I just making it that much harder since the image is now sitting on a bed of old data? hmm...

---

### Post by P4man on 2009-09-01
> **morganpatrick said:**
> I've read enought that says you should never login to the gui as root, that I'm going to stop taking risks and actually take your advice in making an image with dd. I don't know anything about dd but I'm assuming I can image my laptop onto a spare hard drive through a crossover cable, and from that point I can keep booting and using my laptop because if my data is there, it's in the image.

Not sure what you mean by "crossover cable" (to me thats an ethernet cable with crossed wires?), but I guess you mean an USB enclosure or something.

using dd isnt all that hard. 

dd if=/dev/sourceharddisk of=/mountpoint/image.img BS=1M

If you have >1 partition on that drive, you can image only that partition by using (for instance) /dev/sdb2 as input.

Just beware that as long as dd runs, there is no ouput. It appears "hung" until it completed its job. The BS=1M sets blocksize to 1MB. Thats a lot faster than copying 1 bit at a time.

> 
Although, it kind of brings up another interesting issue: If I'm making an image on top of an old hard drive, and ext3grep is deep digging for data, aren't I just making it that much harder since the image is now sitting on a bed of old data? hmm...


No, it makes no difference. It would be something else if you where using forensic tools trying to recover overwritten data by "measuring magnetism" and trying to figure out if a "0.3235" was really a 1 or a zero :). 

But that is not what you are trying here, your "bits" are fine, its the filesystem that you want to rebuild and and "dd" makes an image that contains an exact copy of the original, every bit you have on the original will be on the image.

---

### Post by morganpatrick on 2009-09-01
I see. Thanks a million for all this help, p4man.

a crossover cable is an ethernet cable with two of the wires crossed. For whatever reason, this allows you to chain two computers together with no router. So I'm going to take my crossover cable, connect the two computers through ethernet, boot the laptop with a live CD, then dd the image of the partition through the cable onto this spare hard drive.

We'll see if it works. I also restarted the laptop last night, after i deleted these files, and started searching for a solution, until i came to a comment that as soon as you remount your partition you make it that much harder again to recover data -- AND when it was rebooting it did a disk check... so far it looks like ive done everything wrong I could do.

Anyway, away we go. Thanks again for all the help. Oh and I'm making yet another mistake based on my plans above, please let me know.

Thanks.

---

### Post by P4man on 2009-09-01
Ive never used dd over a network. I suppose it should work if you mount a network drive from the live session, and then feed it the right mountpoint as OF. I googled, and saw this solution, using ssh:

[http://karlherrick.com/dev/2008/09/12/dd-backups-over-ssh/](http://karlherrick.com/dev/2008/09/12/dd-backups-over-ssh/)

edit: btw, transferring 200GB over ethernet, it will take a while :)

---

### Post by morganpatrick on 2009-09-01
...

---

### Post by morganpatrick on 2009-09-01
Hey P4man or whomever,

I ran dd and opted to back up my hard drive in 638 mb chunks, as reccommended by a tutorial I read. This way I can put this on DVD.

The one thing I didn't understand about these dd instructions was, what happens when you copy over an img file? How to I 'burn' this onto the drive? Do I do that?

Also, now that this is in chunks, I doubt I have enough room for the compressed files and the uncompressed. So maybe I have to start over now?

Was the point just to have a backup? Because I suppose I can try to undelete from the original drive now that there's a backup -- or was there a reason to use an image other than backing up?

Anyway I'm on hour 9 of solving this problem for today, plus some hours yesterday so any help is greatly, greatly appreciated.

---

### Post by P4man on 2009-09-02
just burn them to a cd as files (drag an drop them on to an empty cd or dvd)
Im not sure that is a convenient way of doing things though, as you'll need to reassemble all these on to a harddisk before you can run any recovery program on them, but I guess it beats not having a backup.

The idea of making an image is that you can resume working normally on your computer without fear of making things worse, and you can use the image to recover your files.  But if you're putting the image on 30 Cd's.. then, well, Id try to run to recovery on your actual harddisk, and keep the backup in case you mess things up or make it worse.

---

### Post by morganpatrick on 2009-09-02
edt// nevermind

---

### Post by morganpatrick on 2009-09-04
Update, day 5:

Ran [Ext3undel]("http://projects.izzysoft.de/trac/ext3undel") on the image. Recovered everything it could find. no trace of my file. In fact, just from the files I looked at, it became apparent to me that it somehow dredged up all these deleted files that were on the disk before i formatted and burned the image from my laptop. I don't know how that's possible but that's what appears to have happened.

Ext3grep did not recover my files. I don't know why not. Maybe it was because I mounted the laptop drive after deleting and restarting. Maybe it's because I overwrote the directory I was trying to recover. Like I said, I did about everything wrong in this process.

The lesson learned here, though, is that ext3undel is apparently a very effective and powerful tool -- just run it from the actual disk you're trying to recover files from and not from an image of that disk.

---

### Post by P4man on 2009-09-05
Im sorry to hear that :(

However, recovering from an image is 100% the same as recovering from the actual disk. dd makes a bit for bit identical copy, no information is lost in the process. Every remaining piece of file is copied, each bit on that drive.

Now the "magnetic shadow" (for lack of better word) of *overwritten* data that does get "lost" when making an image, is not something any program can use anyway. You need very special tools for that, you have to disassemble the drive, and it will still never produce intact files, just files that may look a bit like the original using statistics to come up with a gamble for each bit. Useful perhaps if you're chasing terrorists and trying to recover an email with 50% of the text being garbled, but not much else.

---

