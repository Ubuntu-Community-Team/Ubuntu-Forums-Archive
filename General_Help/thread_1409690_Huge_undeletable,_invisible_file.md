---
title: "Huge undeletable, invisible file"
date: 2010-02-17
forum: General Help
---

### Post by Stan15 on 2010-02-17
Earlier I noticed I was missing almost all the space on my hard drive. I tracked it down too one huge file in my home folder weighing in at 100 some gigs. I can't remember what the name was but it started with at least five "O"s. Without thinking about it I deleted it. Sent to trash, emptied trash. 
After I deleted it I noticed it had not emptied the space and my drive is still almost full. I searched for it to make sure it was gone and it was. I restarted the computer to no avail. I tried clearing /tmp too but it's still not helping. Here's the shortened output of df -h 
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             141G  131G  3.1G  98% /

```

But, if I go into Nautilus and check the properties of / it tells me I'm using about 14 gigs, which sounds about right. I'd be very thankful someone can atleast point me in the right direction cause I can't find much online.

P.S. 
I'm hoping this is all the information anyone needs, but for the sake of brevity I shortened the way I deleted it. For completeness it involved multiple users and two Xsessions, but I don't think that's the root of the issue

---

### Post by Iowan on 2010-02-17
Guess you'd have to consider this as just a nudge - since I can't provide specifics. 
It's possible to "overlay" files/directories/etc. If you have a directory */home/me/files/hidden* containing gigs of files, then mount another directory to */home/me/files*, the "hidden" directory becomes inaccessible, but is still there. if the second directory is unmounted, "hidden" becomes accessible again. 
I doubt this is your problem - and I may be off-base...
 or...

---

### Post by mikewhatever on 2010-02-17
Try running **sudo du -hs /*** and post the output, which should show the sizes of your root directories. Note, it may take sometime to complete.

---

### Post by jamesisin on 2010-02-17
Are you by chance using any links across drives or shares?

Sometimes these links are counted in size measures though they are not counted as drive space.  (I don't know if that makes sense, but it's based on something true.)

Check out the Disk Usage Analyzer:

Applications &#8212;> Accessories &#8212;> Disk Usage Analyzer

I find the Treemap Chart easier to navigate, but the Rings Chart is cooler to see.  It should help you locate anything odd and large.

---

### Post by Stan15 on 2010-02-17
Here you go
```

5.4M    /bin
57M     /boot
0       /cdrom
452K    /dev
16M     /etc
du: cannot access `/home/notme/.gvfs': Permission denied
11G     /home
0       /initrd.img
0       /initrd.img.old
363M    /lib
16K     /lost+found
20K     /media
8.0K    /mnt
4.0K    /opt
du: cannot access `/proc/1218/task/1463/fd/45': No such file or directory
du: cannot access `/proc/2309/task/2309/fd/4': No such file or directory
du: cannot access `/proc/2309/task/2309/fdinfo/4': No such file or directory
du: cannot access `/proc/2309/fd/4': No such file or directory
du: cannot access `/proc/2309/fdinfo/4': No such file or directory
0       /proc
117G    /root
7.9M    /sbin
4.0K    /selinux
4.0K    /srv
0       /sys
212K    /tmp
2.8G    /usr
571M    /var
0       /vmlinuz
0       /vmlinuz.old

```

---

### Post by juan.villa on 2010-02-17
The bulk of your usage is in the root directory, what's in that folder that you can't delete?

---

### Post by Stan15 on 2010-02-17
> **jamesisin said:**
> Are you by chance using any links across drives or shares?

Sometimes these links are counted in size measures though they are not counted as drive space.  (I don't know if that makes sense, but it's based on something true.)

Check out the Disk Usage Analyzer:

Applications —> Accessories —> Disk Usage Analyzer

I find the Treemap Chart easier to navigate, but the Rings Chart is cooler to see.  It should help you locate anything odd and large.

I'm only using the one drive. Disk usage analyser says about the same as df "130.6 gigs used."

---

### Post by mikewhatever on 2010-02-17
117G    /root   ~~ very exiting.
What's the output of **sudo ls -l /root** ?

---

### Post by Stan15 on 2010-02-17
> **mikewhatever said:**
> 117G    /root   ~~ very exiting.
What's the output of **sudo ls -l /root** ?

That would be.total  
```
 total 4
drwxr-xr-x 2 root root 4096 2009-12-13 20:33 Desktop

```
And according to Nautilus properties the contents are "1 item, with size 4.0 kb"

---

### Post by flippo on 2010-02-17
Try sudo ls -al /root.  That will show hidden files.

---

### Post by jamesisin on 2010-02-17
Applications &#8212;> Accessories &#8212;> Disk Usage Analyzer

It's how I discovered this was happening (though not how to fix it):

[http://ubuntuforums.org/showthread.php?t=1409050](http://ubuntuforums.org/showthread.php?t=1409050)

---

### Post by mikewhatever on 2010-02-17
How about **sudo du -h /root** .


> **jamesisin said:**
> Applications &#8212;> Accessories &#8212;> Disk Usage Analyzer

It's how I discovered this was happening (though not how to fix it):

[http://ubuntuforums.org/showthread.php?t=1409050](http://ubuntuforums.org/showthread.php?t=1409050)

Try experimenting with --exclude=Pattern.

---

### Post by falconindy on 2010-02-17
> **Stan15 said:**
> That would be.total  
```
 total 4
drwxr-xr-x 2 root root 4096 2009-12-13 20:33 Desktop

```
And according to Nautilus properties the contents are "1 item, with size 4.0 kb"

...and what's in /root/Desktop?

---

### Post by Stan15 on 2010-02-17
> **flippo said:**
> Try sudo ls -al /root.  That will show hidden files.

Excellent! That's why I couldn't find it with df or du, now I feel stupid. I found the file at /root/.local/share/Trash/files/oooooooo.ooo  So I'm guessing what happend was that I deleted the file as root then emptied my trash not as root. Thus not actually getting rid of it just moving it around.

By the way for the curious the file is a 116.3 gig plain text file. Which raises further questions...

---

### Post by Stan15 on 2010-02-17
Thanks everyone so much for helping me out. I cant believe Nautilus won't measure the size of hidden files though. That's why it was saying one thing and df and Disk analyser were saying something else.

Hah, further poking around revealed the file was a result of sfill. Guess it didn't exit properly or something cause I've never had that problem before.

---

### Post by dcstar on 2010-02-18
> **Stan15 said:**
> Thanks everyone so much for helping me out. I cant believe Nautilus won't measure the size of hidden files though. That's why it was saying one thing and df and Disk analyser were saying something else.

Hah, further poking around revealed the file was a result of sfill. Guess it didn't exit properly or something cause I've never had that problem before.

Ahh yes sfill, another utility based on the now ancient Gutmann paper that the author himself said no longer applies to modern disk drives - about 2 decades ago!

Once a myth gets some traction, people just refuse to believe it isn't really valid any more.

---

### Post by sgosnell on 2010-02-18
When you move a file to trash, Nautilus no longer lists it, because it's in the trash.  You have to remember to empty your trash now and then.  I usually delete files using Shift-delete, which actually deletes them, bypassing trash.  When I delete a file, I usually want it gone.

---

### Post by jamesisin on 2010-02-18
I didn't think root had a trash so I'm a little confused as to why this was in root's trash (which obviously emptying your trash couldn't effect).

---

### Post by El Zoido on 2010-02-18
Root does indeed seem to have a trash, I had it happen a couple of times that I deleted some file as root and they went in root's trash which in turn could only be emptied as root.

---

