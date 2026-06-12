---
title: "My hard drive is full BUT it's not ! .log files are the problem!"
date: 2011-01-06
forum: General Help
---

### Post by Nitrozzy7 on 2011-01-06
Hello there folks,
According to Disk Usage Analyzer (/var/log) there are some .log files that are 9.9GB in size that I cannot delete.
Recently I created a new user which I think is the cause. Two users in total.
My HHD is 120GB in size but DUA says it's 107.2GB in total. As far as I can remember the actual size is just under 120GB. So where are my Gigs?! And what's the deal with those 9.9GB .log files that fill almost the entire disk but I cannot delete?!
:confused:
What's causing all this behavior anyway?

---

### Post by MaxIBoy on 2011-01-06
Any files outside your home folder need administrator (what Linux users call "root") permissions. To delete the files, you must run the remove ("rm") command with sudo. 

Open a terminal (applications->accessories->terminal) and run the following command to clear out /var/log:
```
sudo rm /var/log/*.log
```
That will delete any file whose name ends with .log. You will be asked for a password, and it is normal if nothing shows up when you type it; just type it anyway.

For more information about sudo, see here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Be very careful when running any command with sudo, you might break your system!


As far as your missing drive space goes: If you have a swap partition, that can reduce the available space. Most filesystems also reserve some extra space (I think about 5%.) 

Finally, the hard drive's manufacturer may have lied about how much space you have. Unfortunately they think one gigabyte is 1000*1000*1000 bytes, or sometimes 1000*1000*1024, when it is really 1024*1024*1024 bytes. This confusion allows them to advertise that their hard drives are bigger than they actually are.

---

### Post by akand074 on 2011-01-06
If you prefer, you can also type this in a Terminal:

```
gksudo nautilus
```

This will open a file browser with root (administrative) privileges. From then you can just browse to /var/log or anywhere else that needs administrative privileges and delete files (make sure not to remove anything important).

---

### Post by coffeecat on 2011-01-06
> **MaxIBoy said:**
> Finally, the hard drive's manufacturer may have  lied about how much space you have. Unfortunately they think one  gigabyte is 1000*1000*1000 bytes, or sometimes 1000*1000*1024, when it  is really 1024*1024*1024 bytes. This confusion allows them to advertise  that their hard drives are bigger than they actually are.

1000*1000*1000 bytes do make 1 gigabyte because ['giga' is an SI prefix]("http://en.wikipedia.org/wiki/Giga-")

> **Giga** is a unit prefix in the metric system indicating multiplication of a unit by 10[FONT=Times New Roman, serif]^[/FONT]9 or 1000000000. It has the symbol **G**.1024*1024*1024 bytes make 1 **gibi**byte. See:

[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)

The inapproriate use of gigabyte when gibibyte is meant may be a  tradition in computing circles, but it is confusing. The SI/metric  system has its roots in the 18th century and is universally used in  other sciences. Its prefixes should take precedence. 

The manufacturers of hard discs may indeed be motivated by hoping to  make things seem larger than they are, but they are not lying. Their use  of the terminology is correct.

---

### Post by Nitrozzy7 on 2011-01-07
I tried "gksudo nautilus" but still I only managed to salvage about 45Gb. What caused this, anyway?

---

### Post by QLee on 2011-01-07
[QUOTE=Nitrozzy7]...but still I only managed to salvage about 45Gb. What caused this, anyway?[/QUOTE]

From the information you have given us so far, something was creating some huge log files is the cause.

Since you didn't even mention what were the names of the huge files, it isn't easy to guess what might have been happening.

Sometimes a program will log errors of some kind and often the log entries suggest what might have gone wrong. If logs start to stream entries rapidly and become huge it probably means something was corrupted or mis-installed/configured or something else was wrong with the system which caused some conflict. 

Still, you must have a lot of files or large ones in your filesystem.

---

### Post by Nitrozzy7 on 2011-01-07
> **QLee said:**
> ...Still, you must have a lot of files or large ones in your filesystem.

