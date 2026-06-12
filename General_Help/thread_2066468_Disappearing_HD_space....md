---
title: "Disappearing HD space...?"
date: 2012-10-04
forum: General Help
---

### Post by mons00n on 2012-10-04
Hi everyone,

I'm running a file/web server using Ubuntu 12.04 64bit.  This issue doesn't seem like it has anything to do with the server portion of my server so I'm posting it here.

The quick and dirty is this: I run the OS off of a 60GB SSD, I run the command
```
/sbin/fstrim -v /
```
daily via sudo's crontab.  Now it seems random, but occasionally all of my HD space will disappear and I can't seem to find out where it went.  This then causes my server functions to stop working because there is no room for the server to write logs; ssh continues to work, but VNC does not.  Here's what a 'df -h' looks like when this happens:
[[IMG]http://i.imgur.com/1phltl.jpg[/IMG]](http://imgur.com/1phlt)
notice my first HDD (/dev/sdd1) is completely full.

I run the command 'sudo du -h --max-depth=1' at '/' to see if I can get an idea where the space is being eaten up and it produces this:
[[IMG]http://i.imgur.com/42eWfl.jpg[/IMG]](http://imgur.com/42eWf)
which shows a total of ~44GB taken (the 2.4TB is a raid volume on separate disks)....so what is taking up all of this room?

If I reboot the computer, everything goes back to normal and 'df -h' looks like so:
[[IMG]http://i.imgur.com/Y8Uydl.jpg[/IMG]](http://imgur.com/Y8Uyd)

This only happens once every few weeks, and I can't pinpoint what causes it.  Any ideas on what is going on here?  Thanks so much for taking the time to read this.

---

### Post by Stonecold1995 on 2012-10-04
You can use Baobab to see what directories are taking up the most space.

```
sudo apt-get install baobab
```

[[img]http://www.pictureshack.us/thumbs/83096_baobab.png[/img]](http://www.pictureshack.us/images/83096_baobab.png)

---

### Post by mons00n on 2012-10-04
> **Stonecold1995 said:**
> You can use Baobab to see what directories are taking up the most space.


I've used baobab and gksudo baobab - both return the same results as du

---

### Post by Stonecold1995 on 2012-10-05
> **mons00n said:**
> I've used baobab and gksudo baobab - both return the same results as du

What I mean is, you can use Baobab to narrow down what files and directories are taking up the most space, instead of just getting the size of one folder at a time.

---

### Post by mons00n on 2012-10-05
> **Stonecold1995 said:**
> What I mean is, you can use Baobab to narrow down what files and directories are taking up the most space, instead of just getting the size of one folder at a time.

No I understand what you mean; my response meant that Baobab shows the same results as if I were using 'du -h', it all totals to ~44GB.  No idea where the suddenly appearing 16GB comes from...or where it goes when I reboot =(

---

### Post by Stonecold1995 on 2012-10-05
So the space gradually accumulates but vanishes when you reboot?  Maybe it's /tmp's fault.

```
sudo du -sh /tmp
```

---

### Post by mons00n on 2012-10-05
> **Stonecold1995 said:**
> So the space gradually accumulates but vanishes when you reboot?  Maybe it's /tmp's fault.

```
sudo du -sh /tmp
```

It's not gradual, it's sudden and seemingly random.  If you look at the second screenshot I posted /tmp is only 52K.

---

### Post by Wim Sturkenboom on 2012-10-05
It's more than likely files that are 'deleted' but still in use by an application. *du* will not see them but *df* will still report them.

I don't know what you're running on the server but for a lamp server I would check the following when it happens.

Restart apache; is the diskspace available after this? If yes, you have a pointer. If not, restart mysqld; is the diskspace available after this? If yes, you have a pointer. If not, check other processes.

*lsof* can be of help as well. e.g.

```

lsof |grep -i deleted

```
will find deleted files that are still in use by an application.


PS
seemingly random might imply a misconfigured logrotate where filesize is the deciding factor on rotating

---

### Post by mons00n on 2012-10-05
> **Wim Sturkenboom said:**
> It's more than likely files that are 'deleted' but still in use by an application. *du* will not see them but *df* will still report them.

I don't know what you're running on the server but for a lamp server I would check the following when it happens.

Restart apache; is the diskspace available after this? If yes, you have a pointer. If not, restart mysqld; is the diskspace available after this? If yes, you have a pointer. If not, check other processes.

*lsof* can be of help as well. e.g.

```

lsof |grep -i deleted

```
will find deleted files that are still in use by an application.

This sounds like a sound plan of attack.  Thanks for the lsof tip; I'll report back in a few weeks when it happens again! 

edit: yea I'm running a LAMP + Mumble server on this machine

---

