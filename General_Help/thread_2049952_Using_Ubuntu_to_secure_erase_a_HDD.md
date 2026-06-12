---
title: "Using Ubuntu to secure erase a HDD"
date: 2012-08-29
forum: General Help
---

### Post by aef54 on 2012-08-29
Hello Forum

Until now, I've always used DBAN if I wanted to wipe a hard drive. However, I am increasingly unhappy with it. It gives me a lot of errors.

So I was thinking (well, not really my idea, inspired by things I found on the internet),

would it be possible to:

- boot (L)Ubuntu from a USB drive
- detect the target hard disk drive.
- use a command like "shred" to overwrite the entire drive with one pass of (pseudo)random data

??

Kind regards,
aef

---

### Post by aef54 on 2012-08-29
Further questions:

- if such a command exists, would it be possible to show progress as it runs? Because overwriting an entire drive is going to take up to a few hours.

- If you guys have another alternative for DBAN, I'd love to hear it too.

---

### Post by MG&amp;TL on 2012-08-29
Shred would be extremely inefficient. You probably want something more like *dd*, an example would be as follows:

```
sudo dd if=/dev/urandom of=/dev/sda
```assuming /dev/sda is your HDD. 

If you want progress reports, try *pv, *as suggested here: [http://www.commandlinefu.com/commands/view/7214/start-dd-and-show-progress-every-x-seconds](http://www.commandlinefu.com/commands/view/7214/start-dd-and-show-progress-every-x-seconds)

Example:

```

dd if=/dev/urandom | pv | dd of=/dev/sda             

```If you don't need random data (not a security expert), replacing /dev/urandom with /dev/zero should give faster input rates.


A list of drives can be generated with the command:

```
sudo fdisk -l
```

---

### Post by nikonian on 2012-08-29
> **aef54 said:**
> Further questions:

- if such a command exists, would it be possible to show progress as it runs? Because overwriting an entire drive is going to take up to a few hours.

- If you guys have another alternative for DBAN, I'd love to hear it too.

You can use "dd" (disk dump) to do this from the command line. It's VERY easy, and yes - Ubuntu will detect your drive and dd, with su permissions, will wipe the entire drive... but you MUST ensure you specify the correct drive... or bye bye data! - I recommend ensuring that the drive to be wiped is the ONLY one in the PC when you wipe it.

You'd do:

#### DANGEROUS COMMANDS - CHECK THAT THE DRIVE IS ALONE IN THE PC AND THAT NO OTHER HARD DISKS ARE CONNECTED ####

```


sudo dd if=/dev/urandom of=/dev/<your_drive> bs=1M



```

AND/OR

```


sudo dd if=/dev/zero of=/dev/<your_drive> bs=1M


```

I'm sure there are better ways, and no - dd has no progress indication. 

[edit]

The suggestion of using "pv" to show progress has two issues:

1/ It is not installed by default, so needs installing.

2/ I have just tried it, and it is VERY VERY inaccurate.

---

### Post by aef54 on 2012-08-30
Hi guys.

This is what I did:

- I opened up my PC and pulled out the SATA cables of hard drives I did not want to erase (my standard practice whenever I format/wipe/reinstall the OS on one of my hard drives)
- I booted Ubuntu from the CD.
- In the terminal I typed this command:

[COLOR=Red]###WARNING! Command designed to irrecoverably destroy data!!! ####[/COLOR]
```

sudo dd if=dev/urandom of=dev/sda bs=1M

```

The prompt disappeared so I guess that means it' s busy.

I have no clue how long it' s going to take, but my guess is anywhere between 4 to 6 hours. I started at 18:20 so I' ll see when it returns the prompt back to me. (I am aware that I can put the process in the background, but then I do not know how I can see when it' s finished).

One thing I really dig about this way is that I can wipe a drive, and still use Ubuntu (albeit on a disk, without possibility to save anything). 

A disadvantage is that I'm really in the dark about how long it is going to take.

---

### Post by zero2xiii on 2012-08-30
Hay,

/dev/urandom will take somewhat longer than /dev/nul since it generates and uses random data instead of just writing zero's to the entire drive but this will be somewhat more secure than just zero'ing everything. Albeight just writing zero's to the drive should be sufficient unless the retriever is VERY determent to recover data. Some say it is impossible, some say it is.

But I think more like 10hours. Also dependant on the specs of the computer, and whether or not you use SATA2 or 1 :)


Cherz

---

### Post by MG&amp;TL on 2012-08-30
> **aef54 said:**
> 
A disadvantage is that I'm really in the dark about how long it is going to take.

You've started the job now, so it's not worth it, but in future check out the example I gave using pv.

---

### Post by aef54 on 2012-08-30
We're at roughly 3 hours and counting. I'm gonna give my computer 8  hours to finish the command, after that I'm killing the process.

> **MG&TL said:**
> You've started the job now, so it's not worth it, but in future check out the example I gave using pv.
Yes I wanted to do that. However, it says that the functionality needs to be installed before it works.

I'm using the Ubuntu live disc to run  the OS, I haven't installed it on a HDD (well, actually I have, but I'm wiping that one right now). I may be  wrong here but I think you can't install stuff when running Ubuntu from the CD (haven't tried, but I think it's impossible).

---

### Post by aef54 on 2012-08-30
One more question: 

when dd has overwritten the entire drive (using the command above), the process automatically finishes, right? It doesn't automatically go for another round, until I terminate the process by hand? Am I right?

---

### Post by oldfred on 2012-08-30
Another version in the repository:

from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

Homepage: [http://dcfldd.sourceforge.net/](http://dcfldd.sourceforge.net/)

---

### Post by aef54 on 2012-08-30
That sounds very promising. Too bad the command is already running (we're at 4 hours and counting). Next time I'm going to try that.

---

### Post by MG&amp;TL on 2012-08-30
> **aef54 said:**
> We're at roughly 3 hours and counting. I'm gonna give my computer 8  hours to finish the command, after that I'm killing the process.


Yes I wanted to do that. However, it says that the functionality needs to be installed before it works.

I'm using the Ubuntu live disc to run  the OS, I haven't installed it on a HDD (well, actually I have, but I'm wiping that one right now). I may be  wrong here but I think you can't install stuff when running Ubuntu from the CD (haven't tried, but I think it's impossible).

Okay, fair point. I thought you could, but tbh it's not something I've tried.

> **aef54 said:**
> One more question: 

when dd has overwritten the entire drive (using the command above), the process automatically finishes, right? It doesn't automatically go for another round, until I terminate the process by hand? Am I right?

Yeah, dd finished automatically. :)

---

### Post by aef54 on 2012-08-30
I'm at 7 and a half hours and I'm killing this process. 

7.5 hours for a HDD of 1TB  (and still not finished) means a throughput of less than 37Mb per second. That's unacceptable. Next time  I'm going to use the "dcfldd" command and see how it does.

---

### Post by aef54 on 2012-08-30
When I killed the process, I got a report:

```

196832+0 records in
196831+0 records out
206392262656 bytes (206 GB) copied, 27752.1 s, 7.4 MB/s

```

That speed is really crappy. To finish it, it would have taken more 35 hours.

Does anybody have an idea to make it faster?

---

### Post by nikonian on 2012-08-30
An awful lot of chatter for such a basic task...


> **zero2xiii said:**
> Hay,

/dev/urandom will take somewhat longer than /dev/nul since it generates and uses random data instead of just writing zero's to the entire drive but this will be somewhat more secure than just zero'ing everything. Albeight just writing zero's to the drive should be sufficient unless the retriever is VERY determent to recover data. Some say it is impossible, some say it is.

But I think more like 10hours. Also dependant on the specs of the computer, and whether or not you use SATA2 or 1 :)


Cherz


"/dev/null"? I think you meant "/dev/zero". "/dev/null" is a "black hole" where you re-direct things when you want them to go nowhere; it doesn't generate anything, it ABSORBS and sends streams to nowhere, hence "null". :)

---

### Post by dcstar on 2012-08-31
"Secure Erase" is a specific built-in function of ATA hard drives.

There is so much utter BS on this issue that people need to get some actual facts:

[http://www.anti-forensics.com/disk-wiping-one-pass-is-enough](http://www.anti-forensics.com/disk-wiping-one-pass-is-enough)

You can use Linux tools like hdparm to actually "Secure Erase" drives:

[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

---

### Post by aef54 on 2012-08-31
Normally when using DBAN, I get throughputs (writing speeds) of about 60 - 100 MB/s.

When using: " if=/dev/urandom", I got a speed of 7MB/s. I expected the CPU to be able to generate random bites faster than my HDD is able to write them, but apparently it is not.

When using the command:
```
sudo dd if=/dev/zero of=/dev/sda
```

```

21566465+0 records in
21566465+0 records out
11042030080 bytes (11 GB) copied, 528.384 s, 20.9 MB/s
```
It gives me a speed of 21 MB/s. This is better, but still very low. My HDD  should be able to write 5 times faster than that.

Do you guys have an idea to solve that?

---

### Post by aef54 on 2012-08-31
The problem I mentioned in my previous post (slow writing speed when zeroing) was solved with advice from this thread: 
[http://ubuntuforums.org/showthread.php?t=2050603](http://ubuntuforums.org/showthread.php?t=2050603)

---

### Post by oldfred on 2012-08-31
Link to caljohnsmith's post mentions that:

```
sudo apt-get install dcfldd
sudo dcfldd if=/dev/<source drive> of=/dev/<destination drive> statusinterval=10 bs=10M conv=notrunc
```

> The "statusinterval" times the "bs" or blocksize is how many bytes  dcfldd copies before it updates its progress, so in the above example  the progress will be updated for every 10M X 10 = 100 MB of data copied.  Using a blocksize of 10 MB works well, because that means dd copies 10  MB chunks at one time, rather than the default which is only 32 kB. That  means the copying goes alot faster. Also, to try and answer your  questions, I don't know of any way to set your source drive as  read-only, but if you are careful with the above command you should be  fine. In addition, you don't have to format the destination drive since  you will cloning the source drive byte-for-byte.

---

### Post by nikonian on 2012-08-31
> **dcstar said:**
> "Secure Erase" is a specific built-in function of ATA hard drives.

There is so much utter BS on this issue that people need to get some actual facts:

[http://www.anti-forensics.com/disk-wiping-one-pass-is-enough](http://www.anti-forensics.com/disk-wiping-one-pass-is-enough)

You can use Linux tools like hdparm to actually "Secure Erase" drives:

[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)


I tried the "secure erase" feature (it is part of the drive firmware for drives of around 20Gb or more, so I seem to recall), last week, and it failed! It doesn't work ALL the time for ALL drives.

This is a VERY long-winded thread for one person wanting to wipe one hard disk; the OP could have done it ten times over by now, without all this faffing on UF.

OP: Bottom line - boot from a LIVE CD, ensure the drive to be wiped is specified, take your method of choice, walk away and do something entirely to take your mind off it; it appears you are really over-thinking all this.

I am not one for waste, but if this drive is not destined to be re-used, smash it to smithereens with a hammer, and then bin it - it is way simpler than seeking the "perfect method" answer, as they don't exist. Anyone seeking *the* method, will be disappointed in life.

Try:

```
 sudo dd if=/dev/zero of=/dev/sda bs=2M 
```

[EDIT]

Why are there two threads for this, from the same OP?

---

