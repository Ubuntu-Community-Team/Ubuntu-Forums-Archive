---
title: "Bad Sectors on Mybook"
date: 2010-03-20
forum: General Help
---

### Post by panti19 on 2010-03-20
Hi, I have a MyBook 500gb external hard drive and it's been infected on a Windows machine by the sal.xls.exe virus. I've connected it to my Ubuntu 9.10 machine and deleted sal.xls.exe from the drive, however Ubuntu says that there are many bad sectors on the drive and that the drive is failing.
Does this have anything to do with the virus?
Is the drive safe now on Windows?
Can it be fixed?

Thanks

---

### Post by linden940 on 2010-03-20
that happened with one of my laptops...i did a full heath check on the hard drive....the hard drive was just fine...no bad sectors

since you run this hard drive ON windows ez thing for you to do for a simple heath check

start>run>cmd

once you get the black cmd screen up type this in

chkdsk

it will do 3 tests...the 3ed test taking the longest and after it will tell you if you have any bad sectors

---

### Post by panti19 on 2010-03-20
thanks,but do you know anything about the virus? i mean is it really gone if I deleted the exe?

---

### Post by soltanis on 2010-03-20
Probably not. The only way to be sure you've deleted a virus from a partition is to format it.

The thing about viruses is that they try to infect files, and depending on the virus and how skilled its writer was, it could've made a lot of copies of itself in your files.

If you have any you need to save, you should pull them off the drive (in a clean environment, like Linux) and scan them with ClamAV before saving them and formatting the external disk.

EDIT:
How many bad sectors does the disk have? If this is palimpset (the "disk utility") talking to you, it has this annoying habit of equating bad sectors to a failing drive. Although it can be true that drives show bad sectors before they go under, it is also completely normal for new hard disks to have one or two bad sectors "off the shelf". Drives are manufactured with extra sectors and automatically swap them out for exactly this reason, actually.

Check the rest of the data, or post the result of
```

sudo apt-get install smartmontools
sudo smartctl -a -H /dev/<disk>

```
Replace /dev/<disk> with the proper /dev/ device node. You can find it by plugging in the MyBook, going into a terminal, and typing
```

mount

```

Look for something mounted in /media.

If the data doesn't match up then ignore the "drive failing" warning. I've personally never heard of a virus that screwed up drive sectors, though with Windows, anything is possible.

---

### Post by panti19 on 2010-03-20
Installed KlamAV. It's scanning and so far nothing.. which is good.
Also I actually think the virus is gone since it is not that destructive.
[http://threatinfo.trendmicro.com/vinfo/virusencyclo/default5.asp?VName=WORM_VB.CII&VSect=P](http://threatinfo.trendmicro.com/vinfo/virusencyclo/default5.asp?VName=WORM_VB.CII&VSect=P)

Will post final results

---

