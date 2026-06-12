---
title: "Access media partition"
date: 2011-08-02
forum: General Help
---

### Post by granul on 2011-08-02
Hi!

I have a partition on my hard drive sda3, that I use to make backup of files, I have to loggin as root evverytime I want to copy a file on that partition. What can I do to make that media accesible?

Thank you

---

### Post by dcollier on 2011-08-02
Is the drive mounted? if so it sounds as if you mounted the drive with root privileges.  Check your permissions

---

### Post by granul on 2011-08-02
> **dcollier said:**
> Is the drive mounted? if so it sounds as if you mounted the drive with root privileges.  Check your permissions

How do I do this, if I log with root, and I click on properties/permissions of the media it say permission of the sd3 cannot be determined. Sorry abour my English, my Ubuntu is in french.

---

### Post by dcollier on 2011-08-02
open a shell, enter cd /media.  this is the directory were you disks are located then enter the ls -a command to see what the permissions are.  you can change the permissions with the chmod command

---

### Post by granul on 2011-08-02
> **dcollier said:**
> open a shell, enter cd /media.  this is the directory were you disks are located then enter the ls -a command to see what the permissions are.  you can change the permissions with the chmod command

here is what I got: .  ..  cdrom  data  sda3, with ls -a

---

### Post by dcollier on 2011-08-02
ok im sorry about that, it should have been ls -l to list the permission. also enter mount /media/sda3

---

### Post by granul on 2011-08-02
> **dcollier said:**
> ok im sorry about that, it should have been ls -l to list the permission. also enter mount /media/sda3

Here is what I get:
ls -l
total 24
drwxr-xr-x 2 root root  4096 2011-06-12 12:52 cdrom
drwxr-xr-x 2 root root  4096 2011-08-02 14:28 data
drwxr-xr-x 8 root root 16384 1969-12-31 19:00 sda3

mount /media/sda3[/QUOTE]
mount: ne peut repérer /media/sda3[/QUOTE] dans /etc/fstab ou /etc/mtab

---

### Post by dcollier on 2011-08-03
as you can see the disk is owned by the user root and the group root.  You should be able to take owner ship of the partition with the chown command.

---

### Post by dcollier on 2011-08-03
your permissions are also set as 755, meaning that only the owner can write to the partition 755 is the same as rwxr-xr-x...  The r is for read the w is for write and the x is for execute.  the - means no write access...

---

### Post by granul on 2011-08-03
Hi!

Sorry about my ignorance, I'm not an expert with Linux. How do I take owner ship of the partition with the chown command.

I have 3 choices with this command :
chown root /u        
chown root:staff /u  
chown -hR root /u    

Thank you for the help

---

### Post by dcollier on 2011-08-03
try this...   man chown

---

### Post by dcollier on 2011-08-03
what is your user name?  it will be the same name for the group...  example your user name is test and you want to take ownership of /media/sda3... so enter chown test:test /media/sda3

---

### Post by granul on 2011-08-03
> **dcollier said:**
> try this...   man chown

I get an emssage that tells me permission denied
chown daniel:daniel /media/sda3

---

### Post by nothingspecial on 2011-08-03
Is the disk mounted as sda3?

Is it a linux file system?

If so

```
sudo chown $USER:$USER /media/sda3
```

if not, what is the file system and mountpoint?

---

### Post by granul on 2011-08-03
I tried this : sudo chown $USER:$USER /media/sda3, permission denied and I also tried this line: sudo chown $daniel:$daniel /media/sda3, i got no message but it still does not work. 

The partition sd3 is a is a fat32, maybe I should format with GParted?

---

### Post by nothingspecial on 2011-08-03
Fat is not a native linux file system and as such will not support linux file permissions unless given at mounting.

If you intend using this partition only with linux I would format it ext4.

I can show you how to mount it with permissions but if you can, just format it.

---

### Post by nothingspecial on 2011-08-03
Oh and you don't need the $ before daniel, the $ signifies a variable, the variable $USER expands to the current user.

So if you are logged in as daniel then $USER means daniel, however if you are logged in as michele $USER will expand to michele.

I used $USER because I didn't know your user name.

---

### Post by granul on 2011-08-03
I use the whole disk for linux, so my linux syst is already ext4, so should I format the sd3 on ext3 or ?

---

### Post by nothingspecial on 2011-08-03
You can format it ext3 if you like, but since ext4 is supposed to be an improvement over ext3 I'd use ext4.

---

### Post by dcollier on 2011-08-03
ok that makes sense.. your not using a linux partition...  shame on you... :)

---

### Post by nothingspecial on 2011-08-03
By the way, since you have to use sudo to partition it, after you have root will still own it so you will still have to do
```

sudo chown -R daniel:daniel /media/whatever
```

---

### Post by granul on 2011-08-03
Hi!

sudo chown -R daniel:daniel /media/sda3 - permission denied

What i don't understand is that if log as root there is no problem, I can copy on the sd3, it is not working as user.

---

### Post by nothingspecial on 2011-08-03
I have to go, are you sure /media/sda3 is the mountpoint? Not /media/somethingelse?

Check back later.

---

### Post by granul on 2011-08-03
Hi!

I reformatted the partition to /dev/sda2 ext4, so it is mounted as /media1/Backup, the problem is still there.

Thank you

---

### Post by granul on 2011-08-03
> **granul said:**
> Hi!

I reformatted the partition to /dev/sda2 ext4, so it is mounted as /media1/Backup, the problem is still there.

Thank you

after I reformatted, i have to boot in safemod, cannot boot ubuntu anymore, get this kind of error cannot read /etc/udev/rules.d/z80_user.rules

---

### Post by nothingspecial on 2011-08-03
> **granul said:**
> after I reformatted, i have to boot in safemod, cannot boot ubuntu anymore, get this kind of error cannot read /etc/udev/rules.d/z80_user.rules

](*,) What????!??!

That shouldn't have happened.


Which release are you using.

---

### Post by granul on 2011-08-03
I am using Zorin 5 wich is a linux Ubuntu base, if i press the S key when I see the error i can boot normally

---

### Post by granul on 2011-08-03
> **granul said:**
> I am using Zorin 5 wich is a linux Ubuntu base, if i press the S key when I see the error i can boot normally

I'm thinking about installing Ubuntu 11.04 instead of Zorin

---

### Post by nothingspecial on 2011-08-03
Well I know nothing of zorin, but I remember that error. Is it based on 10.04?

Anyhow, linux is linux. I don't see why you cannot change the permissions on a mounted native linux file system

---

### Post by nothingspecial on 2011-08-03
But when I visited their website

> This website is currently not available.

We’re sorry, this site is unavailable, because it has used up its monthly bandwidth. Please try back another time.

If you are the site owner, you can signup for additional bandwidth by logging into your Webs.com account.


Doesn't sound promising :-k

---

### Post by granul on 2011-08-03
[QUOTE=nothingspecial;11115234]But when I visited their website

this web site : [http://www.zorin-os.com/](http://www.zorin-os.com/), i just went ans it's ok

---

### Post by granul on 2011-08-03
Finanely I install ubuntu 11.04, I will chexk later on if the problem persist

---

### Post by granul on 2011-08-03
> **granul said:**
> Finanely I install ubuntu 11.04, I will chexk later on if the problem persist

The problem seems to be resolved, I can copy or write on the media.

---

### Post by dcollier on 2011-08-09
Could we get you to change the status of this thread to SOLVED :)

---

