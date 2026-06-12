---
title: "MD5 sums of files keeps changing"
date: 2010-03-14
forum: General Help
---

### Post by u-slayer on 2010-03-14
I copied files from one hard drive to another so I made md5sums of the files to make sure everything went okay. They don't match. 

I wrote a quick bash command to compute the md5sums of all the files and save the result. Half of the time I get something different.

```
x=1;while [ 1 ]; do nice -n 8 md5deep -r -l copy > md5.of.copy.$x; x=$(($x+1)); done
```

[[IMG]http://imgur.com/bMNxP.png[/IMG]](http://imgur.com/bMNxP.png)

It's not just on ntfs. A different hard drive with an XFS filesystem shows the same thing happening.

I was wondering if my memory is corrupt so I did a quick test:
```
while [ 1 ]; do nice -n 8 dd if=/dev/zero bs=1G count=1000 | md5sum >> dev.zero.log; sleep 5m; done
```

Same result every time. No errors.

What's going on?

---

### Post by u-slayer on 2010-03-14
:p

---

### Post by u-slayer on 2010-03-15
:p

---

### Post by DawieS on 2010-03-15
I don't know much about MD5 sums, but if you have copied files to another drive, the file browser has a similar built-in check. Surely you would have received error messages if the destination is not "exactly" a replica of the source?

The same file may consume different sizes on disk, due to file systems being different from source to destination.

Is there perhaps a possibility that the version of md5sum that you use, is not 100% compatible to either the source or destination file systems? If so, then then one of the sums calculated may be incorrect.:grin:

---

### Post by Slim Odds on 2010-03-15
A) md5sum is pretty precise. If the sum is different, the files are different.

B) All modern file systems have exact sizes for files, so that's not likely the problem.

C) Summing all zero's is not a good test of any checksumming method.

D) Something in the process of copying is changing the file or it's getting changed after the fact before you sum it.

E) Your "copy program" may have a text/binary issue.

---

### Post by u-slayer on 2010-03-15
I'm scanning the same files on the same disk with md5sum repeatedly. Usually all of files had the same md5, but sometimes they have different md5 sums. 

Look at the screenshot in the first post. 
The same file has an md5 of of 59ddcb0fe4521515a6eb3eba14a21dcf. on scan 5, 51332dc52e9867b0968e9e828ad67f81 on scan 6, but its back to 59ddcb0fe4521515a6eb3eba14a21dcf on scan 7.

LINUX IS GIVING MD5SUM CORRUPTED DATA, sometimes.

---

### Post by falconindy on 2010-03-15
Are you overclocking your CPU? Inconsistent md5sums can be a sign of failing or improperly configured hardware.

---

### Post by gmargo on 2010-03-15
Does the same thing happen if you do it on a local, non-ntfs, filesystem?

---

### Post by u-slayer on 2010-03-15
> **falconindy said:**
> Are you overclocking your CPU? Inconsistent md5sums can be a sign of failing or improperly configured hardware.

No, CPU is not Overclocked.

Yes, the same thing happens on the XFS filesystem.

My computer does lock up and freeze sometimes when doing large file transfers. I'm running 2.6.31-20-generic x86_64 GNU/Linux if that helps.

---

### Post by Slim Odds on 2010-03-15
> **u-slayer said:**
> LINUX IS GIVING MD5SUM CORRUPTED DATA, sometimes.

A few hundred million people using LINUX don't have this problem. So guess where the problem is.

---

### Post by u-slayer on 2010-03-15
> **Slim Odds said:**
> A few hundred million people using LINUX don't have this problem. So guess where the problem is.

That's not very helpfull.

---

### Post by Slim Odds on 2010-03-15
> **u-slayer said:**
> That's not very helpfull.

It's very likely that you have a hardware problem. I once had a PC with a failing power supply that was providing marginal voltage levels. It would cause occasional seg faults. Bought a new power supply and the problem went away.

So stop saying "Linux did this or that". Linux works just fine. Troubleshoot your problem and narrow it down to find out what is really wrong.

That was my point.

---

### Post by u-slayer on 2010-03-16
> **Slim Odds said:**
> It's very likely that you have a hardware problem. I once had a PC with a failing power supply that was providing marginal voltage levels. It would cause occasional seg faults. Bought a new power supply and the problem went away.

So stop saying "Linux did this or that". Linux works just fine. Troubleshoot your problem and narrow it down to find out what is really wrong.

That was my point.

Ubuntu Forums:

Replies from users who read my post wrong or incompletely: 3
Replies from users that want to give me a lesson in semantics: 2
Replies from users that have solutions: 0

Thanks for all the help guys.

---

### Post by serosis on 2010-03-16
> **u-slayer said:**
> Ubuntu Forums:

Replies from users who read my post wrong or incompletely: 3
Replies from users that want to give me a lesson in semantics: 2
Replies from users that have solutions: 0

Thanks for all the help guys.


They gave you help, but you're not listening.
Changing MD5s can mean multiple things, when it's Linux you're running you can be damn sure it isn't the OS's fault. Unless you have a bad install in which it would be very noticeable.

You can start by taking the advice provided by actually checking your hardware.

Make sure your RAM isn't corrupt and/or fried
Make sure you have the correct settings in your bios
Make sure your CPU is at a nice cool temperature
*Make sure your HDD isn't failing or has bad sectors*

So on and so forth.

I highlight the HDD checking only because of your comment about your system hanging while copying large files.

---

### Post by Slim Odds on 2010-03-16
> **u-slayer said:**
> Thanks for all the help guys.

And thanks for you whining. It's why I come here to try to help for free.

---

### Post by Serpher on 2010-03-16
When using md5crypt for grub to make a boot loader password I got different results each time I was using it. Perhaps MD5 has an algorithm to produce multiple encryptions that lead back to the same string. I'm not on a Linux machine at the moment but if other people want to try running md5crypt on their machine for the same string and tell us what the results are.

---

### Post by Slim Odds on 2010-03-16
> **Serpher said:**
> When using md5crypt for grub to make a boot loader password I got different results each time I was using it. Perhaps MD5 has an algorithm to produce multiple encryptions that lead back to the same string. I'm not on a Linux machine at the moment but if other people want to try running md5crypt on their machine for the same string and tell us what the results are.

MD5 is a very specific algorithm that is designed to produce consistent results.

That does not mean that more than one file cannot produce the same MD5 sum. But the same file will always produce the same sum.

Read up.
[http://en.wikipedia.org/wiki/MD5](http://en.wikipedia.org/wiki/MD5)
[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)

---

