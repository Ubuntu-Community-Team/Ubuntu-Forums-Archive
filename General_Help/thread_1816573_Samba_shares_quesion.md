---
title: "Samba shares quesion"
date: 2011-08-02
forum: General Help
---

### Post by pieroxy on 2011-08-02
Hi,

I have a bunch of Samba shares from my Ubuntu machine, and they are basically all guest shares. What I'd like is the following for each of my share:

- Guest share as read-only
- Authenticated share as RW. 

This is to prevent the kids and the wife from accidentally deleting something in my media collection. All those media center clients always have a "Delete" button way too close to the "Play" for my taste.

Can I do this with Samba? I am running the latest and greatest Ubuntu server right now.

---

### Post by zero2xiii on 2011-08-06
Yes,

It should be already set up like this though?

Just throw a right click > login as... to access your files with a useraccount on the server computer (the user must exist on the remote machine) alternatively, append the IP or hostname with:

"<the remote username>@" followed by the samba share or ip of the machine, this will prompt a password to acompany the username sent via plain text.

---

### Post by Morbius1 on 2011-08-06
> I have a bunch of Samba shares from my Ubuntu machine, and they are basically all guest shares.Unfortunately you didn't tell us what method you are using to create the shares - there are 2.

If you post the output of the following commands we can tell which method you are using so we can tell you how to achieve what you want consistant with the method you are using:
```
testparm -s
``````
net usershare info --long
```Either way though you will have to create a local user on the server itself corresponding to the client user and then add that user to the samba database.

---

### Post by pieroxy on 2011-09-05
> **Morbius1 said:**
> Unfortunately you didn't tell us what method you are using to create the shares - there are 2.

If you post the output of the following commands we can tell which method you are using so we can tell you how to achieve what you want consistant with the method you are using:
```
testparm -s
``````
net usershare info --long
```Either way though you will have to create a local user on the server itself corresponding to the client user and then add that user to the samba database.
I'm back from my vacation ;-)


Here are the (I think) relevant portions of my /etc/samba/smb.conf:
```

   workgroup = WORKGROUP
# commented line:
#security = user

[videos]
path = /myPath
comment = data
available = yes
browsable = yes
public = yes
writable = no
guest ok = yes
force user = pieroxy

```

```
$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[photos]"
Processing section "[music]"
Processing section "[videos]"
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

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[photos]
        comment = data
        path = /pathToPhotos
        guest ok = Yes

[music]
        comment = data
        path = /pathToMP3s
        guest ok = Yes

[videos]
        comment = data
        path = /pathToVideos
        force user = pieroxy
        guest ok = Yes
$ net usershare info --long
$

```

---

### Post by Morbius1 on 2011-09-05
Off the top of my head you've got 3 options:

[1] Modify and add one more line to your definition of the Videos share:
> [videos]
path = /myPath
comment = data
available = yes
browsable = yes
public = yes
writable = no
[COLOR=Blue]guest ok = no[/COLOR]
[COLOR=Blue] write list = pieroxy[/COLOR]
[COLOR=Black]force user = pieroxy[/COLOR]The Good: Only pieroxy will have write access.
The Bad: The only way for Samba to differentiate between pieroxy and everyone else is to force all remote users to authenticate. So the remote guest user will have to be given usernames on your Ubuntu machine and then assigned samba passwords.

[2] Keep all of your shares they way they are but create a set of admin shares that point to the same target but change the share name and limit access only to pieroxy:
> [videos-admin]
 path = /myPath
 comment = data
 available = yes
 browsable = yes
 public = yes
[COLOR=Blue]  writable = yes[/COLOR]
 [COLOR=Blue]guest ok = no[/COLOR]
[COLOR=Blue]valid users = pieroxy[/COLOR]The Good: Remote guests can continue to use the shares as they have before without providing authentication.
The Bad: Somewhat cluttered share list because of the duplication.

[3] Create a master share

