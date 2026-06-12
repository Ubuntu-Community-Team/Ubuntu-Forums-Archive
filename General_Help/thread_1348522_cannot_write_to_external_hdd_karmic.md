---
title: "cannot write to external hdd karmic"
date: 2009-12-07
forum: General Help
---

### Post by netopalis45 on 2009-12-07
i accidently formatted my external usb hard drive. before i did this i could read and write to/from the drive with no problem. after i formatted it i can no longer write to the drive even though i have changed the owner to me.
i am running karmic and the external drive is formatted fat32. 
can anyone help me with this?

---

### Post by prem1er on 2009-12-07
Paste output of 

```
ls -lrt
```

where the drive is mounted.

---

### Post by netopalis45 on 2009-12-07
> **prem1er said:**
> Paste output of 

```
ls -lrt
```where the drive is mounted.

ls: cannot access ï&#9492;uï&#8734;sï]Vï: Input/output error                                                                                                      
ls: cannot access E&#931;3 ë}&#8319;ï.u                                                                                                                          
                            ;: Input/output error                                                                                                     
ls: cannot access                                                                                                                                     
                  aû&#9496;&#9558;i/f: No such file or directory                                                                                                  
ls: cannot access       x&#9571;I/F: No such file or directory                                                                                              
ls: cannot access f&#9608;&#9573;&#9500;&#9559;i/f: No such file or directory                                                                                                 
ls: cannot access ï uï&#8734;sï]Vï: Input/output error                                                                                                      
: Input/output error&#9557;.ï                                                                                                                               
ls: cannot access &#9618;.&#9496;/: No such file or directory                                                                                                     
ls: cannot access ß$&#960;Q&#9564;I/F: No such file or directory                                                                                                 
ls: cannot access ï uï&#8734;sï]Vï: Input/output error                                                                                                      
: Input/output error&#9557;.ï                                                                                                                               
total 22204192                                                                                                                                        
-rwxr-xr-x  1 josh root   77656528 1910-09-04 17:31 ?.¬i                                                                                              
-rwxr-xr-x  1 josh root   77656528 1910-09-04 17:31 ?.&#9566;à                                                                                              
-rwxr-xr-x  1 josh root   77656528 1910-09-04 17:31 ?.?&#9564;?                                                                                             
-rwxr-xr-x  1 josh root 1443388811 1913-09-14 17:31 ?                                                                                                 
-rwxr-xr-x  1 josh root 1443388811 1913-09-14 17:31 ?                                                                                                 
-rwxr-xr-x  1 josh root 1443388811 1913-09-14 17:31 ?                                                                                                 
-rwxr-xr-x  1 josh root          0 1938-11-25 18:08 H,.&#9554;<@                                                                                            
-rwxr-xr-x  1 josh root      11336 1939-11-25 17:31 &#9552;?.?                                                                                              
-rwxr-xr-x  1 josh root          0 1951-11-25 18:08 Kà.&#9554;<@                                                                                            
-rwxr-xr-x  1 josh root          0 1951-11-25 18:08 Kà.&#9554;<@                                                                                            
-rwxr-xr-x  1 josh root 2088831526 1954-12-02 18:08 p&#949;?.p&#949;?                                                                                           
-rwxr-xr-x  1 josh root       3768 1963-11-25 17:31 4E.?                                                                                              
-?????????  ? ?    ?             ?                ? ?x??&#9571;I/F                                                                                          
d?????????  ? ?    ?             ?                ? ÷W&#9557;?.?ï?                                                                                          
d?????????  ? ?    ?             ?                ? ÷w&#9557;?.?ï?                                                                                          
-?????????  ? ?    ?             ?                ? ß$&#960;Q&#9564;I/F                                                                                          
d?????????  ? ?    ?             ?                ? ï uï&#8734;sï].?Vï                                                                                      
d?????????  ? ?    ?             ?                ? ï uï&#8734;sï].?Vï                                                                                      
d?????????  ? ?    ?             ?                ? ï&#9492;uï&#8734;sï].?Vï                                                                                      
-?????????  ? ?    ?             ?                ? f&#9608;&#9573;&#9500;&#9559;i/f                                                                                          
d?????????  ? ?    ?             ?                ? E&#931;3 ë}&#8319;ï.u?;                                                                                      
-?????????  ? ?    ?             ?                ? ?aû&#9496;&#9558;i/f                                                                                          
-?????????  ? ?    ?             ?                ? ?.&#9496;/                                                                                              
-rwxr-xr-x  1 josh root  209552364 1971-11-03 17:31 &#963;                                                                                                 
-rwxr-xr-x  1 josh root  209552364 1971-11-03 17:31 &#963;                                                                                                 
-rwxr-xr-x  1 josh root          0 1980-01-01 00:00 ?.                                                                                                
-rwxr-xr-x  1 josh root          0 1980-01-01 00:00 ?.                                                                                                
-rwxr-xr-x  1 josh root          0 1980-01-01 00:00 ?.                                                                                                
-rwxr-xr-x  1 josh root          0 1980-01-01 00:00 ?.                                                                                                
-rwxr-xr-x  1 josh root         64 1980-01-01 00:00 &#9632;&#9492;&#937;&#8730;MZÉ.?                                                                                         
-rwxr-xr-x  1 josh root          0 1980-01-01 00:00 &#963;.                                                                                                
-rwxr-xr-x  1 josh root         64 1980-01-01 00:00 z?á?MZÉ.?                                                                                         
-rwxr-xr-x  1 josh root   77656544 1980-01-01 00:00 t±á?.kà                                                                                           
-rwxr-xr-x  1 josh root   77656544 1980-01-01 00:00 t±á?&#9492;&#8745;?.kà                                                                                        
-rwxr-xr-x  1 josh root         64 1980-01-01 00:00 S&#9516;Z&#9560;MZÉ.?                                                                                         
-rwxr-xr-x  1 josh root         64 1980-01-01 00:00 &#9557;O&#9569;LMZÉ.?                                                                                         
-rwxr-xr-x  1 josh root   77656544 1980-01-01 00:00 @K.kà                                                                                             
-rwxr-xr-x  1 josh root 1818587694 1980-01-01 00:00 ï}?u?â=&#9508;.±&#949;G                                                                                      
-rwxr-xr-x  1 josh root 1818587694 1980-01-01 00:00 ï}?u?â=&#9560;.0&#9472;u                                                                                      
-rwxr-xr-x  1 josh root          0 1980-01-01 00:00 ÷h                                                                                                
-rwxr-xr-x  1 josh root   77656544 1980-01-01 00:00 êf.x*                                                                                             
-r-xr-xr-x  1 josh root          0 1980-01-01 00:00 &#9554;<@dT?.?                                                                                          
-r-xr-xr-x  1 josh root          0 1980-01-01 00:00 &#9554;<@dT?.?                                                                                          
-r-xr-xr-x  1 josh root          0 1980-01-01 00:00 &#9554;<@dT?.?                                                                                          
-r-xr-xr-x  1 josh root          0 1980-01-01 00:00 &#9554;<@dT?.?                                                                                          
-r-xr-xr-x  1 josh root          0 1980-01-01 00:00 &#9554;<@dT?.?                                                                                          
-rwxr-xr-x  1 josh root         64 1980-01-01 00:00 Å&#9566;&#9577;áMZÉ.?                                                                                         
-rwxr-xr-x  1 josh root          0 1980-01-01 00:00 ?                                                                                                 
-rwxr-xr-x  1 josh root          0 1980-01-01 00:00 ?                                                                                                 
-rwxr-xr-x  1 josh root          0 1980-01-01 00:00 ?                                                                                                 
-rwxr-xr-x  1 josh root          0 1980-01-01 00:00 ?                                                                                                 
-rwxr-xr-x  1 josh root          0 1980-01-01 00:00 ?                                                                                                 
-rwxr-xr-x  1 josh root          0 1980-01-01 00:00 &#9492;&#8745;?                                                                                               
-rwxr-xr-x  1 josh root     126912 1980-01-01 00:00 t?.d±á                                                                                            
-rwxr-xr-x  1 josh root          0 1980-01-04 15:33 PE                                                                                                
-rwxr-xr-x  1 josh root          0 1980-01-04 15:33 PE                                                                                                
-rwxr-xr-x  1 josh root          0 1980-01-04 15:33 PE                                                                                                
-rwxr-xr-x  1 josh root          0 1980-01-04 15:33 PE                                                                                                
-rwxr-xr-x  1 josh root          0 1980-01-04 15:33 PE                                                                                                
-rwxr-xr-x  1 josh root  247078670 1980-07-24 01:00                                                                                                   
-rwxr-xr-x  1 josh root  247078670 1980-07-24 01:00                                                                                                   
-rwxr-xr-x  1 josh root  247078670 1980-07-24 01:00                                                                                                   
-rwxr-xr-x  1 josh root  247078670 1980-07-24 01:00                                                                                                   
-rwxr-xr-x  1 josh root  247078670 1980-07-24 01:00                                                                                                   
-rwxr-xr-x  1 josh root       7204 1981-01-20 00:00 &#9571;&#9524;?.`?
-rwxr-xr-x  1 josh root       4096 1996-01-01 00:00 oc
-rwxr-xr-x  1 josh root       4096 1996-01-01 00:00 oc
-rwxr-xr-x  1 josh root       4096 1996-01-01 00:00 oc
-rwxr-xr-x  1 josh root       4096 1996-01-01 00:00 oc
-rwxr-xr-x  1 josh root       4096 1996-01-01 00:00 oc
-rwxr-xr-x  1 josh root 2080899072 1998-09-09 01:00 &#9552;!Th.PE
-rwxr-xr-x  1 josh root 2080899072 1998-09-09 01:00 &#9552;!Th.PE
-rwxr-xr-x  1 josh root 2080899072 1998-09-09 01:00 &#9552;!Th.PE
-rwxr-xr-x  1 josh root 2080899072 1998-09-09 01:00 &#9552;!Th.PE
-rwxr-xr-x  1 josh root 2080899072 1998-09-09 01:00 &#9552;!Th.PE
-rwxr-xr-x  1 josh root      11108 2004-01-01 00:00 ƒ".?
-rwxr-xr-x  1 josh root   77656528 2004-05-01 01:00 ?.ç&#9580;?
drwx------  3 josh root      16384 2009-11-14 09:49 My Documents
drwx------ 34 josh root      16384 2009-11-14 21:12 Recover
drwx------  3 josh root      16384 2009-11-15 22:55 System Volume Information
-rwxr-xr-x  1 josh root       1364 2010-06-21 01:37 ÿ&#8734;?.h!
-rwxr-xr-x  1 josh root       1364 2010-06-21 01:37 Å.&#934;
-rwxr-xr-x  1 josh root       1364 2010-06-21 01:37 à=?.?ñ
-rwxr-xr-x  1 josh root       1364 2010-06-21 01:37 ƒ;?.?&#9558;
-rwxr-xr-x  1 josh root       2208 2012-01-01 00:00 èñ.?
-rwxr-xr-x  1 josh root          0 2020-01-01 00:37 d+.&#9554;<@
-rwxr-xr-x  1 josh root          0 2020-01-01 00:37 &#9604;).&#9554;<@
-r-xr-xr-x  1 josh root        116 2038-01-14 00:00 ïu?à÷wï}.?u&#9563;
-rwxr-xr-x  1 josh root        116 2038-01-14 00:00 ?.&#9557;

