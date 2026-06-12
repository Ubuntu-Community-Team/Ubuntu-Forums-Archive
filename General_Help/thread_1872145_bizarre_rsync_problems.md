---
title: "bizarre rsync problems"
date: 2011-10-30
forum: General Help
---

### Post by NautiusMaximus on 2011-10-30
Forgive me if I'm missing something really obvious here, as I'm a bit of an Ubuntu n00b, but I'm having problems trying to get a backup to work using rsync. In summary, my script works when run from the terminal, but does really strange things when it runs as a cron job.

Now the detail...

I have written a small script to back up all the files in my home directory. It contains a line that looks like this:

```
rsync -tr --delete --exclude=".*" /home/myname /media/lsduo
```

If I run the script manually from the terminal using sudo, then it does exactly what I want it to do, namely copy the contents of my home folder to my external NAS drive, which is already mounted at /media/lsduo.

So far so good.

However, if I set it up to run as a cron job, it does some very strange things. As far as I can see, it's copying everything across, but not respecting a directory structure: everything is just loose in the /media/lsduo folder.

But it gets weirder than that. If I view the contents of the folder through my Ubuntu PC, the files have names such as "\myname\documents\document.odt", as if they are trying to fit into a directory structure (yes, I did have those slashes the right way round). But the documents seem to be corrupted in some way, in that I can't open them.

On the other hand, if I view the contents on a Windows PC, the file names have become mangled, and have names such as "_2ZEG9~8.JPG" (the file extensions seem to be respected correctly). I can also open the documents without any problems on a Windows PC.

This all seems completely inexplicable to me. Does anyone have any idea what might be going on?

I'm using Ubuntu 11.04, and the external NAS drive is a Linkstation Duo formatted with xfs.

Thanks
NM

---

### Post by killermist on 2011-10-30
Have you considered using "-a" instead of "-tr"? (probably not directly related to the problem)

Are you trying to prevent hidden directories from copying?  And if so, why?
Followup to that, from the terminal, is the ".*" being sent properly to rsync, whereas in cron, it needs additional escaping to pass successfully to rsync?

I've had tons of bad luck in trying to use .* to include or exclude hidden directories because .* (when resolved by bash, and other things) includes ".." and several other things that I DON'T want to match.

---

### Post by Rhizoid on 2011-10-30
How is the NAS drive formatted?  Judging by some of the errors I'm guessing it's NTFS

Instead of using rysnc to copy, why not tar your home drive and compress it at the same time - this works very well with cron too.

```

tar -cpzf /media/lsduo/homefolder.tar.gz /home/myname --exclude="/home/myname/.*"
```

the options are:
c = create
p = retain permissions data
z = use gzip to compress (replace with j to use bzip for slightly better compression but slower performance)
f = direct output to a file
--exclude="excludes the folder listed here" - can be used more than once to exclude multiple folders.

Personally, I'd rather backup all the hidden folders as things like your Thunderbird profile won't get backed up if you don't.

Nicely, this creates a single compressed file which you can easily archive if you want a more permanent restore point.

Hope that helps,

---

### Post by NautiusMaximus on 2011-10-30
Thanks for the replies.

The reason I'm excluding hidden files is that I thought they were probably not useful, but you've made me rethink that. I also found errors when backing up everything, but on closer inspection it was a specific folder called ".gvfs" which was causing the problems, so now I'm excluding only that one.

We'll see what happens when the cron job next runs, but the same thing happened before I excluded anything, so I'm not hopeful.

Don't I need to use -r if I want to back up folders recursively? Surely if I'm going to try -a that should be just instead of -t and not instead of -r, right? Or have I misunderstood how it works?

The suggestion to use tar instead of rsync is a potential workaround, but it's definitely a workaround rather than a fix. I'm reluctant to do that unless I have to, because if I wrap everything into one big compressed file, then it's a bit more of a faff if I need to restore a single file (experience has taught that backups are vastly more likely to be useful in case of accidental overwriting of a single file rather than disaster recovery). I'd like to keep on at this until I find a fix.

The NAS drive is not formatted with ntfs, it's formatted with xfs.

I wonder if this could be some bizarre permission thing? I've checked the permissions on the folder that's been created in the NAS drive, and it says that the owner is "99 - user #99", which is something I haven't seen before, and I suspect can't be right.

I've set permissions to the folder I'm using as a mount point to 777 and the NAS drive has security disabled altogether, so there shouldn't be any permissions problems in theory, but even so, it does look a bit odd.

Many thanks for any further thoughts on this.
NM

---

