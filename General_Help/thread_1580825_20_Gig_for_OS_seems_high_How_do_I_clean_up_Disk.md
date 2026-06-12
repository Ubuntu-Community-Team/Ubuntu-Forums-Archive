---
title: "20 Gig for OS seems high: How do I clean up Disk?"
date: 2010-09-23
forum: General Help
---

### Post by Nazaroo on 2010-09-23
How can I know what to delete to save disk space?
Is there an automated program that safely deletes things I don't need?

thanks in advance,
Nazaroo

---

### Post by CharlesA on 2010-09-23
I suppose 20GB is a bit high, but it all depends on what you have installed.

You could run this:

```
sudo apt-get autoclean
```

To remove old packages from the cache.

Try running this as well:

```
du / -h --max-depth=1
```

---

### Post by Nazaroo on 2010-09-23
hmmm ran first one and :

> root@unknown:~# sudo apt-get autoclean
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

```

I have Synaptic Manager open in another area. Could that be a problem?

---

### Post by libssd on 2010-09-23
Yes, you have a collision with Synaptic; close it, and try again.

Better yet, install Ubuntu Tweak, which provides a fairly intuitive GUI for this and other tasks.

---

### Post by Nazaroo on 2010-09-23
I was installing agedu, but it doesn't show up on the Ubuntu dropdown menu that I can see...

I am installing Tweak, which calls itself a Hex-editor.  Sounds like the "monitor" in an Apple IIe.  Haven't programmed in HEX since the 80s....

---

### Post by CharlesA on 2010-09-23
> **Nazaroo said:**
> hmmm ran first one and :

root@unknown:~# sudo apt-get autoclean
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

```

I have Synaptic Manager open in another area. Could that be a problem?
Yup. You can only have one program accessing dpkg at once.

Close out synaptic and run it again.

The du program will provide the same functionality as agedu.

Even Disk Usage Analyzer will provide the same functionality minus the html report.

---

### Post by Nazaroo on 2010-09-23
Okay I ran DU:

root@unknown:~# du / -h --max-depth=1
17M    /tmp
4.0K    /srv
31M    /boot
du: cannot access `/proc/16725/task/16725/fd/3': No such file or directory
du: cannot access `/proc/16725/task/16725/fdinfo/3': No such file or directory
du: cannot access `/proc/16725/fd/3': No such file or directory
du: cannot access `/proc/16725/fdinfo/3': No such file or directory
0    /proc
4.0K    /mnt
16K    /lost+found
0    /sys
5.7M    /bin
1.1M    /dev
63M    /opt
216M    /lib
16M    /etc
2.0G    /root
^C
root@unknown:~# ^C
root@unknown:~# 


I don't know what I am looking at here...


any advice?

---

### Post by Hobgoblin on 2010-09-23
> **Nazaroo said:**
> 
any advice?

Let the command finish (i.e. don't ctrl+C out of it).

The first column is the size, the second is the folder.  It is showing where the space is being used, or would if you let it finish.

The output of
```
df -h
```
might also be handy.

---

### Post by CharlesA on 2010-09-23
You'll get a few permission denied errors, but that's ok.

If you want a GUI version, check out Disk Usage Analyzer: Applications > Accessories > Disk Usage Analyzer.

---

### Post by Nazaroo on 2010-09-24
> **Hobgoblin said:**
> Let the command finish (i.e. don't ctrl+C out of it).

The first column is the size, the second is the folder.  It is showing where the space is being used, or would if you let it finish.

The output of
```
df -h
```might also be handy.

oh ok. I thought the program was hung.

thank you to everyone for your help.

This time I'm letting it run through longer.

P.S., could there be a bunch of source-code I don't need hanging around somewhere?
Or a game someone may have installed that never got uninstalled?
Where would I look for those? (no big games show up on dropdown menu...)

---

### Post by Nazaroo on 2010-09-24
Okay here is the final listing';

root@unknown:~# du / -h --max-depth=1
17M    /tmp
4.0K    /srv
31M    /boot
du: cannot access `/proc/17284/task/17284/fd/3': No such file or directory
du: cannot access `/proc/17284/task/17284/fdinfo/3': No such file or directory
du: cannot access `/proc/17284/fd/3': No such file or directory
du: cannot access `/proc/17284/fdinfo/3': No such file or directory
0    /proc
4.0K    /mnt
16K    /lost+found
0    /sys
5.7M    /bin
1.1M    /dev
63M    /opt
216M    /lib
16M    /etc
2.0G    /root
41G    /media
9.3M    /sbin
3.4G    /usr
4.0K    /selinux
47M    /home
504M    /var
47G    /
root@unknown:~# 

I still don't know really how to read it.

why is there 50Gig(?) in / ?

3.4G in /usr is that normal?
41G in /media is that extra drives?
2G in /root seems reasonable: is that the OS?

---

### Post by CharlesA on 2010-09-24
The listing for /media is any drives you have mounted, most likely data drives, so that's fine.

As for /usr: I just checked on my clean install and it's around 2GB, so I'd say it's normal. The size can vary depending on what all you have installed.

If you take away the 46GB in /media that leaves / with using only about 6GB, which is fine. :)

---

### Post by mastablasta on 2010-09-24
> **Nazaroo said:**
>  
I am installing Tweak, which calls itself a Hex-editor. 
 
what? the previous poster advised to install this one:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by libssd on 2010-09-24
> **Nazaroo said:**
> I was installing agedu, but it doesn't show up on the Ubuntu dropdown menu that I can see...

I am installing Tweak, which calls itself a Hex-editor.  Sounds like the "monitor" in an Apple IIe.  Haven't programmed in HEX since the 80s....

"Tweak" is not the same as "Ubuntu Tweak". **See:** [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Hobgoblin on 2010-09-24
> **Hobgoblin said:**
> 
The output of
```
df -h
```
might also be handy.

And the contents of /media

If you have really used 20GB then that seems to be the only place it could be.
It *should* only contain mount points for other filesystems but since you are logged in as root [-X there's nothing stopping you putting other stuff in there.

---

### Post by 7h3d4rk0n3 on 2010-09-24
Use the Computer Janitor utility and see if that helps.

---

