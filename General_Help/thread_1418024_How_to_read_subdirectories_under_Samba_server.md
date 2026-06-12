---
title: "How to read subdirectories under Samba server?"
date: 2010-02-28
forum: General Help
---

### Post by blair on 2010-02-28
Would appreciate some assistance. Setting up a simple Samba server share on Ubuntu 9.04 so that my MP3 library is accessible to other PCs on the LAN, including Windows PCs. The /mp3 folder has a series of subdirectories for artists and albums, e.g. /mp3/beatles/abbey_road, /mp3/clapton/slowhand, etc. 

I set path = /mp3 and Windows clients can see the list of subdirectories (i.e. beatles, clapton, etc.) however when a Windows user clicks on the subdirectory, the contents are blank, i.e. none of the mp3 files in the folder are displayed. I can place a world readable mp3 file in the /mp3 directory and it is listed and readable with no problem. 

I have all the mp3 files and directories set to world-readable (chmod -R o+r /mp3) and confirmed that file permissions are correctly set.

How do I make Samba recursively allow read access to all the subdirectories under /mp3? I do not believe this is a file permissions problem, but rather a samba config problem.  I have researched this a bit and all tips either say create another share per subdirectory (infeasible in this case with 100+ subdirectories) or discuss the use of samba ACLs to force permissions when writing files to the samba share. 

I basically want to specify a read-only share at a point in my file system, then provide unlimited read access to every subdirectory and sub-subdirectory under that point. I can create the share and access the share no problem, but can't read anything below the specific directory listed as the share point. 

Thanks for the assistance.

---

### Post by warp99 on 2010-02-28
What are the permissions on just the subdirectories? Can you post a sample of the output 'ls -ls` on the subdirectories?

---

### Post by blair on 2010-02-28
here is the smb.conf:

[global]
workgroup = WORKGROUP
netbios name = Music
security = share

[data]
comment = Ubuntu
path = /media/network_drive/mp3
read only = yes
guest ok = yes
guest only = yes
browseable = yes
guest account = anonread

This smb.conf provides a user anonymous read access. The Linux user account used once on the box is defined by the anonread user account. 

Here is a ls -l extract from the /mp3 folder:

drwx---r--  2 blair blair    4096 2010-02-28 14:37 acdc
drwx------  7 blair blair    4096 2010-02-28 00:16 AC_DC

The AC_DC shows default privileges for the subdirectories because they were created by me. If the Win client clicks on this link, they get access denied because it is not world readable and can't even open the directory. Fine and understood; they don't have read privileges

I created a new test "acdc" subdirectory for test purposes and set its privileges using chmod o+r so it should be world readable. This is shown in the ls -l listing above. When the Win client clicks on this link, the directory opens fine but appears empty even though there are files in it. All the mp3 files in /acdc are also set to world readable as shown: 

-rwx---r-- 1 blair blair 5318163 2008-04-23 12:35 01 - Highway To Hell.mp3
-rwx---r-- 1 blair blair 5428404 2008-04-23 12:36 02 - The Girl's Got Rhythm.mp3
-rwx---r-- 1 blair blair 8205449 2008-04-23 12:38 03 - Walk All Over You.mp3


I also tried changing file permissions so they are owned by the anonread user account accessing the share:

-rwx---r-- 1 anonread ftp 5318163 2008-04-23 12:35 01 - Highway To Hell.mp3
-rwx---r-- 1 anonread ftp 5428404 2008-04-23 12:36 02 - The Girl's Got Rhythm.mp3
-rwx---r-- 1 anonread ftp 8205449 2008-04-23 12:38 03 - Walk All Over You.mp3


I also tried turning all the permissions on:

-rwxrwxrwx 1 anonread ftp 5318163 2008-04-23 12:35 01 - Highway To Hell.mp3
-rwxrwxrwx 1 anonread ftp 5428404 2008-04-23 12:36 02 - The Girl's Got Rhythm.mp3
-rwxrwxrwx 1 anonread ftp 8205449 2008-04-23 12:38 03 - Walk All Over You.mp3
Same result: Files are not displayed when the user opens the folder. 

