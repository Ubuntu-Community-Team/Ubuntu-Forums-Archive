---
title: "&quot;Failed  to mount Windows share&quot;"
date: 2010-08-05
forum: General Help
---

### Post by FA5878 on 2010-08-05
Hi

In my house we have an old PC in the living room connected to the TV (as a communal computer) which we also watch films etc off (running Ubuntu 9.10).

My personal PC runs Ubuntu 10.04 and I have a wide collection of media which I shared across the network allowing us to watch my media.

There was a powercut a few days ago which knocked everything out. Whilst none of the files are damaged (I can still watch them on my computer) I can no longer access the folder across the network.

The files in question are on a secondary internal HDD with only an ext4 filesystem.

I have tried formatting the HDD and replacing all the files with no joy.

I can still access anything I share from my primary HDD.

When attempting to access my secondary HDD across the network I get the following error:

"Unable to mount location. Failed to mount Windows share."

Can anybody shed some light on what is going on here please? I would very much appreciate it.

---

### Post by Morbius1 on 2010-08-05
Post the output of the following commands so we can see what method of Samba you're using and how the shares are configured:
```
net usershare info
sudo net usershare info
testparm -s
```

---

### Post by FA5878 on 2010-08-05
From communal PC (the one I'm mounting to)

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
server string = %h server (Samba, Ubuntu)
map to guest = Bad User
obey pam restrictions = Yes
pam password change = Yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
unix password sync = Yes
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
dns proxy = No
usershare allow guests = Yes
panic action = /usr/share/samba/panic-action %d

[printers]
comment = All Printers
path = /var/spool/samba
create mask = 0700
printable = Yes
browseable = No
browsable = No

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
```

From my PC (the one with the drive I'm trying to mount)

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No                                                                                                                                                               
        browsable = No                                                                                                                                                                

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
```

---

### Post by Morbius1 on 2010-08-05
You don't have any classic shares defined so I'm guessing you used Nautilus-share. Did these commands produce no output?

```
net usershare info
```

```
sudo net usershare info
```

---

### Post by FA5878 on 2010-08-05
Yeah no output at all, I assumed that was meant to happen (I'm fairly novice in this area)

---

### Post by Morbius1 on 2010-08-05
Not that this is unusual for me but I'm confused.

This is a Samba error:
>  "Unable to mount location. Failed to mount Windows share."But testparm and usershare says you haven't created anything to share.

Let's start at the beginning. How are you sharing your folders?

---

### Post by FA5878 on 2010-08-05
Just right-clicking the folders in question.

Right click
Choose 'Properties'
Go to the 'Share' tab
Tick 'Share this folder' and 'Guest access'

4 out of 5 folders are accessible with no problem.

The one that gives me the error is on a separate internal HDD and has only been giving an error message since a premature poweroff a couple of days ago.

---

### Post by Morbius1 on 2010-08-05
> Right click
Choose 'Properties'
Go to the 'Share' tab
Tick 'Share this folder' and 'Guest access'
That's Nautilus-share.

net usershare info should have given you this type of output on that box:
> [share-name]
path=/path-to-shared-folder
comment=
usershare_acl=Everyone:F,
guest_ok=y


Let's try it this way, Post the output of this command:
```
ls -al /var/lib/samba/usershares
```

---

### Post by FA5878 on 2010-08-05
```
total 40
drwxrwx--T 2 root sambashare 4096 2010-08-05 17:30 .
drwxr-xr-x 5 root root       4096 2010-06-07 14:10 ..
-rw-r--r-- 1 liam liam        104 2010-07-31 16:16 fez movies
-rw-r--r-- 1 liam liam        115 2010-07-31 16:17 fez putbox
-rw-r--r-- 1 liam liam         84 2010-08-01 18:56 fez's videos
-rw-r--r-- 1 liam liam         77 2010-07-05 19:05 liams music
-rw-r--r-- 1 liam liam         78 2010-07-05 19:04 liams videos
-rw-r--r-- 1 liam liam         85 2010-08-05 16:11 tv shows
-rw-r--r-- 1 liam liam         80 2010-08-05 17:04 tv shows 2
```
"tv shows" is the one not working

---

### Post by Morbius1 on 2010-08-05
I really don't know why "net usershare info" isn't working but .......

One more piece of info ( sorry about all this ). Post the output of this command:
```
 cat /var/lib/samba/usershares/"tv shows"
```

---

### Post by FA5878 on 2010-08-05
Ah don't apologize, I appreciate your trying to help.

```
liam@Liam-Desktop:~$  cat /var/lib/samba/usershares/"tv shows"
#VERSION 2
path=/media/TV Shows/TV Shows
comment=
usershare_acl=S-1-1-0:R
guest_ok=y
```
(the name of the HDD is 'TV Shows' as well as the folder on it)

---

### Post by FA5878 on 2010-08-05
Ah don't apologize, I appreciate your trying to help

```
liam@Liam-Desktop:~$  cat /var/lib/samba/usershares/"tv shows"
#VERSION 2
path=/media/TV Shows/TV Shows
comment=
usershare_acl=S-1-1-0:R
guest_ok=y

```
(The HDD's name is also 'TV Shows')

---

### Post by Morbius1 on 2010-08-05
I can think of only two reasons why that won't work:

(1) When you reformatted the partition you didn't keep the same label ( TV Shows )

(2) The permissions on that mount point are such that a remote guest can't read it.

If you run the following command you should see all of the partitions mounted to /media:
```
ls -al /media
```That command will tell you if "TV Shows" still exists and what it's permissions are set at.

---

### Post by FA5878 on 2010-08-05
I didn't reformat until after the problem had started, it was originally called 'Storage A'. I was hoping that the traditional 'turn it off and on again' would work but I'm at a loss as to what to do after that.
```
liam@Liam-Desktop:~$ ls -al /media
total 20
drwxr-xr-x  5 root root 4096 2010-08-05 17:52 .
drwxr-xr-x 23 root root 4096 2010-08-04 09:23 ..
drwxr-xr-x  2 root root 4096 2010-08-01 19:04 Fez
lrwxrwxrwx  1 root root    7 2010-05-22 07:50 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2010-05-22 07:50 floppy0
-rw-------  1 root root    0 2010-08-01 11:20 .hal-mtab-lock
drwx------  5 liam liam 4096 2010-08-05 17:32 TV Shows

```

---

### Post by Morbius1 on 2010-08-05
> drwx------  5 liam liam 4096 2010-08-05 17:32 TV ShowsThat's the problem. The only user that can access the share is "liam". The remote user ( guest ) isn't "liam". There is one other oddity though. The only filesystem that mount's that way automatically is NTFS or FAT32. Is that how you have it formatted?

The solution is different depending on how the filesystem is formatted.

---

### Post by Morbius1 on 2010-08-05
I have to shut down - there's a storm coming and power goes off here at any moment under these conditions.

If it's formatted in ext3/4 then use the following command to set it so the remote guest can access the parent folder and thus gain access to the child shared folder:
```
 sudo chmod 0777 /media/"TV Shows"
```If it's an NTFS or FAT32 partition then the equivalent to the above gets a little tricky since you'll have to modify the fstab ( or create one ) for that partition.

There is one workaround that will work for both filssystems:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf
```
force user = liam
```Save the file, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```If your running Ubuntu earlier that 10.04 the command is:
```
sudo service samba restart
```What that will do is create a mask and convert all remote users to "liam". I don't know how your other shares are set up but if they are all set to guest access then this is probably the best way.

---

### Post by FA5878 on 2010-08-05
> **Morbius1 said:**
> I have to shut down - there's a storm coming and power goes off here at any moment under these conditions.

If it's formatted in ext3/4 then use the following command to set it so the remote guest can access the parent folder and thus gain access to the child shared folder:
```
 sudo chmod 0777 /media/"TV Shows"
```
I use ext4, this fixed it straight away thanks.

No idea what caused it to change, seems a bit random that the parent folder would be cut off from guest access because of a premature shutdown. Also the reformatting, why it mounted like that automatically I don't know (as you say ext4 shouldn't do that)

No matter, the problems solved and I have 250GB of my storage back, thanks a lot :)

---

### Post by FA5878 on 2010-08-06
Out of interest.

How would I permanently mount the shared folders onto the communal PC? (so I have a dedicated icon on the desktop at startup without needing to go through 'Network' etc...)

Cheers

---

### Post by Morbius1 on 2010-08-06
There's 3 ways ( that I know of ):

Classic-mount: You set up an entry in fstab to have the client mount it at boot. There are a lot of howto's on that.

GVFS-Mount: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)
This is the method I use these days. It has the advantage of working around a number of bugs that are in 10.04.

Gigolo ( it's in synaptic ): It's the GVFS-method above using an app with a GUI and is a much misunderstood and under appreciated little application that can do some very impressive things.

---

### Post by Insperatus on 2011-02-16
> **Morbius1 said:**
> 

There is one workaround that will work for both filssystems:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf
```
force user = liam
```Save the file, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```If your running Ubuntu earlier that 10.04 the command is:
```
sudo service samba restart
```What that will do is create a mask and convert all remote users to "liam". I don't know how your other shares are set up but if they are all set to guest access then this is probably the best way.

I can confirm this is a working solution for an NTFS formatted external USB hard drive.  After executing the instructions on my laptop running 10.10, my 2TB (NTFS) Iomega external hard drive which is plugged into it was then available to my older desktop, currently running 10.04.

---

### Post by Crick on 2011-06-16
> **Morbius1 said:**
> I can think of only two reasons why that won't work:

(1) When you reformatted the partition you didn't keep the same label ( TV Shows )

(2) The permissions on that mount point are such that a remote guest can't read it.

This latter was key for solving a similar "Failed to mount Windows share" issue. I had several shares that could be accessed fine, and one that couldn't. It turned out the one that couldn't was located in my /home/user directory. Because I have that directory set so only I can read it, it did not matter what permissions I had set on my /home/user/share directory.

I fixed it by moving the share directory to /home (e.g. /home/share) and then sharing via nautilus (since the HDD was mounted on /home, this was as far back as I could bring it). Hope this helps someone.

---

### Post by ubuntu_cork on 2011-09-03
> I fixed it by moving the share directory to /home (e.g. /home/share) and  then sharing via nautilus (since the HDD was mounted on /home, this was  as far back as I could bring it). Hope this helps someone.     This is exactly what was stopping me from seeing one of my own directories being shared so rather than expose my whole home/user directory as there are only two shares I forced the user as per the above post and it works.  

Security implications I am not too sure of however, What I would like is to have one directory where I can put all the stuff I want to share from my home, or even better just symlink it into that folder and voila, share on demand :D

Thanks to a great user ecosystem, more than one person has been helped in this thread!

---

