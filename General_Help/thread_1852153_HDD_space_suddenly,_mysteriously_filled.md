---
title: "HDD space suddenly, mysteriously filled"
date: 2011-09-29
forum: General Help
---

### Post by ronwell on 2011-09-29
so I just rebooted my computer and suddenly I have less than 10 MB storage space left.  I'm totally flummoxed because before rebooting, I had a couple gigs free.  Is there a way to tell what most recently was added to my HDD?

I'm not sure if this is related--I suppose it probably is, but I can't imagine how-- the reason I rebooted in the first place was because my cat walked across my keyboard and somehow activated a fullscreen command-line interface (something I didn't know was possible) that I was able to log in to, but couldn't seem to deactivate or quit out of. It was really weird, I have no idea what keys the cat pressed... could this somehow have filled up my hard drive?

I'm so confused... any help would be greatly appreciated.

---

### Post by Ceiber Boy on 2011-09-29
> **ronwell said:**
> so I just rebooted my computer and suddenly I have less than 10 MB storage space left.  I'm totally flummoxed because before rebooting, I had a couple gigs free.  Is there a way to tell what most recently was added to my HDD?

I'm not sure if this is related--I suppose it probably is, but I can't imagine how-- the reason I rebooted in the first place was because my cat walked across my keyboard and somehow activated a fullscreen command-line interface (something I didn't know was possible) that I was able to log in to, but couldn't seem to deactivate or quit out of. It was really weird, I have no idea what keys the cat pressed... could this somehow have filled up my hard drive?

I'm so confused... any help would be greatly appreciated.
Ctrl+Alt+F1 takes you to a "fullscreen command-line interface". Ctrl+Alt+F7 takes you back to your GUI. you can try it without risk as you now know how to get back to your GUI!

Sorry i don't have any ideas for your HDD suddenly filling up.

---

### Post by carranty on 2011-09-29
Unfortunately I don't know of any way of finding the most recently created files on the entire HDD.  Too fill up 2GB that fast I suspect you have copied a rather large directory without realising it (easy to do from the command line), to check the terminal history you could open up a terminal and type

[I]history | grep cp

[/I]this will then print a list of all your recent copy commands.  Its also worth checking your recent history for other possibilities.  To do this just type

[I]history

[/I]on its own. Sorry I can't be of more help

---

### Post by boxafrogs on 2011-09-29
I've experienced a similar problem. I've just installed Ubuntu on a brand new computer and somehow have lost 70GB from my 500GB hard drive. As I'm unfamiliar with this os I'm not even sure how to find out what it is thats caused it. :confused:
Any clues anyone?

---

### Post by carranty on 2011-09-29
Boxafrogs, is Ubuntu the only operating system on your computer, or are you dual booting?

---

### Post by boxafrogs on 2011-10-03
I chose the option to overwrite win7 when I installed ubuntu so it should be just 1 right?
thanks

---

### Post by Automatiic on 2011-10-03
@OP
Run some HDD diagnostics on your machine. If your HDD is going bad and some sectors become unreadable, disk manager might think they are filled which would explain a sudden loss in space on the drive. Free sectors could be going bad while the sectors that actually have data written on them may be fine which would explain why you haven't noticed any issues... yet.

---

### Post by [S|G] on 2011-10-03
Hi there!

I got a bit confused as to who is having problems on this topic :) Anyway, the best way to see what is taking so much room on your disk is to open a terminal and type in this command:

$ sudo df -h --max-depth=1 /

This should tell you how much space each directory is taking on your disk. Alternatively you launch the disk usage analyzer by going to "applications -> accessories -> disk usage analyzer". 

It would also help to know a bit more from your system. You can see the mounted partitions and their usage/free space by using this command:

$ df -h

If you've done *nothing* and disk space starts to disappear, you might want to monitor your logs, as if there's something wrong there might be a lot of messages being recorded in the /var/log directory and eating up your free space.

---

### Post by boxafrogs on 2011-10-05
Thanks guys,
i ran the smart data self test and the short test says there are no bad sectors and the disk is healthy. I know you don't get 500gb available on a 500gb disk, but is 10% a standard loss? It seems a little high to me.
Cheers
:)

---

### Post by philinux on 2011-10-05
> **ronwell said:**
> so I just rebooted my computer and suddenly I have less than 10 MB storage space left.  I'm totally flummoxed because before rebooting, I had a couple gigs free.  Is there a way to tell what most recently was added to my HDD?

I'm not sure if this is related--I suppose it probably is, but I can't imagine how-- the reason I rebooted in the first place was because my cat walked across my keyboard and somehow activated a fullscreen command-line interface (something I didn't know was possible) that I was able to log in to, but couldn't seem to deactivate or quit out of. It was really weird, I have no idea what keys the cat pressed... could this somehow have filled up my hard drive?

I'm so confused... any help would be greatly appreciated.

For others reading this here's some good advice.
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by SeijiSensei on 2011-10-05
> **boxafrogs said:**
> Thanks guys,
i ran the smart data self test and the short test says there are no bad sectors and the disk is healthy. I know you don't get 500gb available on a 500gb disk, but is 10% a standard loss? It seems a little high to me.
Cheers
:)

By default, the ext2/3/4 file systems set aside five percent of the filesystem for various system processes.  When drives were 1 or 20 GB in size, 5% made sense, but with today's enormous drives, it's overkill.  On a 500 GB drive, 1%, or 5 GB, should be plenty.  You can use the tune2fs command to change the reserved percentage, but I suspect you want to do this on an unmounted filesystem.  Boot from the Ubuntu CD and choose "try" rather than "install."  Then you can open a terminal and run the tune2fs command on the unmounted hard drive file system.  See "[man tune2fs]("http://manpages.ubuntu.com/manpages/maverick/man8/tune2fs.8.html")" for details, in particular the -m parameter.

---

