---
title: "Is there a program to limit terminal pipe speed?"
date: 2009-09-17
forum: General Help
---

### Post by SoftwareExplorer on 2009-09-17
I was using a combination of tar and ssh to backup the files on my computer and found it makes the connection between the two lag. I was wondering if there was some program that you can pipe data into and then out of that just lets you limit how fast the pipe runs? I think that would work, isn't the speed of the data being piped around dependent on the slowest link in the chain?

Thanks in Advance

---

### Post by undecim on 2009-09-17
I don't know of any program to do so (and google yields no meaningful results), though I don't see how limiting the speed would fix the lag. Data can only come out of one command as fast as it creates it, and the program it's piped to takes data from the buffer and does whatever it needs...

Maybe be a little more specific with how you are using tar and ssh, and we can figure out what is causing the lag?

EDIT: Sorry... Misunderstood the question.

---

### Post by s3a on 2009-09-17
sudo apt-get install trickle

examples:

trickle -d 5 -u 5 firefox

OR

trickle -d 5 -u 5 apt-get install firefox

Those two commands limit downloads/uploads to 5 kb/s of the program in the first case and the downloading of the program in the second case. It sounds like you would need the first if I understood your question. (Play with the numbers to suit your needs)

---

### Post by undecim on 2009-09-17
Ahh... I see... I misunderstood the question. I thought you were referring to a lag between tar and ssh.

EDIT: Using trickle, you will need to use it on the ssh command. (i.e. tar [options] | trickle [options] ssh [options])

---

### Post by SoftwareExplorer on 2009-09-17
I'm doing something like this: ```
tar -czf - /some/file | ssh 192.168.0.210 "tar -xzf - -C /destination"
```
If I understand correctly, when a program that is getting data is going faster than the program that is generating the data, it pauses. Well, I figure that if there was a program that read from stdin, limited the data flow to a certain speed, and then sent the data out in stdout, I could put it before ssh, (and therefore before the network) and limit the data speed. 
As far as trickle, does it sound like it would still kind of do what I need? The main thing is that with the LAN between the computers running at full speed, other connections have a latency of about 1-2 seconds. I like to use synergy between the computers and the lag get to be quite noticeable in the mouse cursor.

The program I'm imagining would be incredibly simple. you would use it like 'pipelimit --s=2M' and put it in your pipes to limit the bandwidth. 

Of course, this doesn't mean the answer to my problem has to work that way. 

Thanks!

Edit:I just saw undecim's edit. I'll try messing with trickle once the already running backup finishes.

---

### Post by unutbu on 2009-09-17
Perhaps try experimenting with ionice : [http://linux.die.net/man/1/ionice](http://linux.die.net/man/1/ionice)

Use ionice on the process which is consuming too much IO ?

---

### Post by SoftwareExplorer on 2009-09-17
> **unutbu said:**
> Perhaps try experimenting with ionice : [http://linux.die.net/man/1/ionice](http://linux.die.net/man/1/ionice)

Use ionice on the process which is consuming too much IO ?

It's not an io problem--it's network congestion on the LAN. I just figured there might be a simple tool like I described. I think that trickle will do it, but I'll wait to try that until the backup that is running right now is done. Thanks for the help anyways though.

---

### Post by unutbu on 2009-09-17
Yes, trickle seems like a more direct solution. 

Perhaps it is crazy of me, but I kind of wonder if you can avoid the LAN congestion problem by throttling the speed with which the initial tar can access the hard drive...

---

### Post by ethan1el on 2009-10-05
"cpipe -s <speed in kbps>" is what you need

[http://www.ubuntugeek.com/cpipe-determine-the-throughput-of-a-pipe-command.html](http://www.ubuntugeek.com/cpipe-determine-the-throughput-of-a-pipe-command.html)

here is how I use it to limit the dd speed while copying block devices on a busy system:
dd if=/dev/sdh1 bs=64k | cpipe -vt -s 1024 | dd of=/dev/sde1 bs=64k

---

### Post by SoftwareExplorer on 2009-10-06
> **ethan1el said:**
> "cpipe -s <speed in kbps>" is what you need

[http://www.ubuntugeek.com/cpipe-determine-the-throughput-of-a-pipe-command.html](http://www.ubuntugeek.com/cpipe-determine-the-throughput-of-a-pipe-command.html)

here is how I use it to limit the dd speed while copying block devices on a busy system:
dd if=/dev/sdh1 bs=64k | cpipe -vt -s 1024 | dd of=/dev/sde1 bs=64k

Thanks, that's just what I was looking for! :)

---

### Post by sdaau on 2011-03-18
> **SoftwareExplorer said:**
> 
[QUOTE=ethan1el;8057409]"cpipe -s <speed in kbps>" is what you need

[http://www.ubuntugeek.com/cpipe-determine-the-throughput-of-a-pipe-command.html](http://www.ubuntugeek.com/cpipe-determine-the-throughput-of-a-pipe-command.html)

here is how I use it to limit the dd speed while copying block devices on a busy system:
dd if=/dev/sdh1 bs=64k | cpipe -vt -s 1024 | dd of=/dev/sde1 bs=64k
Thanks, that's just what I was looking for! :)[/QUOTE]
+1, indeed! :) 

I'd just like to mention that previously in debian, there used to be a program called **bfr**, which apparently served the same purpose, but it apparently got removed in 2008: [Re: Removal candidate: bfr]("http://www.mail-archive.com/debian-qa@lists.debian.org/msg13629.html")...

And unfortunately, **cpipe** does not seem to be able to do fine-grained throughput rate control for output: consider that, when instructing it to allow 1 kB/s for a stream to a serial device:

```

$ cat example.txt | cpipe -vr -vw -vt -s 1 -b 1 > /dev/ttyUSB0 
  in:   0.441ms at    2.2MB/s (   2.2MB/s avg)    1024B
 out:   0.026ms at   37.6MB/s (  37.6MB/s avg)    1024B
thru: 980.148ms at    1.0kB/s (   1.0kB/s avg)    1024B
  in:   0.008ms at  122.1MB/s (   4.3MB/s avg)    2.0kB
 out:   0.017ms at   57.4MB/s (  45.4MB/s avg)    2.0kB
thru: 982.593ms at    1.0kB/s (   1.0kB/s avg)    2.0kB
  in:   0.009ms at  108.5MB/s (   6.4MB/s avg)    3.0kB
 out:   0.017ms at   57.4MB/s (  48.8MB/s avg)    3.0kB
thru: 984.750ms at    1.0kB/s (   1.0kB/s avg)    3.0kB

```.. , while it does sequence the stream in 1 kB packets per second, the actual write speed to the serial device is still some 40 MB/s (!, as I don't believe the serial driver in question is capable of such speeds at all).

I guess, what I want to say is: I wish cpipe had throughput control on level of bytes :) 
EDIT: ah yeah, the man says: 
[quote=man cpipe]
   Limiting Throughput
       If  a throughput limit is specified with option -s, cpipe calls usleep(3) in between copying buffers, thereby artifi&#8208;
       cially extending the duration of a read/write-cycle. Since on most systems there is a certain minimum  time  usleep()
       sleeps,  e.g. 0.01s, it is impossible to reach high limits with a small buffer size. In this case increasing the buf&#8208;
       fer size (option -b) might help. However, keep in mind that this limits the throughput only  on  the  average.  Every
       single buffer is copied as fast as possible.
[/quote]

EDIT2: Also [Linux: Limiting data throughput (pipe) in bytes per second?](http://stackoverflow.com/questions/5350499/linux-limiting-data-throughput-pipe-in-bytes-per-second)

Cheers!

---