### Post by Rhizoid on 2011-10-30
You can quickly and easily restore a single file from a tarbal...

```
tar -xvpzf tarball.tar.gz {filename.extenstion}
```I agree regarding restores - far more likely due to an over-write than a real disaster, but how frequently is the realization of the overwrite 24hrs + after the fact?

Encrypting the tarball so it can be safely stored by a free service like dropbox is a snap too

```
tar -cpz {source} | openssl aes-256-cbc -salt -pass pass:{password} > {tarball.enc.tar.gz}
```To extract from an encrypted tarball created as above use:

```
cat {tarball.enc.tar.gz} | openssl aes-256-cbc -salt -d | tar -xzf {file/dir name if required to extract a single file/directory}
```Just replace the bits in { } with your own information.

You don't need a -r switch with tar - the default behaviour is to descend into child directories.

Excluding the .gvfs directory is a good idea whichever solution you choose.

Cheers,

---

### Post by pr3zident on 2011-10-30
> **Rhizoid said:**
> How is the NAS drive formatted?  Judging by some of the errors I'm guessing it's NTFS

Instead of using rysnc to copy, why not tar your home drive and compress it at the same time - this works very well with cron too.

```

tar -cpzf /media/lsduo/homefolder.tar.gz /home/myname --exclude="/home/myname/.*"
```

the options are:
c = create
p = retain permissions data
z = use gzip to compress (replace with j to use bzip for slightly better compression but slower performance)
f = direct output to a file
--exclude="excludes the folder listed here" - can be used more than once to exclude multiple folders.

Personally, I'd rather backup all the hidden folders as things like your Thunderbird profile won't get backed up if you don't.

Nicely, this creates a single compressed file which you can easily archive if you want a more permanent restore point.

Hope that helps,

With rsync instead of copying the files over and over again to the destination it just appends the new files and updates the file.. depending on the backup this can be a long or short process. How does tar back up data its just copies backup.tar.gz to the destination or does exactly what rsync does ? and with rsync you have quicker access to your files right you don't have to extract anything... why should a person pick tar over rsync and vice versa ?

---

### Post by jacob.david on 2011-10-30
Can you try by making a script with the rsync command, test it with the command line and then just call this script from the crontab. Also read about the -R (--relative) option in the manual page and see whether it solves your problem.

The .gvfs file I have observed with samba mounts on home folder.

I too prefer rsync over tar because for incremental changes you don't have to keep backing up the entire folder. However every once in a while take a backup of snapshot as a tar ball and keep it with the date.

---

### Post by pr3zident on 2011-10-30
> **jacob.david said:**
> Can you try by making a script with the rsync command, test it with the command line and then just call this script from the crontab. Also read about the -R (--relative) option in the manual page and see whether it solves your problem.

The .gvfs file I have observed with samba mounts on home folder.

I too prefer rsync over tar because for incremental changes you don't have to keep backing up the entire folder. However every once in a while take a backup of snapshot as a tar ball and keep it with the date.

what do you mean take a backup of snapshot as a tar ball ? it just so happen that i made my first backup script this week using rsync and i see this post

---

### Post by jacob.david on 2011-10-30
[FONT="Verdana"][SIZE="2"]What I mean is, in addition to your rsync, say for every month create a tar ball of /home/yourname and store it like bkup_yyyymm.tar.gz. So at any time if you want a certain file as it was 6 month ago, the you can retrieve it from this.
It just depends on your requirements. If you think you are never going to be in a situation like this, where you will need a snapshot from the past, then you can very well skip this [/SIZE][/FONT]

---

### Post by pr3zident on 2011-10-30
> **jacob.david said:**
> [FONT="Verdana"][SIZE="2"]What I mean is, in addition to your rsync, say for every month create a tar ball of /home/yourname and store it like bkup_yyyymm.tar.gz. So at any time if you want a certain file as it was 6 month ago, the you can retrieve it from this.
It just depends on your requirements. If you think you are never going to be in a situation like this, where you will need a snapshot from the past, then you can very well skip this [/SIZE][/FONT]

Oh ok I understand that's a smart idea .....

---

### Post by NautiusMaximus on 2011-10-31
> **jacob.david said:**
> Can you try by making a script with the rsync command, test it with the command line and then just call this script from the crontab. 

Not sure what you mean there. I have a script, and if I call it from the command line, it works just fine. If I put it in my /etc/cron.daily folder, it runs at the appropriate time, but then gives the bizarre behaviour I've described. Is that what you meant?

I've now tried it with the -a switch, and with that it no longer works from the command line. It gives a whole bunch of errors saying "chown xxx failed: permission denied".