You decided to obfuscate the real path to your shares which is unfortunate since I don't know if this would be an applicable option for you but you could create a share that encompass all the other shares and make it accessible only to you:
> [master-share]
path = /parent/of/all/your/other/shares
writable = yes
guest ok = no
valid users = pieroxy

---

### Post by pieroxy on 2011-09-05
> **Morbius1 said:**
> 
[3] Create a master share

You decided to obfuscate the real path to your shares which is unfortunate since I don't know if this would be an applicable option for you but you could create a share that encompass all the other shares and make it accessible only to you:

Thanks for your help! I will try option 3 tonight and will let you know.

---

### Post by pieroxy on 2011-09-09
So... HEre is what I tried:
```
[rwmedia]
path = /media/raid/Media
writable = yes
guest ok = no
valid users = pieroxy

```

I tried to mount this on another machine and here is what it does:


With /etc/fstab, I added the line:
```
//192.168.1.26/rwmedia /media/rwmedia cifs uid=1000,username=pieroxy,password=mypass,iocharset=utf8 0 1

```

Whenever I try to mount the drive, I get the following:
```
$ sudo mount /media/rwmedia 
mount: block device //192.168.1.26/rwmedia is write-protected, mounting read-only
mount: cannot mount block device //192.168.1.26/rwmedia read-only

```

With the command line I tried the following:
```
$ sudo mount -t smbfs -o credentials=.smba //192.168.1.26/rwmedia /media/rw-movies 
mount: wrong fs type, bad option, bad superblock on //192.168.1.26/rwmedia,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
with the file .smba like:
```
username=pieroxy
password=mypass
```


So... I cannot mount my share. Any idea of what might be wrong?

---

### Post by Morbius1 on 2011-09-10
[1] Make sure you have the following package installed:
```
sudo apt-get install cifs-utils
```[2] Try mounting it the gvfs way just to make sure it works:
```
 nautilus //192.168.1.26/rwmedia
```It will mount it to: [COLOR=Blue]/home/your-user-name/.gvfs/rwmedia on 192.168.1.26[/COLOR]

[3] Change your fstab entry to this:
>  //192.168.1.26/rwmedia /media/rwmedia cifs uid=1000,[COLOR=Blue]nounix[/COLOR],[COLOR=Blue]dir_mode=0777,file_mode=0666[/COLOR],username=pieroxy,password=mypass,iocharset=utf8 0 [COLOR=Blue]0[/COLOR]

---

### Post by pieroxy on 2011-09-10
I didn't have the cifs-utils installed. It is now done. Things are slightly different. Things changed at least!


With the new fstab line I go the following:
```
$ sudo mount /media/rw-movies 
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```


Mounting manually, I get ```
$ sudo mount -t cifs -o credentials=/home/pieroxy/.smba //192.168.1.26/rwmedia /media/rw-movies
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

And the last error: ```
nautilus //192.168.1.26/rwmedia
``` gave me a message "Could not find //192.168.1.26/rwmedia
Please check the spelling and try again"

---

### Post by Morbius1 on 2011-09-10
If this is your share definition:
> [rwmedia]
path = /media/raid/Media
writable = yes
guest ok = no
valid users = pieroxyPost the complete output of the following please:
```
ls -al /media/raid
```

---

### Post by pieroxy on 2011-09-11
```
$ ls -al /media/raid
total 32
drwxr-xr-x 5 pieroxy pieroxy  4096 2011-08-11 21:46 .
drwxr-xr-x 4 root    root     4096 2011-07-18 19:09 ..
drwxr-xr-x 2 pieroxy pieroxy  4096 2011-08-12 19:30 BKPS
drwx------ 2 root    root    16384 2011-07-18 19:03 lost+found
drwxr-xr-x 5 pieroxy pieroxy  4096 2011-07-26 21:16 Media
$
```