Nope. I'm currently using about 25Gb. That includes everything from music and pictures to videos and applications.
Are .log files necessary to the system?
Btw, as far as I can recall there where four names on the .log files. One was ".messages.log" the other was starting with k but it wasn't kernel and the last two I can't recall. For each file there was another one with the number one printed on it (eg. ".messages.1.log").
Is there a way to ensure that I won't see those .log files again?

---

### Post by hakermania on 2011-01-07
Hey, why don't you give in a terminal
```
baobab
``` to see what's eating your space anyway?

---

### Post by drs305 on 2011-01-07
> **Nitrozzy7 said:**
> I tried "gksudo nautilus" but still I only managed to salvage about 45Gb. What caused this, anyway?

When you used nautilus as root, when you deleted the files in /root/.local/share/Trash did you use SHIFT-DEL? Just hitting DEL will move them.... to the trash bin! SHIFT-DEL permanently removes them and releases the space they occupied.

You might find this guide useful:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by efflandt on 2011-01-08
If you have log files growing very large, looking at those log files may give you a clue what the problem is.  The system uses a cron job to automatically rotate most log files to compress them as the whatever.2.gz, etc. versions, then deletes the older ones eventually.  But if you install something that log rotation does not know about, they could grow larger.  See **/etc/logrotate.conf** and **/etc/logrotate.d/** dir.

But how do you have your drive partitioned.  If you have a separate partition for /var or /var/log (or / ), maybe it is not large enough and you need to rethink your partition sizes.

---

### Post by QLee on 2011-01-08
[QUOTE=Nitrozzy7]Nope. I'm currently using about 25Gb. That includes everything from music and pictures to videos and applications.[/QUOTE]

The system I'm writing this from is using 4G so "a lot" or "large" are relative terms, compared to mine you are using a lot. However, it seems from your statements that you have most of the space back that was filled and caused your system to not work.

[QUOTE=Nitrozzy7]Are .log files necessary to the system?[/QUOTE]

Strictly speaking I suppose not. However, if you look at them before you delete them then they can sometimes be helpful identifying a problem.

...

[QUOTE=Nitrozzy7]Is there a way to ensure that I won't see those .log files again?[/QUOTE]

Not if the same conditions occur that caused them to fill up, if it happens again, they would fill up again.

---

### Post by psusi on 2011-01-08
> **coffeecat said:**
> 1000*1000*1000 bytes do make 1 gigabyte because ['giga' is an SI prefix]("http://en.wikipedia.org/wiki/Giga-")

1024*1024*1024 bytes make 1 **gibi**byte. See:

[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)

The inapproriate use of gigabyte when gibibyte is meant may be a  tradition in computing circles, but it is confusing. The SI/metric  system has its roots in the 18th century and is universally used in  other sciences. Its prefixes should take precedence. 

The manufacturers of hard discs may indeed be motivated by hoping to  make things seem larger than they are, but they are not lying. Their use  of the terminology is correct.

Words have different meanings depending on their context.  In the context of bytes, the SI prefixes are rounded to the nearest power of 2: 1024.  The only #^@^holes who stubbornly refuse to follow that convention are hard disk makers.  You remember 1.44 MB floppy disks?  They held exactly 1440 * 1024 bytes, not 1000.

Now those same #%@#$%holes are making up this kibi/mibi/gibi crap so they can claim that they aren't liars.

---

### Post by Nitrozzy7 on 2011-01-10
I rebooted the PC and now I have all my space back. I guess when I deleted those .log (Shift delete) files the system needed a reboot in order to give me the true size of my free space.
Thnx for the feedback. Cheers!

---

### Post by Nitrozzy7 on 2011-01-10
I rebooted the PC and now I have all my space back. I guess when I deleted those .log (Shift delete) files the system needed a reboot in order to give me the true size of my free space.
Thnx for the feedback. Cheers!

---

