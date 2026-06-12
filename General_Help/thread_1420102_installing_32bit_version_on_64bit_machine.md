---
title: "installing 32bit version on 64bit machine"
date: 2010-03-02
forum: General Help
---

### Post by venkatad on 2010-03-02
Hi It looks like my lappy is 64bit...But I dont remember, So far I am using 32bit ubuntu. So How can I know if my computer is 64bit machine? if it is, Installing ubuntu 9.10 64bit will give any performance fetch??I guess 64bit ubuntu and 32bit are same interms of functionality and look Right? may be performance difference? give me some info...
Thanks

---

### Post by El Zoido on 2010-03-02
Any recent machine should be 64bit I think.
However, unless you have more than 3GiB ram, there isn't much reason to use a 64bit OS (as you need 64bit OS to use more than 3GiB ram without tricks).
For some applications 64bit may be faster, but you won't feel much of that in everyday use.

I'm using 64bit versions of Ubuntu for over a year now and never had real problems, but some people reported problems especially with Flash.

---

### Post by jpl888 on 2010-03-02
Well I don't think all Intel chips support 64 bit. Some of the Atoms don't for instance however you can check by typing ```
cat /proc/cpuinfo
```

If you can see "lm" in the output you are 64 bit.

It's swings and roundabouts. You will see a modest performance increase with some things and not with others. However if you use (or plan to use) anything out of the ordinary prepare for some hoop jumping or that you might not be able to get it to work with 64 bit (although reasonable unlikely these days).

---

### Post by audiomick on 2010-03-02
Funny, I just posted this about five minutes ago in another thread...
A conversation in another thread lead to the script in this post
[http://ubuntuforums.org/showpost.php?p=8851089&postcount=27](http://ubuntuforums.org/showpost.php?p=8851089&postcount=27)
save the script (via gedit) as "somename" in your home folder then do
```
bash ./somename
```it should give you an output something like this
```
mick@ubuntu-desktop:~$ bash ./anewdumb
Your computer is running 64 bit Linux

Your CPU is 64 bit capable
```with "32bit" and "64 bit" as applicable.

---

### Post by DedMoroz on 2010-03-02
Thanks for the tip. All along I thought my desktop was 32 bit, but according to this, it is 64  bit capable.

Technically, moving from 32 bit to 64 bit should allow you to double the amount of data it can process. It doesnt necessarily mean it will be twice as fast though. Most programs like writing a doc you wouldnt notice any difference, but when you are playing games, running programs like CAD, or audio and video encoding, image editing, ZIPping files, etc... you should notice a difference. 

Here are some interesting websites which might be helpful...

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by venkatad on 2010-03-02
THANKS GUYS....!
My machine is 64 bit yet
I LL JUST STICK WITH 32 BITS SINCE
I HAVE 3 GB RAM
and I dont really do video encoding/editing or other process that really need more resources...

---

