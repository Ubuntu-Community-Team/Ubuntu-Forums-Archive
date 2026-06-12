---
title: "need help to undelete mysql database files and restore DB"
date: 2011-05-08
forum: General Help
---

### Post by thejoester on 2011-05-08
OK so here is what happened. 

I installed Ubuntu 10 (maverick) for a friend of mine who wanted to host a web server with PHP and MYSQL. 

IT was all setup and running fine except one day after doing some updates my friend reboots the machine and suddenly it will not boot. The cursor was flashing and then it reported "Read Error"

Well rather than look for help he decided to test the Hard drive with a boot diagnostic disk, and when that checked out per something he read online booted to the Ubuntu CD I had burned for him intending to repair it. Well, he reinstalled a fresh install (with a format of that partition of course). 

Now here is the problem. He had some data in a mysql database that we need to get restored if at all possible. 

I have run photorec to restore only the mysql files but It does not restore them to their original names or directories so at this point I have a munch of .myi and .myd files but no idea how to get thier data into mysql. 

Any guides out there on how to do this or maybe a better way to recover the data from the HDD?

thanks in advance to any help I may get with this!

---

### Post by dragonfly41 on 2011-05-08
What does running  **[COLOR=DarkSlateBlue]myisamchk *.MYI[/COLOR]**  command do for you?

[http://dev.mysql.com/doc/refman/5.0/en/myisam-table-maintenance.html](http://dev.mysql.com/doc/refman/5.0/en/myisam-table-maintenance.html)

---

### Post by thejoester on 2011-05-09
@dragonfly41: Thanks for that tip! 

ok so I found a directory with a .MYI file in it, ran the ```
myisamchk *.MYI
```

What I get back is a bunch of this:

```
---------

myisamchk: File 'f34950824.MYD' not found (Errcode: 2)
myisamchk: error: File 'f34950824.MYI' doesn't exist

---------

myisamchk: File 'f34950840.MYD' not found (Errcode: 2)
myisamchk: error: File 'f34950840.MYI' doesn't exist

---------

myisamchk: File 'f34950920.MYD' not found (Errcode: 2)
myisamchk: error: File 'f34950920.MYI' doesn't exist

---------
```

I think the photorec program only recovered the .MYI files so now  I am going to attempt to use testdisk to see if I can restore the files.

I have never restored files on linux before but when I have done it on windows in the past with most programs it will show the deleted directories and I can just restore that whole directory and choose a place to restore it to. is there anything like that on linux?

---

### Post by dragonfly41 on 2011-05-09
I guess that you are getting these errors because photorec changes file names if they are recovered.  

Others in this forum have had similar problems trying to recover.

e.g. see here .. [http://ubuntuforums.org/showthread.php?t=1742220](http://ubuntuforums.org/showthread.php?t=1742220)


I think that this is because the Partition Table is lost in your partition.

As an windows Vista user as well as recent unbuntu user (dual boot) I've had good results using recovermyfiles in windows.

You can try this in a free demo at [http://www.recovermyfiles.com](http://www.recovermyfiles.com) .. but it has to run in windows.


[EDIT] 

Tips on data recovery ..

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


Try partition table recovery using Testdisk.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by thejoester on 2011-05-11
thanks again for the tips, I am still having no luck. 

So to sum up where I am now...

I used photorec ant it recovered a lot of .myi files with names like "f34950824.MYD". When I tried using **myisamchk** it errors out as there is no .MTD files. 

I tried using foremost, scalpel and testdisk. I cannot get it to recover the removed /var/lib/mysql directory. Nor can I even get them to find any .MYI or .MYD files. 

I tried other programs such as recovermyfiles, Stellar, and Final Recovery all with the same results. 

One did have the option to add custom file types but it requires me to enter file header information in hex, how do I find this. 

If anyone has any other help they could give, that would be awesome. 

thanks!

---

### Post by dragonfly41 on 2011-05-12
Okteta is one hex editor you can try .. install via Synaptic Package Manager

another is Ghex

there are others


[EDIT]

Just to add that I found reference to Autopsy and sleuthkit

[http://www.sleuthkit.org/index.php](http://www.sleuthkit.org/index.php)

but I haven't got around to trying it.

Autopsy is in Synaptic Package Manager as front end to sleuthkit.

---

### Post by thejoester on 2011-05-12
I believe both of these are on the backtrack live CD I just downloaded so I will try these. 

thanks

---

