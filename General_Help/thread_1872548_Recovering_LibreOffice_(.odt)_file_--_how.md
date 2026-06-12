---
title: "Recovering LibreOffice (.odt) file -- how?"
date: 2011-10-30
forum: General Help
---

### Post by Mark Phelps on 2011-10-30
I'll try to keep this as unemotional as possible .. but I'm pretty disgusted that something a simple as installing CCSM in 11.10 will automatically TRASH documents -- even though I saved them before restarting!

And yes, it's done it twice now!

So, not having really had to spend any real amount of time trying to recovery documents in Ubuntu, I've only recently done some reading on testdisk and photorec.  Supposedly, the latter is what I need -- except, it does not provide any option to select .odt files, or anything like them.

I don't really want to have to browse through thousands of entries in a 105GB Ext4 partition just to find one document -- which is what I'm guessing testdisk is going to do if I turn it loose on the partition.

So, is there any simple way to recover a now missing, odt file?

UPDATE2: Sorry, after considerable searching, was not able to find the earlier page I had seen referring to the Ext4 zero filesize problem with LibreOffice.  So, I have to retract this earlier statement -- and I have added a new reply to this thread.

---

### Post by WasMeHere on 2011-11-01
Hi Mark,

According to the following thread, PhotoRec can recover odt files.
[[COLOR="RoyalBlue"]_http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec_[/COLOR]]("http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec")

I think it is worth trying, if it was a valuable file, or to be prepared, if an odt file is lost again.

If it does not work, although *cgsecurity* claims it works, maybe it is because the file header was destroyed by Libre Office.

Good luck :-)
Olle

---

### Post by WorMzy on 2011-11-01
Every time you save your document, save it as a different name.

e.g.

importantdoc-0.1.odt
importantdoc-0.2.odt
importantdoc-0.3.odt
etc.

Then, should disaster strike and you lose importantdoc-0.3.odt, you still have importantdoc-0.2.odt as a starting point.

Coupled with that, you could set up a cron-based rsync job to synchronize your works in progress to another folder and/or partition.

All this won't help you recover your lost work, but it may help you to not lose it in the future, or at least, if you do lose it, you don't lose *all* of it.

---

### Post by Mark Phelps on 2011-11-01
> **Olle Wiklund said:**
> Hi Mark,

According to the following thread, PhotoRec can recover odt files.


Yeah ... I read that too ... but when I launched Photorec, and it provided a list of file types, there was no odt in the list -- all the files were media files.

Since then, I've read that LibreOffice creates backups in a folder.  So, I went into that folder -- empty!

So now, every time I make some major changes, I'm copying it from my desktop to another partition.  It's unlikely that BOTH versions will get trashed.

---

### Post by WasMeHere on 2011-11-01
I am rather sure that PhotoRec can recover other files than media. I am not positive about odt though, but I think you might find a tab or menu where to select *office files* or something like that, and odt should be listed there.

All of us reading this thread are warned, and we should also backup extra files until we know that the bug in Libre Office is fixed.

---

### Post by WasMeHere on 2011-11-01
Hi again Mark,

I have *Ultimate Boot CD* version 5.03. The current versions is 5.1.1. I think both have *PhotoRec 6.12 included in Parted Magic*. At least on my UBCD odt files are recovered as ***zip*** files (you can untick all files and then tick zip files).

I tested it on a USB stick, and yes, PhotoRec finds odt (write) files. It also finds ods (calc) and odp (impress) files and they are readable afterwords.

Having fun finding out :-)
Olle

---

### Post by Vaphell on 2011-11-01
> Since then, I've read that LibreOffice creates backups in a folder. So, I went into that folder -- empty!

check in preferences if the autobackup feature is enabled.

---

### Post by Mark Phelps on 2011-11-01
> **Olle Wiklund said:**
> I tested it on a USB stick, and yes, PhotoRec finds odt (write) files. It also finds ods (calc) and odp (impress) files and they are readable afterwords.

OK ... but does it allow you to select ONLY odt files? I have thousands of files on the 100+GB partition and don't want to have to wade through a great long list to find the ONE odt file.

