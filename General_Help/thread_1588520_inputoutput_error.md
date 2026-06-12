---
title: "input/output error"
date: 2010-10-05
forum: General Help
---

### Post by supermooshman on 2010-10-05
Hi all,

recently I got an error in my download folder.
Everytime I open it, I get a notification window saying "input/output error"
Pretty vague...

It seems that my download folder somehow changed to read only, but I did not change anything (or at least as far as I know)  

anyone knows how I can check what the exact problem is?

---

### Post by supermooshman on 2010-10-05
bump?

---

### Post by Merthod on 2010-10-05
Could you post the permissions for the folder? (Command ls -l)

---

### Post by Merthod on 2010-10-05
It also may be that your file system is corrupted, so I'd recommend to check it. However, it is NOT recommended doing it in mounted partition, so you would have to do it from a Live CD.

Check [FONT="Courier New"]fsck[/FONT] command to understand its output.

---

### Post by supermooshman on 2010-10-05
> **Merthod said:**
> Could you post the permissions for the folder? (Command ls -l)

Euhm, can you specify what you need to know?
I got ```
-rw-r--r--  user user 254496 2010-09-11 09:39 filename
ls: cannot access filename: Input/output error
-?????????? ? ?    ?           ?              ?  filename
```

> **Merthod said:**
> It also may be that your file system is corrupted, so I'd recommend to check it. However, it is NOT recommended doing it in mounted partition, so you would have to do it from a Live CD.

Check [FONT="Courier New"]fsck[/FONT] command to understand its output.
It is my internal second sdd, would it be safe to unmount and run fsck?

---

### Post by Merthod on 2010-10-06
What to you think may have caused this problem? But for the meantime you can just check that your file system is ok. Sometimes they get messed up with no apparent reason.

You can check it from wherever you want you if you have this partition **unmounted**. If you ran fsck right now it itself would warn you that doing so in a mounted partition ***WILL*** cause damage to your file system, and therefore ask for your confirmation. So if you can boot and have access to a terminal to check this partition in your second partition go ahead, or a Live CD will do the job. 

Here's a little further reading: [http://adminschoice.com/repairing-unix-file-system-fsck]("http://adminschoice.com/repairing-unix-file-system-fsck")

---

### Post by supermooshman on 2010-10-06
> **Merthod said:**
> What to you think may have caused this problem?  [http://adminschoice.com/repairing-unix-file-system-fsck]("http://adminschoice.com/repairing-unix-file-system-fsck")

Cool this did the trick


If anyone would be interested in finding out why it happened, hopefully this helps:
```
user@desktop:~$ sudo fsck /media/sdb1
fsck from util-linux-ng 2.17.2
WARNING: bad format on line 13 of /etc/fstab
e2fsck 1.41.11 (14-Mar-2010)
/dev/sdb1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 212995 has zero dtime.  Fix<y>? yes


Inode 294914, i_blocks is 239728, should be 244568.  Fix<y>? yes

Pass 2: Checking directory structure
Entry 'filename1' in /Downloads (65537) has deleted/unused inode 65579.  Clear<y>? yes

Entry 'filename2' in /Downloads (65537) has deleted/unused inode 65580.  Clear<y>? yes

Entry 'filename3' in /Downloads (65578) has deleted/unused inode 294918.  Clear<y>? yes

Entry 'filename4' in /Downloads (65578) has deleted/unused inode 294935.  Clear<y>? yes

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Inode 65581 ref count is 1, should be 2.  Fix<y>? yes

Pass 5: Checking group summary information
Block bitmap differences:  -(132115--132122) -(438274--438278) -(640576--640622) -(640679--640737) -(640770--640785) -(640830--641052) -(641113--641319) -(641388--641470) -(641479--641936) -(641940--642329) -(642335--642435) -(642440--642441) -(642448--642451) -(642458--642461) -(642468--642484) -(642586--642590) -(642596--642707) -(642712--643072) -(643080--643090) -(643096--643143) -(643172--643715) -(643720--643727) -(643732--643795) -(643800--643987) -(643992--644051) -(644056--644086) -(644107--644387) -(644411--644423) -(644428--644633) -(644644--644775) -(644780--644807) -(644812--644826) -(644840--644858) -(644863--644888) -(644920--644931) -(644936--644954) -(644959--644963) -(645019--645029) -(645034--645092) -(645147--645148) +(645265--645268) -(645278--645325) -(645338--645361) -(645366--645406) -(645411--645544) -(645549--645584) -(645617--645649) -(645654--645656) -(645659--645690) -(645704--645707) -(645763--645770) +(645799--645800) -(645801--645807) +(645808--645817) +(645822--645825) -(645827--645871) -(645903--645959) -(645964--645980) -(645984--645985) +(646005--646012) -(646027--646035) -(646054--646126) +(646163--646166) -(646171--646214) -(646216--646293) -(646313--646382) -(646427--646429) +(646457--646460) -(646473--646514) -(646569--646622) -(646729--646732) +(646733--646736) -(646825--646884) -(646889--646893) +(646898--646901) +(646905--646908) +(646913--646916) +(646921--646924) +(646932--646935) +(646953--646956) +(646993--646996) +(647016--647019) +(647022--647025) -(647081--647095) -(647116--647123) -(647372--647374) +(647656--647659) +(647684--647687) +(647967--647970) +(647992--647994) +(648030--648045) +(648059--648066) +648080 +(648126--648129) +(648193--648196) +(648204--648211) +(648232--648235) +(648248--648250) +648255 +(648276--648279) +(648483--648486)
Fix<y>? yes

Free blocks count wrong for group #4 (11427, counted=11435).
Fix<y>? yes

Free blocks count wrong for group #13 (6, counted=11).
Fix<y>? yes

Free blocks count wrong for group #19 (9361, counted=13919).
Fix<y>? yes

Free blocks count wrong (2906813, counted=2911384).
Fix<y>? yes

Inode bitmap differences:  -(65579--65580) -212995 -(294918--294934)
Fix<y>? yes

Free inodes count wrong for group #4 (16293, counted=16295).
Fix<y>? yes

Free inodes count wrong for group #13 (16383, counted=16384).
Fix<y>? yes

Free inodes count wrong for group #18 (16362, counted=16379).
Fix<y>? yes

Directories count wrong for group #18 (2, counted=1).
Fix<y>? yes

Free inodes count wrong (1981437, counted=1981457).
Fix<y>? yes

```

---

### Post by Merthod on 2010-10-06
Glad you've solved your system's problem. If you are satisfied please mark this thread as resolved. In "Thread Tools" you'll find the option.

---

