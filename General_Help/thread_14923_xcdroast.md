---
title: "xcdroast"
date: 2005-02-10
forum: General Help
---

### Post by varla on 2005-02-10
Hi 

I am trying to duplicate a bootable cd with xcdroast 0.98 alpha 15.
I go in Duplicate CD and that is where I notice that the cd information does not load.
I get no CD loaded. I have duplicated audio cds before and it works fine.
The only difference I have seen is that when I put in a data cd an icon for it is on my desktop. 
When I load an audio cd there is no icon.
 I don't know how to get the cd loaded.
Has anyone experienced this before??? 

How do I fix this problem?

Thanks

---

### Post by Wim Sturkenboom on 2005-02-11
I don't know if it will solve the problem, but try unmounting before you start duplicating the CD. In a terminal, enter the command *umount /media/cdrom*.

---

### Post by varla on 2005-02-11
Thanks Wim Sturkenboom

I was imagining I should try and unmount the cd, I didn't know how exactly.
I will try that.

---

### Post by varla on 2005-02-11
[QUOTE=varla]Thanks Wim Sturkenboom

I was imagining I should try and unmount the cd, I didn't know how exactly.
I will try that.[/QUOTE]
 So I did it and it sees the cd now but the data is being seen as audio.
I am trying to duplicate a bootable cd...it is the Dynebolic iso image on a cd I have.
I also tried to duplicate the ubuntu iso image from a cd and the same thing happens, it is being seen as audio... and it isn't we all know this.
What gives?

---

### Post by jkeelsnc on 2008-04-10
I am trying to get XCDRoast to operate correctly with a Sony CRX140E CDR drive.  It worked perfectly in windows just a few days ago!  Anyway, I used sudo xcdroast to start it but then it says "Starting to scan for devices..." and it never finishes.  In fact, one day I let it sit for a very long time (2 hours) and it never detected the CDRW drive.  What is up with this?

Thanks.

---

### Post by gpenguin on 2008-06-05
Same deal here under Hardy Heron (Xubuntu).  Scanning for devices never finishes.  I do a 'ps aux' and find the process:

   wodim dev= 2,0,0 -v -checkdrive

which seems to come from:

sh -c /usr/lib/xcdroast/bin/xcdrwrap CDRECORDDVD dev= "2,0,0" \
  -v -checkdrive 2>&1

When I kill the wodim process, it restarts with:

  wodim dev= 2,0,0 -prcap

now from:

sh -c /usr/lib/xcdroast/bin/xcdrwrap CDRECORD dev= "2,0,0" -prcap 2>&1

and maxing out the CPU.

After killing *that* wodim process, Xcdroast finally comes back saying the
scan has finished.  However, moving forward to use the program fails. Just going to view "CD/Image Info" causes it to max out the CPU again and never finish.

Now what?

---