is this what you wanted?

---

### Post by prem1er on 2009-12-07
I meant the on the directory where it is mounted, not the contents of the directory. So if it is mounted at /mount/flash, go into /mount and then run the command.

---

### Post by netopalis45 on 2009-12-07
total 40
drwx------ 11 josh root 16384 1969-12-31 19:00 0A24-0160_
drwxr-xr-x  2 root root  4096 2009-05-14 09:20 cdrom2
drwxr-xr-x  2 root root  4096 2009-05-14 09:20 cdrom1
drwxr-xr-x  2 root root  4096 2009-05-14 09:20 cdrom0
lrwxrwxrwx  1 root root     6 2009-05-14 09:20 cdrom -> cdrom0
drwx------  2 root root  4096 2009-11-07 23:51 EF6C-A031
drwxr-xr-x  2 root root  4096 2009-11-09 08:09 sdd1
drwx------  2 root root  4096 2009-11-29 19:01 0A24-0160

was this one it?

---

### Post by netopalis45 on 2009-12-14
still needing help here. is there anybody out there who knows what is going on here?

---

### Post by Dennis N on 2009-12-14
> **netopalis45 said:**
> i accidently formatted my external usb hard drive. before i did this i could read and write to/from the drive with no problem. after i formatted it i can no longer write to the drive even though i have changed the owner to me.
i am running karmic and the external drive is formatted fat32. 
can anyone help me with this?

