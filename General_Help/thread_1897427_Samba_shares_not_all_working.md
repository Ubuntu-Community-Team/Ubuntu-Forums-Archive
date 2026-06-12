---
title: "Samba shares not all working"
date: 2011-12-19
forum: General Help
---

### Post by exup1000 on 2011-12-19
Hi

I am running Ubuntu 11.10 teaching myself to build a file server.
I have a partition on the same drive as the main o/s, call Data and created a sub folder called "sharetest" I have also create a group called "users" and added a user to that group. Next I made sure that the groups users had read, write and execute to that folder and all sub folders. I can whilst logged on the server have read and write access to this folder.

If I do ls - l I get this

[INDENT]drwxrwx--- 3 root users  4096 2011-12-19 22:03 IT_DRIVE[/INDENT]

I have then edited my smb.conf to create the share and run testparm and stopped and restarted smbd and nmbd

As a test I have also allowed home drives (see testparm below)

So on both a windows 7 and ubuntu client I can connect to the home drive, but the issue is this "sharetest". I can see it in the browser, but when I connect using net use in windows or mount in Ubuntu after prompting for a password they both say unable to mount permission denied.
Looking at the log files it shows 

[INDENT][2011/12/19 23:49:57.551995,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service sharetest, path /media/IT_Drive[/INDENT]

Here is the testparm result

[INDENT]Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[sharetest]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = TESTING
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
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[homes]
	comment = Home Directories
	read only = No
	browseable = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[sharetest]
	comment = this is a test share
	path = /media/IT_Drive
	read only = No
[/INDENT]

I do want to lock the shares down so only user accounts on the server have ability to browse and edit files folders on the shares.

---

### Post by Morbius1 on 2011-12-19
I'm a little confused by your description of this share.
> I have a partition on the same drive as the main o/s, call Data and created a sub folder called "sharetest" > [sharetest]
    comment = this is a test share
    path = /media/IT_Drive
    read only = No
What is the relationship between the "sharetest" subfolder on the "Data" partition and /media/IT_Drive?

If the "Data" partition is being automounted at /media/Data and you have a subfolder that you with to share named "sharetest" then the path to the share in smb.conf should read:
```
path = /media/Data/sharetest
```Am I missing something?

---

### Post by exup1000 on 2011-12-20
Oh dear I am an idiot....#-o

yes well spotted, the smb.conf entry is wrong as you say and it is or should be /data/IT_Drive

I made the changes to the conf file, re ran testparm and restarted samba, in fact restarted the server **_but _**still have the same issue and not able to connect. Windows is still reporting I do not have permission to the drive even though I can see it in the browser. I can still connect to the home drives ok.

I will check the logs and see what its reporting.
Update: found logs reporting same error.
 canonicalize_connect_path failed for service sharetest, path /data/IT_Drive

---

### Post by Morbius1 on 2011-12-20
What are the permissions along the entire path to the shared folder:
```
ls -al /data
```

---

### Post by exup1000 on 2011-12-21
Hi, $ls -la /data gives

[INDENT]drwxr-xr-x  4 root root   4096 2011-12-11 23:29 .
drwxr-xr-x 24 root root   4096 2011-12-18 06:54 ..
drwxrwx---  3 root users  4096 2011-12-19 22:03 IT_DRIVE
drwx------  2 root root  16384 2011-12-05 21:13 lost+found
[/INDENT]

I created a local group called "users" and the user that is trying to connect has an account on the server and is a member of the group. If type $ members users I can see the user account in there.

Should I be using the workgroup or server name when entering in the user name for example from a windows machine I use
net use \\testsfs01\sharetest /user:testing/username
the workgroup = testing and server name is testsfs01
then entering the servers password for the user I have created on that server.

I have also printed out my smbclient -L on the server

```
Domain=[TESTING] OS=[Unix] Server=[Samba 3.5.11]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        sharetest       Disk      this is a test share
        IPC$            IPC       IPC Service (testsfs01 server (Samba, Ubuntu))
        au009900        Disk      Home Directories
Domain=[TESTING] OS=[Unix] Server=[Samba 3.5.11]

        Server               Comment
        ---------            -------
        TESTSFS01            testsfs01 server (Samba, Ubuntu)
        TESTW100             TESTW100 server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        TESTING              TESTW100

```

and from the client

```
Shared resources at \\testsfs01

testsfs01 server (Samba, Ubuntu)

Share name  Type  Used as  Comment

-------------------------------------------------
au009900    Disk  (UNC)    Home Directories
sharetest   Disk           this is a test share
The command completed successfully.
```

---

### Post by Morbius1 on 2011-12-21
I have recreated your share on my system and gave the shared folder the same permissions ( not exactly, I made the group plugdev since all my server users are members of that group by default ) and I can't reproduce your symptoms.

The only thing I can think of at the moment is that you also have a Samba Usershare that is in conflict with that Samba Classic share. Run the following command and see if you also have a userhsare for that directory:
```
net usershare info --long
```

---

### Post by exup1000 on 2011-12-21
I quickly ran the command in the location of the share and it does not return anything? No errors or comments.

I will check the commands usage in case I am not using it properly.

I did have openldap (slapd) installed along with samba sharing as per the ubuntu server guide, but I removed them. I wonder if there is some legacy hangover from them?

---

### Post by Morbius1 on 2011-12-22
Here's the problem that I personally don't understand:
> So on both a windows 7 and ubuntu client I can connect to the home  drive, but the issue is this "sharetest". I can see it in the browser,  but when I connect using net use in windows or mount in Ubuntu after  prompting for a password they both say unable to mount permission  denied.Whatever setup you have place in your system or on your network seems fine with the [homes] share. Remote users are authenticated and can access their home directories on your server. It's only the sharetest share that's the issue. 

Create a Test directory in the same partition where your home directories are located:
```
sudo mkdir /home/Test
```Then share that directory:
```
[test]
path = /home/Test
read only = no
guest ok = no
```Replicate the ownership and permissions you have on "sharetest" and see if this new share has the same problem. It may be something with that partition in /data that's the issue.

---

### Post by exup1000 on 2011-12-22
RESOLVED: oh dear, linux 101 training lacking.

Still the same original issue, typo in the share. I forget about the case sensitivity when using linux

IT_DRIVE does not equal IT_Drive as you see in the post where I list the read, write, execute status for the drive its actually IT_DRIVE so i correctedt that and it works.



sorry for the run around and thanks for helping out, it helps to have someone look over what your trying to fix. (Not seeing the woods for the trees)

---

### Post by Morbius1 on 2011-12-22
If it makes you feel any better I didn't notice that the path in the share didn't match the output of ls -al either :oops:

---