I tried giving everyone rwx access to /media/raid/Media but the result is the same. Now I have:
```
$ ls -ltr /media/raid
total 24
drwx------ 2 root    root    16384 2011-07-18 19:03 lost+found
drwxrwxrwx 5 pieroxy pieroxy  4096 2011-07-26 21:16 Media
drwxr-xr-x 2 pieroxy pieroxy  4096 2011-08-12 19:30 BKPS
$ 
```

---

### Post by Morbius1 on 2011-09-11
> [2] Try mounting it the gvfs way just to make sure it works:
     Code:
      nautilus //192.168.1.26/rwmedia 
My mistake, should have been the following. Sorry:
```
nautilus smb://192.168.1.26/rwmedia
```[COLOR=Blue]**EDIT:**[/COLOR] I just realized in looking over your posts that nowhere did you mention if you added your username to the samba password database. You have to do that first:
```
sudo smbpasswd -a pieroxy
```

---

### Post by pieroxy on 2011-09-11
Ah. That did it. 

```
sudo smbpasswd -a pieroxy
```

THAT did it. Thanks.

Now, what's the best way to hide my password? Making the fstab file readable only by root should do it... Will it have any ill side effects?

---

### Post by Morbius1 on 2011-09-11
Just change the permissions of /home/pieroxy/.smba and use the credentials file in your fstab entry:
```
chmod 0600 /home/pieroxy/.smba
```
It will be accessible only to you.

---

### Post by pieroxy on 2011-09-12
Thanks a lot Morbius1. I'm marking the thread as solved.

---

### Post by pieroxy on 2011-09-28
So... I have to reopen this thread because I have an issue with the solution proposed. It basically doesn't work reliably at home... I mount the samba drive with no issue, but after a while, all files disappear from the mountpoint and I get strange errors. On the server side, everything looks fine. All my read only shares do work as expected, only the RW shares behaves erratically.

I've tried to restart the smbd service and it works again for a few seconds. Here is an example of the command-line on the client machine:

```
pieroxy@pieroxy-dev:/media$ cd rw-media/
pieroxy@pieroxy-dev:/media/rw-media$ ls
\toto
pieroxy@pieroxy-dev:/media/rw-media$ rm \\toto 
rm: cannot remove `\\toto': No such file or directory
pieroxy@pieroxy-dev:/media/rw-media$ ls
\toto
pieroxy@pieroxy-dev:/media/rw-media$ ls // NOTE: I did restart smbd on the server
_5FKBU~3  IMG  MP3  VID
pieroxy@pieroxy-dev:/media/rw-media$ ls
_5FKBU~3  IMG  MP3  VID
pieroxy@pieroxy-dev:/media/rw-media$ ls
_5FKBU~3  IMG  MP3  VID
pieroxy@pieroxy-dev:/media/rw-media$ ls
ls: cannot access \toto: Invalid argument
\toto
pieroxy@pieroxy-dev:/media/rw-media$ ls
\toto
pieroxy@pieroxy-dev:/media/rw-media$ ls
\toto
pieroxy@pieroxy-dev:/media/rw-media$ ls
ls: cannot access \toto: Invalid argument
\toto
pieroxy@pieroxy-dev:/media/rw-media$ ls
\toto
pieroxy@pieroxy-dev:/media/rw-media$ ls
\toto
pieroxy@pieroxy-dev:/media/rw-media$ ls
ls: cannot access \toto: Invalid argument
\toto
pieroxy@pieroxy-dev:/media/rw-media$ ls
\toto
pieroxy@pieroxy-dev:/media/rw-media$ ls
\toto
pieroxy@pieroxy-dev:/media/rw-media$ ls
ls: cannot access \toto: Invalid argument
\toto
pieroxy@pieroxy-dev:/media/rw-media$ 

```

I could go on and on... On  the server:
```
pieroxy@ubuntu-home-server:~$ cat /etc/samba/smb.conf 
(...)
[videos]
path = /media/raid/Media/VID
comment = data
available = yes
browsable = yes
public = yes
writable = no
guest ok = yes
force user = pieroxy