Still nothing. I think the problem is with Samba not making accessible things below the shared folder, not the permissions for individual files.

Everything I'm reading is related to creating files, not accessing files already there. Appreciate any assistance.

---

### Post by warp99 on 2010-02-28
Those permissions are not going to work at all. I would do the following:

Change into the mp3 directory:
```
cd /media/network_drive/mp3
```

and run the following code:
```
find -type d -print0 |xargs -0 chmod 755
```
This will change the directories to the proper permissions. Then in the same directory run this string:
```
find -type f -print0 |xargs -0 chmod 644
```
This will change the files to the proper permissions. Your permissions should look like this on the directories:
```
/share/music$ ls -ls
total 8
4 drwxr-xr-x 2 warp99 warp99 4096 2010-02-28 13:58 INXS-The_Greatest_Hits
4 drwxr-xr-x 2 warp99 warp99 4096 2010-02-28 13:59 The_Jimi_Hendrix_Experience_Are You Experienced
```
and on the files:
```
/share/music/INXS-The_Greatest_Hits$ ls -ls
total 118052
 6448 -rw-r--r-- 1 warp99 warp99  6602680 2010-02-28 13:58 01-The_One_Thing.mp3
10108 -rw-r--r-- 1 warp99 warp99 10349266 2010-02-28 13:58 02-Original_Sin.mp3
 6720 -rw-r--r-- 1 warp99 warp99  6881040 2010-02-28 13:58 03-What_You_Need.mp3
 7136 -rw-r--r-- 1 warp99 warp99  7305687 2010-02-28 13:58 04-Listen_Like_Thieves.mp3
 5924 -rw-r--r-- 1 warp99 warp99  6064348 2010-02-28 13:58 05-Shine_Like_It_Does.mp3
 5744 -rw-r--r-- 1 warp99 warp99  5879610 2010-02-28 13:58 06-Need_You_Tonight.mp3
 9752 -rw-r--r-- 1 warp99 warp99  9985641 2010-02-28 13:58 07-Devil_Inside.mp3
 6916 -rw-r--r-- 1 warp99 warp99  7079153 2010-02-28 13:58 08-New_Sensation.mp3
 7968 -rw-r--r-- 1 warp99 warp99  8159160 2010-02-28 13:58 09-Never_Tear_Us_Apart.mp3
 7300 -rw-r--r-- 1 warp99 warp99  7473707 2010-02-28 13:58 10-Suicide_Blonde.mp3
 7744 -rw-r--r-- 1 warp99 warp99  7929282 2010-02-28 13:58 11-Disappear.mp3
 9324 -rw-r--r-- 1 warp99 warp99  9545112 2010-02-28 13:58 12-The_Stairs.mp3
 6336 -rw-r--r-- 1 warp99 warp99  6486487 2010-02-28 13:58 13-Heaven_Sent.mp3
 6016 -rw-r--r-- 1 warp99 warp99  6158807 2010-02-28 13:58 14-Beautiful_Girl.mp3
 7400 -rw-r--r-- 1 warp99 warp99  7576525 2010-02-28 13:58 15-The_Strangest_Party_(These_Are_the_Times).mp3
 7216 -rw-r--r-- 1 warp99 warp99  7387607 2010-02-28 13:58 16-Deliver_Me.mp3

```

---

### Post by warp99 on 2010-02-28
Your smb.cmf should look like this:

```

[global]
workgroup = WORKGROUP
netbios name = Music
security = share

[data]
path = /media/network_drive/mp3
guest ok = yes
read only = yes
valid users = anonread
available = yes
browsable = yes
public = yes
writable = no

```

Edit: Now you only need anonread group ownership, but not anonread user ownership.

---

### Post by blair on 2010-02-28
The directory and file chmod commands worked perfectly. Problem solved. THANK YOU !

Unfortunately, the smb.conf changes broke the share completely. I rolled back to my original smb.conf and everything is fine. I am new to samba and will read up on the parameters you recommend I use.  Thank you very much for your assistance.

---

### Post by warp99 on 2010-02-28
You can also do it this way:

[http://www.debuntu.org/guest-file-sharing-with-samba](http://www.debuntu.org/guest-file-sharing-with-samba)

---

