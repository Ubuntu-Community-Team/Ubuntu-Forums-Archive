---
title: "rsync command needs help exclude command not excluding"
date: 2012-04-23
forum: General Help
---

### Post by AlexOnVinyl on 2012-04-23
Here's what I'm trying to do - back up all the folders in my home directory except /Videos/.

This is the command I have made: ```
rsync --progress -rEog --exclude-from="~/Videos" /home/alex /media/backup/12.04-Precise-backup_4.23.2012/
```

I've also tried without the quotes and = sign.  I've also tried this:

```
rsync --progress -rEog --exclude home/alex/Videos /home/alex /media/backup/12.04-Precise-backup_4.23.2012/
```

But all of them still create the same Videos folder..

What am I doing wrong?

---

### Post by oldfred on 2012-04-23
I do not fully understand rsync. It  has many options and parameters. I just copied something that worked for me.

I think the --exclude-from expects a file name with the list of excludes.
see 
man rsync
>             --exclude=PATTERN       exclude files matching PATTERN
            --exclude-from=FILE     read exclude patterns from FILE


This works for me. But I want to exclude more than just my .thumbnails and want to create a list and use the --exclude-from=file

rsync -aurvlP --exclude '.thumbnails' /home /mnt/Backup

---

### Post by gsgleason on 2012-04-23
I thought I got it working but was wrong.  This is weird.

[edit]

Try this:
```

cd ~
rsync --progress -rEog --exclude=/Videos /home/alex/ /media/backup/12.04-Precise-backup_4.23.2012/

```

Important things I learned from the man page and from testing:

The exclude pattern starting with a slash (/) means that it's relative to the transfer-root, not the filesystem root.

When you include a trailing slash in you transfer root, that directory becomes the transfer root, otherwise the parent directory is.  Example:

This should create the directory 'alex' in the destination directory, ending up with /destination/alex/files
```
rsync -r /home/alex /destination
```

This, on the other hand, copies each file within /home/alex to the destination without creating an 'alex' directory. Notice the tailing slash on the source directory:
```
rsync -r /home/alex/ /destination
```

This will create various subdirectories in the destination:

So, back to your command, if you DO NOT include the trailing slash in the source, your pattern would need to be **/alex/Videos** whereas if you DO include the trailing slash in your source, your pattern would be **/Videos** because the trailing slash on the source changes your transfer-root.

---

### Post by AlexOnVinyl on 2012-04-23
> **gsgleason said:**
> I thought I got it working but was wrong.  This is weird.

[edit]

Try this:
```

cd ~
rsync --progress -rEog --exclude=/Videos /home/alex/ /media/backup/12.04-Precise-backup_4.23.2012/

```

Important things I learned from the man page and from testing:

The exclude pattern starting with a slash (/) means that it's relative to the transfer-root, not the filesystem root.

When you include a trailing slash in you transfer root, that directory becomes the transfer root, otherwise the parent directory is.  Example:

This should create the directory 'alex' in the destination directory, ending up with /destination/alex/files
```
rsync -r /home/alex /destination
```

This, on the other hand, copies each file within /home/alex to the destination without creating an 'alex' directory. Notice the tailing slash on the source directory:
```
rsync -r /home/alex/ /destination
```

This will create various subdirectories in the destination:

So, back to your command, if you DO NOT include the trailing slash in the source, your pattern would need to be **/alex/Videos** whereas if you DO include the trailing slash in your source, your pattern would be **/Videos** because the trailing slash on the source changes your transfer-root.
So as far as the trailing slash goes - how would I make sure to specify to exclude the folder /alex/Videos/ from the recursive copy?

---

### Post by agillator on 2012-04-23
At the risk of stating the obvious, rsync can be confusing. To do what I think you are trying to do, 'rsync -av --except Videos /home/alex/ /media/backup/' should do it - I simplified the destination a little. That should copy everything in alex to /media/backup except anything named Videos (file or directory). Note /home/alex/. If I had used /home/alex it would have copied the tree rooted at alex to /media/backup, so you would see /media/backup/alex/, not /media/backup/<contents of alex>. Of course the alex directory would have the entire tree. Does this help? The -a switch combines a lot of switches. For details, see the man page.

---

### Post by AlexOnVinyl on 2012-04-23
> **agillator said:**
> At the risk of stating the obvious, rsync can be confusing. To do what I think you are trying to do, 'rsync -av --except Videos /home/alex/ /media/backup/' should do it - I simplified the destination a little. That should copy everything in alex to /media/backup except anything named Videos (file or directory). Note /home/alex/. If I had used /home/alex it would have copied the tree rooted at alex to /media/backup, so you would see /media/backup/alex/

Actually, thats fine with me, I can restore from that as well, I have the reverse command just not the command that copies it and the reason I set so many params was to keep the ownership as well as the file properties.

> **agillator said:**
> 
not /media/backup/<contents of alex>. Of course the alex directory would have the entire tree. Does this help? The -a switch combines a lot of switches. For details, see the man page.

So what you're saying is instead of using:

```
rsync --progress -rEog --exclude=/Videos /home/alex/ /media/backup/12.04-Precise-backup_4.23.2012/
```

I can use the following:

```
rsync --progress -rEog --except Videos /home/alex/ /media/backup/12.04-Precise-backup_4.23.2012/
```

But that would mean I would also have to cd into the directory itsself then?

---