Any ideas?

---

### Post by NautiusMaximus on 2011-10-31
Oh, and one more bizarre fact which probably supports my theory that it's a permissions thing:

When I try to remove all the unwanted files from the NAS drive, I have to run both the following commands to do so:

```
rm -r -f *
sudo rm -r -f *

```

It seems that neither command on its own has sufficient permissions to delete all the files. Some can be deleted as myself but not as root, and vice versa.

---

### Post by HermanAB on 2011-10-31
Hmm, as mentioned by another poster, beware of ".*", because "*" includes ".", which means that you also get "..", which goes back one directory level, which can then cause huuuuuge trouble.

---

### Post by Rhizoid on 2011-10-31
> **pr3zident said:**
> why should a person pick tar over rsync and vice versa ?

That's a very good question - personally I prefer tar to rsync for the following reasons:

1.) I'm not bandwidth restricted while creating the tarball - it's created locally and only a weekly backup tarball is copied offsite - this is also encrypted.

2.) I'm not backing up large quantities of data which could easily be redownloaded in it's original form - eg music or video.  My important backup consists of several hundred MB of spreadsheets, databases and text files.

3.) I don't need immediate access to a single file in the tarball - I can wait the, perhaps tens of minutes to access any single file I may need to restore.

4.) I might discover a data entry error several days after it's made... or it might be several weeks even.  In which case having only a single backup set and a single snapshot which could be up to a month old doesn't allow me the flexibility to return to a given point in time.

Reasons to prefer rsync over tar, in my opinion, would be pretty much the reverse of the reasons I prefer tar.

---

### Post by pr3zident on 2011-10-31
> **Rhizoid said:**
> That's a very good question - personally I prefer tar to rsync for the following reasons:

1.) I'm not bandwidth restricted while creating the tarball - it's created locally and only a weekly backup tarball is copied offsite - this is also encrypted.

2.) I'm not backing up large quantities of data which could easily be redownloaded in it's original form - eg music or video.  My important backup consists of several hundred MB of spreadsheets, databases and text files.

3.) I don't need immediate access to a single file in the tarball - I can wait the, perhaps tens of minutes to access any single file I may need to restore.

4.) I might discover a data entry error several days after it's made... or it might be several weeks even.  In which case having only a single backup set and a single snapshot which could be up to a month old doesn't allow me the flexibility to return to a given point in time.

Reasons to prefer rsync over tar, in my opinion, would be pretty much the reverse of the reasons I prefer tar.

I digz, I think I will do a backup with rsync and do a snapshot with tar I don't like that my information in a tar can only be accessible on my Linux(and my Mac I'm guessing) so I won't be able to easily access my data if I have to open it up on my other systems ? Or am I wrong ?

---

### Post by killermist on 2011-11-01
Sorry it took me a while to get back to this thread.

According to the rsync help:
> 
 -a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)
 -r, --recursive             recurse into directories
 -l, --links                 copy symlinks as symlinks
 -p, --perms                 preserve permissions
 -o, --owner                 preserve owner (super-user only)
 -g, --group                 preserve group
 -t, --times                 preserve modification times
 -D                          same as --devices --specials
     --devices               preserve device files (super-user only)
     --specials              preserve special files

 -H, --hard-links            preserve hard links
 -A, --acls                  preserve ACLs (implies --perms)
 -X, --xattrs                preserve extended attributes

 -a pulls in a bunch of the permission/ownership/time/link-ness stuff in addition to recursing by default.
I will often add -H to store hard links as hard links on devices that can handle them because there's no reason to have multiple copies of a single file that's been hard linked multiple times.

As to the tar-vs-rsync argument, I think that some backups work OK as tars, but they suffer the need to be "unwrapped" later if you need to pull something back out of them.  Also, rsync (if properly configured/scripted) can do incremental backups where each new backup is completely functional by itself, but uses the space savings of hard links for files that don't change.

```
$ sudo du -hsc torrent-pool/home-backups/*/2011*
126G	torrent-pool/home-backups/grace@grace/2011-10-27
626M	torrent-pool/home-backups/grace@grace/2011-10-28
676M	torrent-pool/home-backups/grace@grace/2011-10-29
547M	torrent-pool/home-backups/grace@grace/2011-10-30
572M	torrent-pool/home-backups/grace@grace/2011-10-31
64G	torrent-pool/home-backups/killermist@grace/2011-10-28
3.2M	torrent-pool/home-backups/killermist@grace/2011-10-29
3.2M	torrent-pool/home-backups/killermist@grace/2011-10-30
3.1M	torrent-pool/home-backups/killermist@grace/2011-10-31
2.0K	torrent-pool/home-backups/killermist@killermist/2011-10-28
2.0K	torrent-pool/home-backups/killermist@killermist/2011-10-29
1.7G	torrent-pool/home-backups/killermist@killermist/2011-10-30
13M	torrent-pool/home-backups/killermist@killermist/2011-10-31
194G	total
```

