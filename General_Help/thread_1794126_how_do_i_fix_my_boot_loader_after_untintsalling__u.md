---
title: "how do i fix my boot loader after untintsalling  ubuntu?"
date: 2011-06-30
forum: General Help
---

### Post by ralph1221 on 2011-06-30
Ok I uninstalled ubuntu 11.04 from one hard drive and along with it went grub loader. So now I'm left with no bootloader for windows xp on a seperate harddrive. I tried repair with a windows cd and couldn't find C:\windows All there was was
 
C:\MininNT
 C:\I386
 D:\windows

 I believe D:\windows is not my local C:\ because my D drive is my dvd drive! What is c:\minint and C:\i386? What happened to C:\windows?

---

### Post by drs305 on 2011-06-30
ralph1221,

Welcome to the Ubuntu Forums. I've moved your post to the General Help forum, where I'm sure someone will assist you. 

Almost all the Ubuntu forums are support forums which help users resolve issues. The 'Resolution Center' is used for resolving non-support issues between users and the forum staff, usually due to violations of the Forum Code of Conduct.  You probably want to avoid being in that thread...  :-)

---

### Post by ralph1221 on 2011-06-30
> **drs305 said:**
> ralph1221,

Welcome to the Ubuntu Forums. I've moved your post to the General Help forum, where I'm sure someone will assist you. 

Almost all the Ubuntu forums are support forums which help users resolve issues. The 'Resolution Center' is used for resolving non-support issues between users and the forum staff, usually due to violations of the Forum Code of Conduct.  You probably want to avoid being in that thread...  :-)

Ok where do I access general help forum?

---

### Post by drs305 on 2011-06-30
> **ralph1221 said:**
> Ok where do I access general help forum?

You are there! I moved the thread.

I'm no longer competent in Windows, but I'd investigate D:\windows. Drive letters can change.

---

### Post by akand074 on 2011-06-30
Have you tried just entering the command prompt from a Windows XP cd and type

```
fixmbr
```

---

### Post by ralph1221 on 2011-07-01
> **akand074 said:**
> Have you tried just entering the command prompt from a Windows XP cd and type

```
fixmbr
```

Well the thing with unning the command is I don't know which drive or partition to pick
I have 3 options like I wrote in my original post
After that yes. I could write fixmbr but the thing is I don't know which to choose

---

### Post by Rubi1200 on 2011-07-01
Hi and welcome to the forums ralph1221 :)

I suggest you get hold of an Ubuntu CD and boot the computer with it.

Then do the following so we can get a better idea of what is where on your system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by akand074 on 2011-07-01
> **ralph1221 said:**
> Well the thing with unning the command is I don't know which drive or partition to pick
I have 3 options like I wrote in my original post
After that yes. I could write fixmbr but the thing is I don't know which to choose

Yeah do as the the post above said. But I think even in the Windows disc the partition that is selected as the boot partition is flagged (has a * beside it or something to let you know). It's most likely C:/, but the bootinfo script from above will tell us everything we need to know.

---

### Post by Dr. C on 2011-07-02
My first suggestion here is to change the hard drive boot order in the bios to make the hard drive with Windows XP boot ahead of all other hard drives.

---