[rwmedia]
path = /media/raid/Media
writable = yes
guest ok = no
valid users = pieroxy

pieroxy@ubuntu-home-server:~$ ls /media/raid/Media
IMG  MP3  \toto  VID
pieroxy@ubuntu-home-server:~$ 


```

Anyone has ever seen such behavior?

Edit: both machines are 64-bit 11.04s

---

### Post by Morbius1 on 2011-09-28
For one thing:
>  pieroxy@[COLOR=Blue]**ubuntu-home-server**[/COLOR]:~$ cat /etc/samba/smb.confThe name of your server is 3 characters too long. You can change it for networking purposes by doing this:

Edit smb.conf and add the following line to the [global] section:
```
netbios name = ubuntu-server
```It doesn't have to be that exact name but it has to be 15 characters or less in length.

THen restart samba:
```
sudo service smbd restart
```

---

### Post by pieroxy on 2011-09-30
My RO shares also seem affected by the problem, not only mw RW share.

Thanks for the tip. I just did that. Restarted smbd but nothing worked. Rebooted the machine. Nothing works. Seems worse than before actually... even after rebooting nothing works. I'm sure it has nothing to do with the netbios name... On my client machine:

```
pieroxy@pieroxy-dev:~/Downloads$ ls /media/rw-media/
\toto
pieroxy@pieroxy-dev:~/Downloads$ sudo umount /media/rw-media/
pieroxy@pieroxy-dev:~/Downloads$ ls /media/rw-media/
pieroxy@pieroxy-dev:~/Downloads$ sudo mount /media/rw-media/
pieroxy@pieroxy-dev:~/Downloads$ ls /media/rw-media/
ls: cannot access /media/rw-media/\toto: Invalid argument
\toto
pieroxy@pieroxy-dev:~/Downloads$ ls /media/rw-media/
\toto
pieroxy@pieroxy-dev:~/Downloads$ ls /media/rw-media/
\toto
pieroxy@pieroxy-dev:~/Downloads$ ls /media/rw-media/
ls: cannot access /media/rw-media/\toto: Invalid argument
\toto
pieroxy@pieroxy-dev:~/Downloads$ 

```

It's probably something very stupid on my end, but I can't pinpoint it. Moreover, I removed the '\toto' file from the root of the share and now ls just gives me nothing at all...

---

### Post by Morbius1 on 2011-09-30
The original name of the server ( ubuntu-home-server ) because of it's character length will be invisible on the network. You had to change it to something shorter - you had no coice.
> ls /media/rw-media/\totoYou can do that command forever and you won't get an output since the syntax is incorrect:
```
 ls /media/rw-media/toto
```

---

### Post by pieroxy on 2011-09-30
> **Morbius1 said:**
> The original name of the server ( ubuntu-home-server ) because of it's character length will be invisible on the network. You had to change it to something shorter - you had no coice.
You can do that command forever and you won't get an output since the syntax is incorrect:
```
 ls /media/rw-media/toto
```

I understand the original problem and I have fixed it. As far as the command you mentioned, I never tried it. If you look closely at my "logs", you'll see it is an error message from samba.

The shares still aren't stables... Some heavy scan of all files for example by a media app will make the share disappear. Then, I hav e to reboot the server to get my files back, there is no other option.

Could it be an issue on my network? Is there an app I can install on two machines that will test the connectivity ?

---

### Post by pieroxy on 2011-09-30
> **tumutanzi.com said:**
> I do not use this application, I just use Dropbox to share files between different computers.

Thanks a lot. Care to compute how much it's going to cost for me? I have around 7TB of data on these shares. So the calculation should include Dropbox pricing + 4 times 7TB of HDD to be able to synchronize that on my 4 clients ;-)

Dropbox is great. It just doesn't fit all purposes.

---

### Post by tumutanzi.com on 2012-05-18
No matter there are Google drive or SkyDrive, I always use Dropbox to sync my files between different devices, it is really a nice application.

---

