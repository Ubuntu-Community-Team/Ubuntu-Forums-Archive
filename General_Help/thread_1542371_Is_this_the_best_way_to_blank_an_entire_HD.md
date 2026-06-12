---
title: "Is this the best way to blank an entire HD?"
date: 2010-07-30
forum: General Help
---

### Post by giddyup306 on 2010-07-30
After doing some searching I found this:

```
dd if=/dev/zero of=/dev/hda 
```From what I understand, this will turn the drive into nothing but 0's. 

Is this the easiest and/or best way?  I'm giving my drive to someone else, and I don't want anyone to be able to dig up old data.  I will be running TestDisk after to see if I can see the partition. 


Thanks.

---

### Post by philinux on 2010-07-30
> **giddyup306 said:**
> After doing some searching I found this:

```
dd if=/dev/zero of=/dev/hda 
```From what I understand, this will turn the drive into nothing but 0's. 

Is this the easiest and/or best way?  I'm giving my drive to someone else, and I don't want anyone to be able to dig up old data.  I will be running TestDisk after to see if I can see the partition. 


Thanks.

That would do the trick you could add bs=1M option which I believe speeds the process up.
[http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux](http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux)

---

### Post by gzarkadas on 2010-07-30
To fully erase the contents of a drive you must write it repeatedly with specific series of patterns (which they generally cycle zeros and ones in each bit position), in order to reduce the residual magnetization below the noise threshold. If you don't do this then it is possible for someone with dedicated tools to recover your data even if you execute the mentioned dd command.

I would propose to use shred, which was designed with this specific task in mind and use not less than 25 iterations, like this:

```

shred --iterations=25 --zero /dev/hda

```The --zero switch is to end up with your hdd containing all zeros and it is optional since it does not affect the erase function, it just makes the disk look "empty".

Since you will be overwriting your disk 25 (+1 if --zero selected) times, you should expect it to take _much longer_ to finish.

---

### Post by philinux on 2010-07-30
> **gzarkadas said:**
> To fully erase the contents of a drive you must write it repeatedly with specific series of patterns (which they generally cycle zeros and ones in each bit position), in order to reduce the residual magnetization below the noise threshold. If you don't do this then it is possible for someone with dedicated tools to recover your data even if you execute the mentioned dd command.
.

They would need a team of FBI forensics in a dedicated lab with very expensive hardware.

[http://www.anti-forensics.com/disk-wiping-one-pass-is-enough](http://www.anti-forensics.com/disk-wiping-one-pass-is-enough)

---

### Post by giddyup306 on 2010-07-30
Thanks guys!  > **gzarkadas said:**
> To fully erase the contents of a drive you must write it repeatedly with specific series of patterns (which they generally cycle zeros and ones in each bit position), in order to reduce the residual magnetization below the noise threshold. If you don't do this then it is possible for someone with dedicated tools to recover your data even if you execute the mentioned dd command.

I would propose to use shred, which was designed with this specific task in mind and use not less than 25 iterations, like this:

```

shred --iterations=25 --zero /dev/hda

```The --zero switch is to end up with your hdd containing all zeros and it is optional since it does not affect the erase function, it just makes the disk look &quot;empty&quot;.

Since you will be overwriting your disk 25 (+1 if --zero selected) times, you should expect it to take _much longer_ to finish.

 Is there a way to track progress with that operation?   > **philinux said:**
> They would need a team of FBI forensics in a dedicated lab with very expensive hardware.

[http://www.anti-forensics.com/disk-wiping-one-pass-is-enough](http://www.anti-forensics.com/disk-wiping-one-pass-is-enough)

  Some guy on that site said that data could be recovered even if it had a second pass.  I'd rather be safe than sorry. :)

---

### Post by t0p on 2010-07-30
> **gzarkadas said:**
> To fully erase the contents of a drive you must write it repeatedly with specific series of patterns (which they generally cycle zeros and ones in each bit position), in order to reduce the residual magnetization below the noise threshold. If you don't do this then it is possible for someone with dedicated tools to recover your data even if you execute the mentioned dd command.


From [How To Permanently Erase Data from a Hard Disk]("http://mirror.href.com/thestarman/asm/mbr/WIPE.html"):

> 
[FONT=Times New Roman, Times, serif][SIZE=3]**But, we believe simply 'zeroing-out' a drive AND checking that    it has actually been done is more than adequate.** For example, say a competitor    was able to buy all of your old machines (and assuming, of course, that your    IT Dept. employees follow the proper procedures for doing at least a single-pass    'wipe' of each drive**[FONT=Verdana, Arial, Helvetica, sans-serif][COLOR=#ff0000]*[/COLOR][/FONT]**),    without knowing which drive contained any valuable data (or if any of them ever    did), we highly doubt anyone could justify the TIME and COST to employ an experienced    Electron Microscope operator in a Data Lab to hunt down bit by bit whatever    tiny amount of info they MIGHT find; with no assurances that ANYTHING (let alone    something of value) could ever be recovered! NOW IN THE YEAR 2008, after **15    years** of people warning others and passing along their fears of possible    scenarios involving elecron microscopes, WE STILL have NEVER heard of a single    case from any lab actually using a microscope to discover any useful bit patterns!


There's a good "secure delete" utility called [Darik's Boot And Nuke]("http://www.dban.org/") - it'll do a great job if you're that paranoid - but the dd command will do just fine.
[/SIZE][/FONT]   [SIZE=7][B][FONT=Times New Roman, Times, serif]
[/FONT][/B][/SIZE][FONT=Arial, Helvetica, sans-serif][SIZE=5][/SIZE][/FONT]

---

### Post by gzarkadas on 2010-07-31
[B]@philinux, @t0p:
[/B]
Thanks for the links; I took the time to read them all and update my (pre-millennium acquired) view on the subject. Indeed with today's drives a single pass seems enough for today's analytical capabilities of possible opponents. 

However I am still with the paranoids (as have long ago been) and because:

[LIST]
[*]releasing a disk out of ones control is a potential liability that can last several years (depending of course on what's in there),
[*]technology advances with a high pace; what is infeasible today may be feasible within a few years, sometimes even for less capable adversaries than agencies and high-profile organisations (thus a safety margin about the abilities and inabilities of the future is desirable),
[*]making some extra passes on a disk that one will no longer use is a very cheap operation,
[/LIST]
I think that doing some extra passes (I would now say 3-4) is both easily affordable and a nice safeguard from unanticipated future developments. 

This is of course my personal taste (or underlying paranoia, one could say) on the subject; I expect others' to vary :).

[B]@giddyup306:
[/B]
Adding the `--verbose' option to shred will provide progress messages.

---

### Post by ezsit on 2010-07-31
> However I am still with the paranoids (as have long ago been) and because

Sorry to cut you off, but if you are of this mindset, destroy the drive and don't give or sell it to anyone. If you really believe that anything you may have once stored on the drive is THAT important to keep secret, just pry the sucker open and destroy the platters. 

Did the drive give you a few years of reliable use? If so, then it was worth the $100 bucks and served its purpose and you can feel fine destroying such a drive.

I don't mean to be rude, but is your former computer use so dangerous in the hands of others who would require extreme talent, time, and expense to extract any possible shred of evidence?

---

