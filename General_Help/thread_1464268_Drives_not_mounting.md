---
title: "Drives not mounting"
date: 2010-04-28
forum: General Help
---

### Post by sunnyengineeer on 2010-04-28
Hello,

         I've been Ubuntu 8.10 along with Windows from abt 3-4 months
For automatically mounting of NTFS drives that I has which were created by WIndows, I uses NTFS Configuration tool.
       Everything was working fine in both OS's.
But how come of a sudden today I'm not able to open any drive that I have which were happening till now.
      Not only this,at least if we press F9 then we get sidebar,from where we could have opened the drive .even that is not happening.
  Can somebody plz explain me what has happened to my Ubuntu that it is behaving like this...& more than that to solve it.

Thanks
Sunny Sharma

---

### Post by sunnyengineeer on 2010-04-28
Can somebody please guide me...Im utterly in need of this.....!!!!!

---

### Post by Monkey77 on 2010-04-28
I am not 100% sure from your description if the problem is just related to NTFS partitions or a whole drive.

However I do know that if the NTFS drive is "dirty" as in it needs to be checked for corruption, then it will not mount it.

Try booting windows and performing a chkdsk /F on the affected partition.

---

### Post by spufi on 2010-04-28
What type of disks are these?  USB?  Internal disks?  SAN LDEV's?  
You mentionned this was working fine before, so what has changed since?  Did you do an dist-upgrade?  Or have you changed some configuration files?  Some settings?
(in other words: the more info, the merrier)

Anyway, in case it's a USB enclosure, unplug the drives and tail your messages file in a terminal:
```
tail -f /var/log/messages
```
Once you reconnect the USB drive, you'll see a bunch of kernel output in the terminal.  This output should give you a clue which logical device name your disks will have and possibly even what the problem might be.

---

### Post by sunnyengineeer on 2010-04-28
Thanks guys for replying quickly...

Actually I made a mess of my HD myself...I think this was the reason...

Actually I created one more partition form Windows using DiskManagement using its GUI.
But I didn't shut down it properly,bcz I was in hurry...
When I came back I saw none of the NTFS partition was opening in Ubuntu...
I was in extreme hurry that time bcz our college submissions are going on...& not like my friends I do work in Ubuntu softwares...so my files were in NTFS drives but I can open them from Ubuntu....so that took almost a hell out of me...

After reading ur posts I thought o give a reboot,than It all worked....Cheers...

Now as we have tea break,so I'll submit before lunch time  & can go to my home after submission....

Thanks to all the guys who responded in such a quick time....U all r great...
& More than that Ubuntu Forum is such a gr8 place to learn,to tkae help ...& to know where we didi wrong.....

Once again thanks to all...I'll punch my head on the wall for this stupididy...

Sunny Sharma

---

