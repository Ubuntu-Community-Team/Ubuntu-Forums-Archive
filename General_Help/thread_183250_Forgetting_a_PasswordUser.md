---
title: "Forgetting a Password/User"
date: 2006-05-27
forum: General Help
---

### Post by thelabyrinthworm on 2006-05-27
Okay, I bought a PC at a yardsale today and it has ubuntu on it, and I thought what a perfect chance to learn about linux. I boot it up and obviously there was a user/password, that I did not know.

So I came to these forums, which offered me three methods that unfortunetaly aren't doing much.

I tried booting into recovery mode - which asks me for root password, and then I can't type anything, all i can do is boot into the interface

I downloaded and booted into the rescue mode from the install disk, and i get to the shell prompt and do the new user - type in a new user account name, then it will not let me type in a password, and when i just hit enter twice it tells me that's all invalid to do (obviously), so I am stuck on what to do. 

Any help? Thanks Guys!

](*,)

---

### Post by oldmanstan on 2006-05-27
honestly your best bet would be to just reformat the HD and do a clean install of ubuntu. if the person had it set up with ubuntu already chances are it shouldn't be hard to reinstall it.

---

### Post by thelabyrinthworm on 2006-05-27
Hey,

is that my only option? it just seems weird that i can't do any of that. if i were to reformat though, do i just do the regular setup of the disk, there are three options
erase entire disk: IDE master (hda)
Eraste entire disk and use LVM: IDE master 
Manually edit partition table

is there a way to partition without deleting the files?

(and is that my only option?)

---

### Post by seth0x2b on 2006-05-27
I don't know about how Ubuntu handles it's passwd file(if it allows passwordless logins).
On older distros (mandrake, redhat) you could use a live cd, mount the harddrive RW, open /etc/passwd and where it says
```
"root:x:0:0:root:/root:/bin/bash"
```
just erase the x to leave the account passwordless.

Again, I am not sure that Ubuntu allows you to use passwordless logins.
Cheers and welcome to Linux :)

---

### Post by Steven_B on 2006-05-27
> is there a way to partition without deleting the files?
Yes.  Select "Manually edit partition table".  There you can create a new partition, and install Ubuntu onto it.  If you don't reformat the current partition, the new install should be able to see the other partition and it's files.
That said, I wouldn't think that saving the old files is that important, since you will hopefully have a fresh, working install.

---

### Post by glinsvad on 2006-05-27
Fire up a LiveCD and delete the password files... never tried it myself, but I'm pretty sure that the root password is stored in binary files somewhere on the harddrive.

I'm guessing here, but try deleting the following files (BACKUP FIRST!!!):
/etc/passwd
/etc/passwd-
/ect/shadow
/ect/shadow-

Rebooting might glitch, but if you'r lucky there just might be no root password anymore...

EDIT: Hmm, just noticed seth0x2b's answer - let's go with his idea first :D

---

### Post by seth0x2b on 2006-05-27
If there's an x instead of a(hashed) password in "/etc/passwd", that means that the system uses shadow passwords.Those are stored in "/etc/shadow"
I don't think he'll be able to login if he deletes the passwordfiles

Cheers

---

### Post by thelabyrinthworm on 2006-05-27
okay i need to make a LIVE CD first, i had just made an ISO of the install cd, i assume that makes a difference and will try seth's way.

i tried creating a new partition in manual, but it doesn't look like i can , is there a limit to partitions or maybe im just missing something.

---

### Post by AlexandreP on 2006-05-27
[QUOTE=thelabyrinthworm]I downloaded and booted into the rescue mode from the install disk, and i get to the shell prompt and do the new user - type in a new user account name, then it will not let me type in a password, and when i just hit enter twice it tells me that's all invalid to do (obviously), so I am stuck on what to do. [/QUOTE]Password isn't not shown when typed.  It is entered, but no asterisks or dots or anything is shown.  It's normal if you don't see anything on your screen when you type a password.

For the partitions, there is a limit.  On a hard disk, you can only create up to 4 primary partitions.  But, to bypass this limit, you can create an extended partition that would contain logicial partitions, which are almost like primary partitions.
For example, let's say you want to have 5 partitions on your hard disk.  You can create 3 primary partitions, and 1 extended partition which would contain 2 logical partitions.

If you want to keep the datas on the disk, you can try this:
- Using a liveCD, open a terminal.
- In this terminal, type: ```
$ sudo -s
# mkdir /media/root
# mount /dev/hda1 /media/root
# chroot /media/root
# adduser your_login
Password:
Again:
# adduser your_login admin
```
(assuming /dev/hda1 [line 3] is the root partition and your_login [line 5 and 6] is your desired login name)
- Then, restart your computer and try to log in using *your_login* as your login.  You should be in the admin group, meaning you would be able to use sudo.
- If it all works, disable the root account by typing this in a terminal: ```
$ sudo passwd -l root
```

---

### Post by thelabyrinthworm on 2006-05-27
oh thanks everyone i got it, i didn't realize passwords were invisible so i went to sudo -s and did the password for the drive there, thanks for all your help :)

now to figure out linux haha, (first time user)

---

### Post by thelabyrinthworm on 2006-05-27
okay, so i am getting used to what is going on, and i am trying to get online, which isn't happening, so i assume i have to do something, i plugged in my ethernet cord, hoping it would just work, but it doesnt. haha. anyhelp:?

---

### Post by thelabyrinthworm on 2006-05-27
nvm got it to work, thanks again guys!

---

### Post by JayBachatero on 2006-05-27
Thanks AlexanderP.  That worked perfectly for me.  Damn OEM didn't create the user I specified.

---

### Post by AlexandreP on 2006-05-27
You're welcome :)

---