### Post by agillator on 2012-04-24
I must have been asleep - not 'except', but 'exclude'. I am terribly sorry about that, I try to be so careful. However, '--exclude Videos' is correct, no equal sign.  The key on whether or not the directory itself is copied or just the contents is the slash at the end of the source: /home/alex/ means the contents of the directory will be copied, /home/alex means the directory and the contents will be copied. Specifically, assume /home/alex contained files name f-one and f-two. /home/alex would result in /media/alex/f-one and /media/alex/f-two at the destination; /home/alex/ would result in /media/f-one and /media/f-two. To omit a directory, '--exclude Videos' or '--exclude Videos/' will work, but '--exclude /Videos' or '--exclude /Videos/' will not (the leading / is the problem).

---

### Post by AlexOnVinyl on 2012-04-24
> **agillator said:**
> I must have been asleep - not 'except', but 'exclude'. I am terribly sorry about that, I try to be so careful. However, '--exclude Videos' is correct, no equal sign.  The key on whether or not the directory itself is copied or just the contents is the slash at the end of the source: /home/alex/ means the contents of the directory will be copied, /home/alex means the directory and the contents will be copied. Specifically, assume /home/alex contained files name f-one and f-two. /home/alex would result in /media/alex/f-one and /media/alex/f-two at the destination; /home/alex/ would result in /media/f-one and /media/f-two. To omit a directory, '--exclude Videos' or '--exclude Videos/' will work, but '--exclude /Videos' or '--exclude /Videos/' will not (the leading / is the problem).

Alright Alligator :),

Here comes today bonus challenge - how would I exclude TWO directories? or multiple directories?

---

### Post by agillator on 2012-04-24
Two excludes: '--exclude Videos --exclude Audios' for example.

---

### Post by AlexOnVinyl on 2012-04-24
> **agillator said:**
> two excludes: '--exclude videos --exclude audios' for example.

friggin score!!!!! :d yes!!!! Thank you alligator!

:ks

---

### Post by AlexOnVinyl on 2012-04-24
> **agillator said:**
> Two excludes: '--exclude Videos --exclude Audios' for example.

I've got one last issue going on:

I'm receiving this message from time to time on certain parts of the copy:

> rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)

Here's the whole command I used: ```
rsync --progress -rEog --exclude Videos/ --exclude converted_music/ --exclude VirtualBox\ VMs/ --exclude virtual-drives/ --exclude Backup_of_boot_sectors/ --exclude examples.desktop --exclude Music/ --exclude .ecryptfs --exclude .VirtualBox/ --exclude .thumbnails/ --exclude .thunderbird/ --exclude .vidalia/ --exclude .teamviewer/ --exclude Templates/ --exclude sources.list --exclude wary-5.3.iso --exclude Public/ --exclude .cache/ /home/alex/ /media/backup/12.04-Precise-backup_4.23.2012/

```

It gets stuck copying over my Windows ISO - The destination drive is formatted in EXT4 so I have no clue what its giving me negativity.

but this is what it says:
> Downloads/Windows.7.Ultimate.32-64Bit.(2011-02-09).iso
  3809312768  83%   21.03MB/s    0:00:35  
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: connection unexpectedly closed (70735 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(605) [sender=3.0.9]


Any ideas?

---

### Post by papibe on 2012-04-24
Is the destination a local HD, a USB HD,  or network share mounted?
Regards.


BTW, you have so many excludes that I would do this:
```
rsync --progress -rEog --exclude-from='excludes.txt /home/alex/ /media/backup/12.04-Precise-backup_4.23.2012/
```
and then in excludes.txt I would put all rules:
```
- Videos/
- converted_music/
- VirtualBox VMs/
- virtual-drives/
- Backup_of_boot_sectors/
- examples.desktop
- Music/
- .ecryptfs
- .VirtualBox/
- .thumbnails/
- .thunderbird/
- .vidalia/
- .teamviewer/
- Templates/
- sources.list
- wary-5.3.iso
- Public/
- .cache/
+ *
```

---

### Post by AlexOnVinyl on 2012-04-25
> **papibe said:**
> Is the destination a local HD, a USB HD,  or network share mounted?
Regards.


BTW, you have so many excludes that I would do this:
```
rsync --progress -rEog --exclude-from='excludes.txt /home/alex/ /media/backup/12.04-Precise-backup_4.23.2012/
```
and then in excludes.txt I would put all rules:
```
- Videos/
- converted_music/
- VirtualBox VMs/
- virtual-drives/
- Backup_of_boot_sectors/
- examples.desktop
- Music/
- .ecryptfs
- .VirtualBox/
- .thumbnails/
- .thunderbird/
- .vidalia/
- .teamviewer/
- Templates/
- sources.list
- wary-5.3.iso
- Public/
- .cache/
+ *
```

how would I set it up to exclude folders that begin in "."?
and Im copying it to an external

---

### Post by papibe on 2012-04-25
> **AlexOnVinyl said:**
> how would I set it up to exclude folders that begin in "."?
For excluding all files and directories starting with a dot:
```
- .*
+ *
```
For just the folders:
```
- .*/
+ *
```

> **AlexOnVinyl said:**
> Im copying it to an external

USB external hardrive?

I look around for that error, but I didn't find an specific reason for it. However, several hints about timeouts were suggested.

I've seen that even when there is enough space, but the filesystem is tight for it, rsync may significantly slow down when transferring big files.

Taking that into consideration I've separated my home's backup rsync command to deal with big files. For example, for VirtualBox's vdi files I use the --inplace option.

Just some thoughts.
Regards.

---