---

### Post by WasMeHere on 2011-11-01
It allows you to select only ***zip*** format files, so along with the odt files there will be other open document files, regular zip archive files etc. But all other files will be skipped, so regular rubber boots will keep you dry while wading through the file torrent ;-)

---

### Post by Mark Phelps on 2011-11-02
> **Olle Wiklund said:**
> It allows you to select only ***zip*** format files ...

So, it thinks .odt files are compressed archive files?

Sorry to keep asking, but I've been very busy and haven't had time to get to my Linux PC to try out your suggestions.

---

### Post by Vaphell on 2011-11-02
> So, it thinks .odt files are compressed archive files?

true, mainly because they are compressed archive files. Rename some .odt to .zip just for kicks and see for yourself.

---

### Post by Mark Phelps on 2011-11-02
I KNOW I should have kept the link to the page describing the Ext4 filesystem problem! I think it had something to do with delayed writes and, since my desktop crashed, I had to reboot to get it back -- but I saved the file, first.  Even then, when I got the desktop back and opened a terminal, the odt file was zero size.

So, in all fairness, I have to RETRACT my earlier statement about it being a KNOW bug.  I will continue to search for the page.  If I find it, I will update this thread.

Sorry if this causes anyone concerns -- but I really did have the .odt file zeroed out, more than once. The ONLY difference was that, in the case of using 11.10, I had the odt file stored on an Ext4 partition; whereas, with 11.04, I had the odt file stored on a FAT32 partition (for sharing with Windows).

---

### Post by vasa1 on 2011-11-02
> **Mark Phelps said:**
> ...
Since then, I've read that LibreOffice creates backups in a folder.  So, I went into that folder -- empty!
...

I think creating backups is not enabled by default. One has to go into Tools, Options, Load/Save, General and tick "Always Create a Backup Copy".

Did you do that and still find that folder empty?

---

### Post by Vaphell on 2011-11-02
yes, when you click 'save' there is no guarantee that the data is physically written to disk and that is true for all filesystems (performance would be horrible if writes were not buffered). Ext4 makes it somewhat more obvious because of the chosen balance between performance and frequency of writes.
Having said that OO/LO should try to work around the problem, like not saving file in place and always having few backup files available.

edit:
[http://codegouge.blogspot.com/2011/04/ext4-delayed-allocation-data-loss.html](http://codegouge.blogspot.com/2011/04/ext4-delayed-allocation-data-loss.html)

---

### Post by Slim Odds on 2011-11-02
This is why I still use ext3 only. For a desktop machine I see no reason to use ext4.

---

### Post by Vaphell on 2011-11-02
real world is all about tradeoffs. Ext4 is much faster than ext3, files are getting bigger and bigger and soon ext3 will appear excruciatingly slow.

---

### Post by Slim Odds on 2011-11-02
> **Vaphell said:**
> real world is all about tradeoffs. Ext4 is much faster than ext3, files are getting bigger and bigger and soon ext3 will appear excruciatingly slow.

In what context is it faster and does this matter for a desktop user?

How much faster?

Slower with NO corrupt files might be preferable for many users.

---

### Post by Mark Phelps on 2011-11-02
> **Vaphell said:**
> ... Having said that OO/LO should try to work around the problem, like not saving file in place and always having few backup files available.

Agreed ... and that's what really frustrated me.  Since the LO windows was still open, I went to the trouble to SAVE the file before closing the window.

My guess is that it was not actually saved when I rebooted the PC, as the file was zero size when I opened it again.

---

### Post by WorMzy on 2011-11-02
Well, disk buffers are supposed to be synced to disk before the computer powers off; if that's not happening, then there may be a problem with upstart, rather than the filesystem.

I'm led to believe that the 0 byte files are the product of an incorrect shutdown (e.g. power outage, hard reset, etc), rather than a problem with OOo/LO or the filesystem.

---

### Post by Slim Odds on 2011-11-02
> **WorMzy said:**
> Well, disk buffers are supposed to be synced to disk before the computer powers off; if that's not happening, then there may be a problem with upstart, rather than the filesystem.

I'm led to believe that the 0 byte files are the product of an incorrect shutdown (e.g. power outage, hard reset, etc), rather than a problem with OOo/LO or the filesystem.

You might be wrong :)