I've attached (gzipped) a copy of the rsync backup script I'm using from a 3 accounts across 2 different machines to make backups to a different storage machine.  It should be easy enough to modify for whatever your purpose is.  I tried to make it as modular as possible.

---

### Post by Rhizoid on 2011-11-01
I like that a lot!

One small point - how do you abandon a backup set once it's definitely of no further use?  Example - I keep a 3month rolling backup set, anything older than 3 months is completely discarded as the backup policy document requires it.  Obviously tar lends itself to this very easily, you just delete the files older than 3 months.  Is there similar functionality for rsync or is it a case of start over and archive the previous backup until old enough to permanently delete?

---

### Post by killermist on 2011-11-01
> **NautiusMaximus said:**
> Not sure what you mean there. I have a script, and if I call it from the command line, it works just fine. If I put it in my /etc/cron.daily folder, it runs at the appropriate time, but then gives the bizarre behaviour I've described. Is that what you meant?The perk of making the procedure a script is that if the script works properly when called directly from the terminal, it should work just fine when summoned by cron.  As in wild cards aren't prematurely resolving or anything.

> **NautiusMaximus said:**
> I've now tried it with the -a switch, and with that it no longer works from the command line. It gives a whole bunch of errors saying "chown xxx failed: permission denied".
It sounds like ownership/group-ship information isn't being retained. 
Possible causes:  
1.) Your user doesn't own the directory you're copying to (though the copy would probably fail on that)
2.) The filesystem doesn't like ownership (maybe group) changes (possibly NTFS or VFAT?)

Maybe -a isn't a good option for syncing in this case.  Maybe -rt is your best set of options in this case.

---

### Post by killermist on 2011-11-01
> **Rhizoid said:**
> I like that a lot!

One small point - how do you abandon a backup set once it's definitely of no further use?  Example - I keep a 3month rolling backup set, anything older than 3 months is completely discarded as the backup policy document requires it.  Obviously tar lends itself to this very easily, you just delete the files older than 3 months.  Is there similar functionality for rsync or is it a case of start over and archive the previous backup until old enough to permanently delete?

Removal of any specific day or group thereof is easy.
```
rm -fr torrent-pool/home-backups/grace@grace/2011-10-27
```
Since they're all hard links of the same files with the only changes between them being what changed day-to-day, each day is "shelf stable".
Deleting any day out of the middle, or all days older than 30, or every 3rd red moon day, or whatever makes no affect on any other snapshot.

The only minor hazard to mention is that with all the archives using hard links for identical files, if you go into the backups and change a file, any other backup referencing that file will also be changed.

---

### Post by Rhizoid on 2011-11-01
Thanks for the clarification killermist - the potential to update every backup with a single edit is, unfortunately, the killer for me but for home use it's spot on.  I imagine this is precisely the way Mac's Timecapsule backup does what it does, perhaps with a slightly niftier looking interface, but still...

Apologies to the OP for the hijack ;)

Cheers,

---

### Post by killermist on 2011-11-01
As long as the backup is being used for backup purposes and not as a working platform, the hazard of edits shouldn't be a problem.

---

### Post by killermist on 2011-11-01
> **pr3zident said:**
> I digz, I think I will do a backup with rsync and do a snapshot with tar I don't like that my information in a tar can only be accessible on my Linux(and my Mac I'm guessing) so I won't be able to easily access my data if I have to open it up on my other systems ? Or am I wrong ?

There are several tools for windoze that can decompress tar, tar-gz, and tar-bz2 files.  If I recall, winzip, winrar, and IZarc can all decompress tar and tar-gz files.  Not as sure about tar-bz2.

Tarballs as longer-term backups used in tandem with the script I attached a few posts earlier would make a good solution in that case.

---

### Post by pr3zident on 2011-11-02
> **killermist said:**
> There are several tools for windoze that can decompress tar, tar-gz, and tar-bz2 files.  If I recall, winzip, winrar, and IZarc can all decompress tar and tar-gz files.  Not as sure about tar-bz2.

Tarballs as longer-term backups used in tandem with the script I attached a few posts earlier would make a good solution in that case.

Cool i used winrar all the time ... smh only thought it was good for rar files lol well that's all i used it for.

---

