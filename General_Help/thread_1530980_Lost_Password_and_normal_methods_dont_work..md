---
title: "Lost Password and normal methods dont work."
date: 2010-07-14
forum: General Help
---

### Post by sasrail on 2010-07-14
So I have forgotten my password, like a moron, and have been trying to reset/recover it.
I have found the plethora of sites giving instructions on how to reset my password, such as psychocats.net
So have gotten into the root shell and this is what I type.
ls /home
(gives me the name of my account)
passwd (my account here)
unknown user (account name here)

I have also tried doing the editing the boot kernel.
I add this: rw init=/bin/bash[COLOR=Black][COLOR=#FF0000]*[FONT=Verdana][/FONT]*[/COLOR][/COLOR]
Once I restart I get the root@(none) command prompt. Then I type passwd (username here) and get back ' unknown user


Any help would be greatly appreciated. Thanks!

I am running ubuntu 9.04 on an Acer netbook. It is the only os on the hd as well.

---

### Post by K.J. on 2010-07-14
Try using the UID instead of the username. I believe the first account created is 1 (with root being 0).

---

### Post by sasrail on 2010-07-14
So I would just use the number 1 in place of the username in the commands or do I need to do something special to make it work?

---

### Post by sisco311 on 2010-07-14
> **sasrail said:**
> So I would just use the number 1 in place of the username in the commands or do I need to do something special to make it work?

Nope, you have to use the username. 

To get the list of users, run:
```
awk -F: '{if ($3 > 999) print $1}' /etc/passwd
```

NOTE: Linux is case sensitive, UserName & username are two different users.

---

### Post by nothingspecial on 2010-07-14
> **K.J. said:**
> Try using the UID instead of the username. I believe the first account created is 1 (with root being 0).

It`s 1000

---

### Post by sasrail on 2010-07-14
> **sisco311 said:**
> Nope, you have to use the username. 

To get the list of users, run:
```
awk -F: '{if ($3 > 999) print $1}' /etc/passwd
```NOTE: Linux is case sensitive, UserName & username are two different users.


I tried that and got back cannot open /ect/passwd no such file or directory

---

### Post by sisco311 on 2010-07-14
> **sasrail said:**
> I tried that and got back cannot open /ect/passwd no such file or directory

/etc/passwd file stores essential information, which is required during login i.e. user account information.

It contains a list of the system's accounts, giving for each account some useful information. 

There should be a backup of /etc/passwd named /etc/passwd-, copy this file and change its name to /etc/passwd:
```
cp /etc/passwd- /etc/passwd
```

---

### Post by sasrail on 2010-07-14
How would I find it and do that? I am newish to ubuntu so all the instruction you can give is helpful.

---

### Post by sisco311 on 2010-07-14
First make sure that the file doesn't exist:
```
ls /etc/passwd
```

Then check out if the backup file exists:
```
ls /etc/passwd-
```

EDIT: the ls command lists a file or directory and prints an error message if the file dos not exist.

  
If /etc/passwd is missing and /etc/passwd- is prsent, then copy /etc/passwd- to /etc/passwd:
```
cp /etc/passwd- /etc/passwd
```

---

### Post by sasrail on 2010-07-14
Says neither exist...I assume that means I am screwed.

---

### Post by Penguin Guy on 2010-07-14
First you'll need to chroot into your old system:

[LIST=1]
[*]Boot into the live CD
[*]Find which partition the real system is installed on with [FONT="Courier New"]sudo fdisk -l[/FONT] (post the result here if unsure)
[*]Make a directory to mount the chroot at with [FONT="Courier New"]sudo mkdir -p /mnt/computer[/FONT]
[*]Change to that directory with [FONT="Courier New"]cd /mnt/computer/[/FONT]
[*]Mount the system with [FONT="Courier New"]sudo mount /dev/sd**??** /mnt/computer/[/FONT]
[*]Change root with [FONT="Courier New"]sudo chroot /mnt/computer/[/FONT]
[/LIST]

Then run these commands (you should automatically be root):
```

$ users
bob bob
$ passwd bob
[sudo] password for bob: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

```
(obviously you replace [FONT="Courier New"]bob[/FONT] with your username)

---

### Post by sisco311 on 2010-07-14
> **sasrail said:**
> Says neither exist...I assume that means I am screwed.

You may have another backup in the /var/backups/ directory, run:

```
ls /var/backups
```to list the files in the directory. The name of the backup should be something like passwd.bak.

```
cp /var/backups/passwd.bak /etc/passwd
```
You may have to change the permission of the file:
```
chmod 0644 /etc/passwd
```

EDIT: Do you have any files in /etc?

---

### Post by sasrail on 2010-07-14
Its saying there is no /etc 

I also tried the cd approach but each time it says crc error -- System halted

---

### Post by sasrail on 2010-07-14
Well I figure that some how my install is fairly messed up. So I went and tried to reinstall. My disk works in that it boots to the install menu, but when I select install it just sits there. I can still move the selector around as well. What is even more unusual is windows installs just fine.

---

