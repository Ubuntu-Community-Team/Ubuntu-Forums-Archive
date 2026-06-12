---
title: "periodic harddrive activity ... why?"
date: 2009-11-24
forum: General Help
---

### Post by MichaelBurns on 2009-11-24
I periodically (about once per minute) hear what sounds like harddrive activity (a grinding noise coming from the tower).  By the time I look for the light, it stops, so I don't know, but I'm relatively sure that it is the harddrive activity.  This is happening when I am simply reading something (usually a webpage).  What's the deal?  Why does this happen?  How can I stop it?  I don't like my computer to do things without my permission (thus the migration from MS Windows).

---

### Post by fluffman86 on 2009-11-24
It could be anything.  Firefox keeps a cache of the webpages you have open, and stores them every so often.  That way, if firefox crashes, you can easily recover the web pages you were viewing.

Ext3 and Ext4 filesystems also keep a journal of what they do.  So if Firefox writes a cache file, your kernel and filesystem is going to log that.  If your computer suddenly loses power right as firefox was writing the cache file, then when you reboot your kernel will know what was going on, know that it wasn't that important, and keep going.

---

### Post by harfa on 2009-11-24
most likely a program on your system is reading or writing to your hard drive. programs tend to do that. it could be any number of the programs you have given permission to run on your system, and I would suggest they probably need to do it in order to function. With some time and effort you can probably track down the cause(es) although it would be mostly pointless.

Good luck on your quest to suppress any program that dares to make use of your system resources without checking with you first every time....

---

### Post by Darael on 2009-11-24
It's possible that your computer is moving things that aren't being actively used from RAM to swap, for performance optimisation.  To see if it is, and change it should it be, take a look at [This help article section]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?").  Changing your swappiness down a little may increase performance anyway, so it's well worth a look.

---

### Post by fluffman86 on 2009-11-24
> **harfa said:**
> Good luck on your quest to suppress any program that dares to make use of your system resources without checking with you first every time....

Hahaha...that's the reason I *DON'T* use vista.  Windows is trying to run updates on itself? Should I Cancel myself or Allow myself to do that?  :lolflag::rolleyes:

---

### Post by sadi2009 on 2009-11-24
> **harfa said:**
> most likely a program on your system is reading or writing to your hard drive. Programs tend to do that. It could be any number of the programs you have given permission to run on your system, and i would suggest they probably need to do it in order to function. With some time and effort you can probably track down the cause(es) although it would be mostly pointless.

Good luck on your quest to suppress any program that dares to make use of your system resources without checking with you first every time....

lol... :d:d:d

---

### Post by Giblet5 on 2009-11-24
Possible causes:

Web site caching.

"updatedb" (keeps a cache of filenames for locate command)

Unwritten data writing.

Lookahead buffering.

Or thousands of other possibilities.

You have a few dozen tools for monitoring everything your system does, and there are a few thousand more available to install.

If this is really bugging you, and it sounds like it is, install 'blktrace' and 'iotop'. These will help you track down every buffer-write if you're OCD enough to bother.

And no, Windows won't help you with this. It's a multitasking OS too (kinda). What you want is MS-DOS or CP/M: one thing at a time and you get to govern what that one thing is.

---

### Post by MichaelBurns on 2009-11-24
Update:
The harddrive busy light does indeed come on.

Re swappiness (I love the name of that parameter):
I'm wondering if I can afford to reduce it, or I should just leave it alone.  The machine has 384 MB of RAM, and it will stay that way.  (Part of my sales pitch to get my mom to use xubuntu was that she didn't need to buy a new computer, or anything.)  It's running pretty smoothly right now, and not too sluggishly even compared to my (relatively) modern laptop.  It is an *occasional* annoyance when firefox won't respond for a few seconds, but other than that it runs fine.  (I do wish that it would show the time-out cursor, though, instead of just making me think that it is frozen.)

Re the MS Windows comments:
I hope that there was not a misunderstanding.  I no longer use MS Windows, and I dread the thought of ever again needing to do so for any reason.

I will look at those specific suggestions that y'all gave for tweaking and monitoring.  Thanks.

---

### Post by MichaelBurns on 2009-11-24
> **harfa said:**
> Good luck on your quest to suppress any program that dares to make use of your system resources without checking with you first every time....Damn right.

---

