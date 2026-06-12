---
title: "Help copying files to external drives. (don't have permission)"
date: 2011-03-20
forum: General Help
---

### Post by seanbrannon on 2011-03-20
OK.  Before I started this thread I did a little searching for a similar thread and didn't find one.  I am having issues copying files from my desktop to external devices (iPod, external HDD etc.).  I have to log out of my account and log in as root in order to do so.  Is there a way to do this without having to log in as root?  Thanks for any help in advance.

---

### Post by tredegar on 2011-03-20
> Before I started this thread I did a little searching for a similar thread and didn't find one.
*Really*? Putting **copying files to external drives** into google.com[COLOR="Red"]/linux[/COLOR] gave me 2.9*million* hits.

Anyway, plug in the HDD, wait a few seconds then give us the output of the following commands
```
ls -l /media/
mount
```
And please tell us which version of ubuntu you are running.

Don't get me started on iPods.

---

### Post by seanbrannon on 2011-03-20
```
user@ubuntu:~$ ls -l /media/
total 72
drwxr-xr-x  2 root root  4096 2010-10-23 15:23 cdrom
drwxrwxr-x  2 root root  4096 2010-11-07 18:34 CreativeZenXtra
drwx------  1 user root   152 2011-03-20 09:01 MEDIA ONLY!
drwxrwxr-x  2 root root  4096 2010-11-07 18:46 MyZen
*lrwxrwxrwx  1 root root     4 2010-11-07 19:31 usb -> usb0*
drwxr-xr-x 56 root root 32768 1969-12-31 16:00 usb0
drwxr-xr-x  2 root root  4096 2010-11-07 19:31 usb1
drwxr-xr-x  2 root root  4096 2010-11-07 19:31 usb2
drwxr-xr-x  2 root root  4096 2010-11-07 19:31 usb3
drwxr-xr-x  2 root root  4096 2010-11-07 19:31 usb4
drwxr-xr-x  2 root root  4096 2010-11-07 19:31 usb5
drwxr-xr-x  2 root root  4096 2010-11-07 19:31 usb6
drwxr-xr-x  2 root root  4096 2010-11-07 19:31 usb7

```

I italicized what is currently plugged in.  I know how to access the drives and copy files *from* them.  But I can't copy files *to* them.  And I am running Ubuntu 10.10

---

### Post by tredegar on 2011-03-20
This looks very odd, with all those **usb*n*** entries, but you did not give us the output of the **mount** command.

Please try again, with the outputs of _both_ the commands afresh (because the situation may have changed).

It looks like you do not have write access to **CreativeZenXtra** either (was it plugged in at the time?)

Is your username really **user** ?

If not, please leave it as it is, and don't edit it before posting, as this causes confusion, especially when there are permissions issues to be fixed.

Disclosing your username really isn't a security issue.

Do you think there is anything possibly relevant that you might have forgotten to tell us, perhaps like you are running a "wubi install" or a "virtual machine", or your ubuntu installation is "in the cloud"? I am assuming that you are booting ubuntu 10.10 from your HDD. If this is not the case, please explain your exact situation further.

---