You say you changed the owner. Did you also change the read/write permissions for yourself (as owner)? After the formatting, they might not be correct.

---

### Post by netopalis45 on 2009-12-14
How would I go about doing that?

---

### Post by Dennis N on 2009-12-14
> **netopalis45 said:**
> How would I go about doing that?

1) plug in drive so that it is mounted.
2) if your drive shows up at /media/drivename, use nautilus file browser to navigate to and open that folder. Use icon view, and right click in some of the white space in the window and click on 'properties'.
3) in the properties window (should say 'drivename' properties at the top), select the 'permissions' tab.

You said you changed the owner so you should be owner.
Folder access for owner should say 'create and delete files'. (If not, use the drop down box to change it).
Set file access for owner to 'read and write'

For the group
You can change the group and set folder and file access for the group.

When done, click on 'apply permissions to enclosed files'.

---

### Post by netopalis45 on 2009-12-14
just to clarify, how long should this take? the setting permissions part. it seems to be taking forever

---

### Post by Dennis N on 2009-12-14
As I recall, its pretty quick. I don't think you get any notification when its done. Just close the properties window and see if you have access to the files.

---

### Post by netopalis45 on 2009-12-14
well mine is taking a long time. and for some reason it didnt work. and idea as to why that happened or another way of doing that (possibly with terminal)?

