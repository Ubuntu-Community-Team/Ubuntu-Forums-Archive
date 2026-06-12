---
title: "Losing drive space at the rate of 300Mb's an hour!"
date: 2011-02-06
forum: General Help
---

### Post by spaceboy909 on 2011-02-06
** I have **NO** file download activity...no bit torrent, no web downloads...nothing that I can see.

For the last half day or so, I've been constantly losing space (/home part.), and getting low space warnings from Ubuntu.  At first, I just deleted some old files because I have a lot of files and I just assumed that it was an older warning that I ignored previously.

But the shrinking continued.

I have compared directory / partition size data between 'disk usage analyzer', gparted, and Nautilus.  Gparted and Nautilus show a constant change in available free/used space for my /home.  'Disk usage analyzer' does not show any change for any of the largest directories where the changes would have to occur.

It's drained me completely at least once, and possibly once the other day amidst some downloading so I wouldn't have suspected anything at that point.

Any ideas what this might be and how to correct it?  I saw one thread talking about a CUPS bug leaving massive tmp files behind, but I don't print from this box, and I think I have CUPS switched off; I also checked file sizes in the CUPS dir. and there's nothing large in there.

---

### Post by rpaskudniak on 2011-02-06
Spaceboy,

First, try this command on the file system that is shrinking
```
du /home 2>/dev/null| sort +0 -1 -nr | head -20
```
If there is a file growing, something should show up near the top of the output.

Have you tried rebooting your box?  I didn't notice you mentioning that in your post.  I will give you the benefit of my similar experience.

In my case, while back, I saw a process writing a godzlillion messages per second to a flat file, eating up disk space quickly.  I was unable to kill the process (no root access) but I tried deleting the rapidly growing file.  But disk space continued to shrink at the same rate.  What was wrong?

Well, all my rm succeeded at was to delete the name link to the inode for the file.  Since the inode was already open to that process, it merrily continued to write to that blessed file. I finally reached an SA who killed the process but the space did not get released upon the close.  (I'd call that a bug in the file system but that's another issue.)  I knew the name of the file I had deleted but I don't know if the SA was able to use that information.  There was, however, a way for the SA to locate the largest files by inode number (some variation of the du command?), and release the disk space referenced by that inode.

So now, if this is indeed your problem, we need to discover a way to expose such anomalous files.  That's why I suggested the reboot; fsck should clean this up as a matter of course at that time.

As for the esoterica I mentioned above - the location of link-less inodes - I would like to see someone post the right option for that one as well.

Good luck.

---

### Post by fabricator4 on 2011-02-06
Have a look at what processes seem to be producing unexpected activity. Install and run Gkrellm so that you can see when disk activity is occurring.  You might need to look at both of these together to see what's going on.

It does sound like some sort of out of control tmp file behaviour.  Try to think of any applications you may have installed before this behaviour began.  As a last resort make a new Desktop user login and use that for a day or two to see if the behaviour follows you.  If it doesn't then it's something in the config or startup of your main login.

Chris

---

### Post by spaceboy909 on 2011-02-24
Just wanted to say thanks for the help on this.  :)  I did a touch forcefsck and rebooted and that did seem to stop the bleeding.  I don't think it recovered the space though, so when I have some time I'll dig in and see if I can't find and purge it.

---

### Post by jgratero on 2011-02-25
Same thing here, only that the rate is about 100mb per hour/half hour (aprox.)... Did the touch forcefsck, didn't work... The HD keeps losing space...

---

