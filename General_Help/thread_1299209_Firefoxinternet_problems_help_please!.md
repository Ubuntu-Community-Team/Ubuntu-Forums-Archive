---
title: "Firefox/internet problems: help please!"
date: 2009-10-23
forum: General Help
---

### Post by Bluebirdnick on 2009-10-23
Hello all,

I'm quite new to Ubuntu, so please excuse my ignorance.

When I turned on my computer today, it did not automatically connect to the internet as normal.  Also, Firefox has stopped working.  The "back" button no longer works, and buttons appearing on websites (e.g. "login" on websites) no longer work.  (I'm posting this via Vista).

The only other glitch I've had was last night when I was downloading something and was told that my disc was full (I've checked - it is no more than 30% full).

What can I do to fix this?  I have loved using Ubuntu over the last few months, and I don't want to have to go back to Microsoft!

Thanks

Nick

---

### Post by jbrown96 on 2009-10-23
What type of connection are you using (wired, wireless, ppoe, isdn)? Have you tried playing around with the network icon in the top right? If you are using a connection that requires a password (wireless), network-manager can "forget" a password; you may need to reconfigure the connection.

If you are still having problems, post the output from the following commands. Enter them in a terminal (apps-->accessories-->terminal)
```
sudo lshw -c network
``` ```
ifconfig
``` ```
lsmod
``` and if using wireless ```
iwconfig
```

---

### Post by kanikilu on 2009-10-23
This is just a stab in the dark, but I wonder if maybe your Firefox profile somehow got it's permissions or ownership changed?

Can you post the output of the following from a terminal:

```
whoami
```
Not really necessary, but does help verify the permissions in the next step.
```
ls -la ~/.mozilla/firefox/
```
```
df -h
```
You said you have plenty of free disk space, but it doesn't hurt to check...

// Edit, I overlooked part of your post and realized the problem may not be specific to FF, so I'm probably off-base here...

---

### Post by Giblet5 on 2009-10-23
The "disk full" error is not a mistake.

It doesn't matter that you appear to have 100MB free and the file looks like it's 1MB. That can be a lie. The file can easily be infinitely large (Sony does this regularly with music files).

If you're downloading a file that is larger than your free space, you will get that error, the download will stop, and the partial file will be removed, freeing up the space it used.

Running out of disk space is really bad on an operating system that tends to buffer disk writes in memory... There is a possibility that the filesystem has been damaged (corrupted) by this oversight.

The best thing to do is to restart your computer and boot into Recovery Mode, check the disk drive with fsck allowing it to fix any/all errors, then try again.

```
fsck -an /dev/sdXX
``` where XX is the device of your / filesystem (eg, /dev/sda1).

---