---

### Post by PseudoLemon on 2009-12-14
This is a bit drastic, but you could nuke the drive. It's part of the 'dd' command but I forget which part. You should only do this if you have tried everything else.

---

### Post by Dennis N on 2009-12-14
Try unplugging (be sure to unmount) and plug the drive in again.

**EDIT** I'll add this before I leave:

Another thread about same or similar problem which has some additional ideas:

[http://ubuntuforums.org/showthread.php?t=1329975](http://ubuntuforums.org/showthread.php?t=1329975)

Since you have fomatted FAT, I checked a FAT external drive I have:

Permissions tab on my FAT hard drive folder by default:

```
Owner
Folder Access: read and write
File Access: ---

Group is Root
Folder Access: none
File Access: ---

Others
Folder Access: none
File Access: ---

```

A post on the other thread suggests using sudo (See post 4). You would need that if you are not shown as the owner. 

In terminal:

```
gksudo nautilus
```


If no solutions appear, you could delete all partitions with gparted and try again. 

Good Luck.

---

### Post by netopalis45 on 2009-12-16
the permissions on mine look the same as yours but i still cant write to the drive. i cant change those permissions either and i have too much data to move off of the drive so it can be formatted. is there any way i could possibly change the permissions in windows so i can write to it?

---

### Post by netopalis45 on 2009-12-27
ok. so i ended up having to reformat the drive as ntfs and it works fine now. what i need now is a program that will restore all or some of the files i lost in the original accidental format. i know there is a windows program that will do this but it wont restore large files and cant find a lot of other types of files. i would like something open source and easy to use. any ideas?

---

