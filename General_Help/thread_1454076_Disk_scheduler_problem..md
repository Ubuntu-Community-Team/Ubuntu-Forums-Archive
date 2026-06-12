---
title: "Disk scheduler problem."
date: 2010-04-14
forum: General Help
---

### Post by Japsser on 2010-04-14
Hi,

As an assignment, I need to run a couple of benchmarks on my ubuntu system here at home using the 4 different disk schedulers.
To save myself some time and because the PC isn't the fastest I decided to run them at night consecutively usign a little script.
First I saved the batch settings for the test suite and ran this script last night:

```
#!/bin/sh
phoronix-test-suite batch-run compilebench unpack-linux
sudo bash -c 'echo deadline > /sys/block/sda/queue/scheduler'
phoronix-test-suite batch-run compilebench unpack-linux
phoronix-test-suite batch-run compilebench unpack-linux
phoronix-test-suite batch-run compilebench unpack-linux
sudo bash -c 'echo anticipatory > /sys/block/sda/queue/scheduler'
phoronix-test-suite batch-run compilebench unpack-linux
phoronix-test-suite batch-run compilebench unpack-linux
phoronix-test-suite batch-run compilebench unpack-linux
sudo bash -c 'echo noop > /sys/block/sda/queue/scheduler'
phoronix-test-suite batch-run compilebench unpack-linux
phoronix-test-suite batch-run compilebench unpack-linux
phoronix-test-suite batch-run compilebench unpack-linux

Main HDD info:
          *-disk:0
                description: ATA Disk
                product: Maxtor 4D040H2
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: DAH0
                serial: D20D762E
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ea1aa9c7
                            *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 90ffab18-7234-4be8-bf40-cb9857c147bc
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-26 15:17:19 filesystem=ext3 modified=2010-04-13 19:47:12 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2010-04-13 19:47:12 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1474MiB
                   capacity: 1474MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1474MiB
                      capabilities: nofs


```So as far as I know I did everything correct, yet my results all indicate it used CFQ as disk scheduler(which is the initial setting). If I run 
root@jasper-desktop:~# cat /sys/block/sda/queue/scheduler
I get:
[noop] anticipatory deadline cfq 

so it actually indicates the right scheduler, though it doesn't seem like it in the results... (the numbers are all very alike btw, which probably shouldn't be the case)

I ran one of the benchmarks manually this morning, after I checked the scheduler was set to noop, and these are the results:
[IMG]http://i42.tinypic.com/6hqhvn.png[/IMG]

So, anyone got an idea as to where this went wrong?

---

### Post by 3rdalbum on 2010-04-14
The 'sudo bash -c' part probably hangs up waiting for you to type your password. Instead you should change it to:

```
#!/bin/sh
phoronix-test-suite batch-run compilebench unpack-linux
echo deadline > /sys/block/sda/queue/scheduler
phoronix-test-suite batch-run compilebench unpack-linux
phoronix-test-suite batch-run compilebench unpack-linux
phoronix-test-suite batch-run compilebench unpack-linux
echo anticipatory > /sys/block/sda/queue/scheduler
phoronix-test-suite batch-run compilebench unpack-linux
phoronix-test-suite batch-run compilebench unpack-linux
phoronix-test-suite batch-run compilebench unpack-linux
echo noop > /sys/block/sda/queue/scheduler
phoronix-test-suite batch-run compilebench unpack-linux
phoronix-test-suite batch-run compilebench unpack-linux
phoronix-test-suite batch-run compilebench unpack-linux

```

and run the script as root.

---

### Post by Japsser on 2010-04-14
^I ran it as root, and well the script finished successfully, so I asume it didn't hang? I have about 12 results but they're all the same :P. And after the script if I checked the scheduler it actually indicated noop is the current active one, so that means the script did indeed change the disk scheduler right?

---

### Post by john newbuntu on 2010-04-14
If you had run the script as root and found no difference, run your own custom benchmark test.  

Replace phoronix's with a simple *ix command, say "time cat largeFile > /dev/null" or something like that.  Check with "cat /sys/block/sda/queue/scheduler". Change scheduler. Lather, rinse and repeat.

Now, if this custom test works and is truly changing the scheduler as we think it to be, then look into your test suite and see if there are any options that is making it use the default CFQ scheduler (or is this a bug??).

---

### Post by Japsser on 2010-04-14
So I did that, with a 100MB file and these are the results. Are these differences big enough to indicate the scheduler has indeed changed? I know it's a small testing file but I couldn't get a bigger one really quick.

And in my documentation there's no indication that the benchmarking suite has a default scheduler setting.

```
root@jasper-desktop:/home/jasper/Downloads# echo noop >  /sys/block/sda/queue/scheduler
root@jasper-desktop:/home/jasper/Downloads# cat  /sys/block/sda/queue/scheduler
[noop] anticipatory deadline cfq 

root@jasper-desktop:/home/jasper/Downloads# time cat file > /dev/null  

real    0m0.211s
user    0m0.012s
sys    0m0.144s

root@jasper-desktop:/home/jasper/Downloads# echo anticipatory > /sys/block/sda/queue/scheduler
root@jasper-desktop:/home/jasper/Downloads# cat /sys/block/sda/queue/scheduler
noop [anticipatory] deadline cfq 
root@jasper-desktop:/home/jasper/Downloads# time cat file > /dev/null 

real    0m0.170s
user    0m0.008s
sys    0m0.164s
root@jasper-desktop:/home/jasper/Downloads# echo deadline > /sys/block/sda/queue/scheduler
root@jasper-desktop:/home/jasper/Downloads# cat /sys/block/sda/queue/scheduler
noop anticipatory [deadline] cfq 
root@jasper-desktop:/home/jasper/Downloads# time cat file > /dev/null 

real    0m0.167s
user    0m0.004s
sys    0m0.164s
root@jasper-desktop:/home/jasper/Downloads# echo cfq > /sys/block/sda/queue/scheduler
root@jasper-desktop:/home/jasper/Downloads# cat /sys/block/sda/queue/scheduler
noop anticipatory deadline [cfq] 
root@jasper-desktop:/home/jasper/Downloads# time cat file > /dev/null 

real    0m0.165s
user    0m0.012s
sys    0m0.152s



```

---

### Post by john newbuntu on 2010-04-14
I was hoping you would stick all those commands into just one script and fire it off once.  You could try that.  But, I really doubt if that would change anything.

Sorry, I do not know much about their testing suite to pinpoint your problem.  But looking into Phoronix's documentation at: [http://www.phoronix-test-suite.com/documentation/1.8/pts_options.html](http://www.phoronix-test-suite.com/documentation/1.8/pts_options.html) , instead of using the batch-run option, use the "run" option and give it a different test (not sure on what other tests exists).  Maybe running it in a non-batch mode and a different test might shed some light.

---