This symptom is exactly what people have been reporting about the ext4 filesystem. Though a proper shutdown should certainly flush the memory cache to disk. And it certainly sounded like Mark did a proper shutdown.

---

### Post by Vaphell on 2011-11-02
> **Slim Odds said:**
> In what context is it faster and does this matter for a desktop user?

How much faster?

Slower with NO corrupt files might be preferable for many users.

hd cameras burn gigabytes in a matter of seconds, people have huge collections of photos, music and movies. Moving that stuff around can be a huge pita and it becomes even more painful with each passing year.

but of course i agree that such kinks should be ironed out.

I think SSDs should be free of problems with buffered writes because there are no platters to be spinned up and down, no heads to be moved around

---

### Post by WorMzy on 2011-11-02
> **Slim Odds said:**
> You might be wrong :)

This symptom is exactly what people have been reporting about the ext4 filesystem. Though a proper shutdown should certainly flush the memory cache to disk. And it certainly sounded like Mark did a proper shutdown.

Which is why I suggested upstart as a possible culprit. I've been using ext4 since when it was first officially classed as stable, but I've never had one of these 0 byte files. That could be because I didn't used to write that many documents, and by the time I *did* start to write a lot of documents, I'd already moved away from Ubuntu. It could be because of my save-versioning habits (mentioned earlier in the thread). It could be because I use systemd, instead of traditional initscripts and/or upstart. It could be because I compile my own kernel.

Or it could just be one of those things, and I'll get a zero-byte file tomorrow. :P

---

### Post by Slim Odds on 2011-11-02
> **Vaphell said:**
> hd cameras burn gigabytes in a matter of seconds, people have huge collections of photos, music and movies. Moving that stuff around can be a huge pita and it becomes even more painful with each passing year.

but of course i agree that such kinks should be ironed out.

I think SSDs should be free of problems with buffered writes because there are no platters to be spinned up and down, no heads to be moved around

When writing to SSD's , they have to be written in fairly large blocks. So some intelligent write caching that consolidates the writes within the block still needs to be done. Also, SSD's still have a limited number of write cycles for each location, so "smart" writing is still needed.

---

### Post by The Cog on 2011-11-02
> **Slim Odds said:**
> In what context is it faster and does this matter for a desktop user?

How much faster?

Slower with NO corrupt files might be preferable for many users.I think slowly getting it right is vastly prefereable to quickly trashing your data. 

I tried ext4 when it first became the Ubuntu default, and suffered a number of inexplicable crashes, most of which caused quite grevious disk corruption, on 3 different PCs. So I went back to jfs (as advertised by SCOG). I can't really say if this is more crash resilient because I haven't had enough crashes to find out since then. I have vowed never to use ext4 again.

I am eager to give btrfs a go, but I have my doubts that it's really ready yet. Unplugging a btrfs USB stick seems to cause an instant black screen of death around 50% of the time, even after using umount and sync. I seem to remember something to do with delayed commits in the crash text.

---

### Post by Mark Phelps on 2011-12-01
I realize this is an old thread ... but recent info came to my attention, and folks have to know the FACTS.

I had earlier retracted my claims about LibreOffice and documents being trashed because, while I remembered finding a reported bug, I could not find it again to reference it here.

TheTrueRaven came to my rescue in a more recent thread, and WAS able to find the bug report:

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/817326]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/817326")

So, I am retracting my earlier retraction and going back to saying, now with the proof in hand, that this IS a KNOW BUG with LibreOffice.

The link to the new thread, with TheTrueRaven's response, is here:
[http://ubuntuforums.org/showthread.php?t=1889324]("http://ubuntuforums.org/showthread.php?t=1889324")

---

### Post by Vaphell on 2011-12-01
yup, reliance on the filesystem behavior in a high profile productivity suite is a fail and the fact there are no safeguards in place is a fail too. This could fly in case of some obscure little app nobody cares about but not here.

---

