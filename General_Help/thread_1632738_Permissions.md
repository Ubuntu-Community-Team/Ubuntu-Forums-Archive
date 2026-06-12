---
title: "Permissions"
date: 2010-11-28
forum: General Help
---

### Post by Sepher on 2010-11-28
Hi,

I am pulling my hair out with this. I have shared two external harddrives via samba on ubuntu, but only I can access it. The reason being is because I have logged into linux, and become the owner of the external hdd's. On the permission properties, I can see that the group I have created every other user under has "No Folder Access", and if I change this it reverts back instantly. So frustrating, I've tried to chmod it which hasn't done a thing. The owner of the external hdd's seems to be the only person who can access it over samba.

Is there anyway I can get normal users to just read and write to external hdd's? It's silly this isn't the default option?

Cheers

---

### Post by Sepher on 2010-11-28
bump

---

### Post by Sepher on 2010-11-29
Any ideas anybody? My post is getting lost in the crowd haha :P

---

### Post by pricetech on 2010-11-29
Did you "sudo chown" the drives ??  How about "sudo chmod" ??

Unless I'm badly mistaken though, your permissions you set in your Samba config are different from your local permissions and if you share with other users via Samba, it should just work.

---

### Post by CharlesA on 2010-11-29
> **pricetech said:**
> 
Unless I'm badly mistaken though, your permissions you set in your Samba config are different from your local permissions and if you share with other users via Samba, it should just work.

Samba permissions are different then file permissions, but if the file permissions are correct, it should "just work"

Depending on the file system of those external drive, chmod and chown might not work (they don't work on NTFS drives).

---

### Post by SaintDanBert on 2010-11-29
When you connect USB drives, **YOU** are the owner by default. Consider making udev (or similar) rules that deal with the ownership issues.

I create one or more groups for files and folders and file systems.
The default users -- having nothing to do with interactive login -- have appropriate group membership. For example, I might have a "samba" user and groups of "smbpublic" "smbfamily" "smbclients" and so on.

Now when someone connects to a share, their identifiers samba:smbfamily etc determine what they can see and access.

REMEMBER -- Different flavors of win-dose use different techniques during share browsing and authentication.


Bonne chance,
~~~ 0;-Dan

---

### Post by Sepher on 2010-11-30
Thanks for the replys, I have tried CHMOD but now CHOWN but after doing some more research these two things will not work in my situation. My external harddrives are NTFS.

I can understand that whoever plugs in the harddrives becomes the owner and I've moved away from that now. I've found something else which says to put "force user = username" in the smb.conf file which I've done but this still isn't working. 

Have I started this off right, as I've created user accounts on the linux box that are exactly the same user accounts on the PC's accessing the linux shares if that makes sense? So I'll be accessing it with two different PC's and I've setup two accounts in linux as the PC's use two different logins.
I'm also using a GUI version of Samba that I installed through the package manager. It seems to have set me up with a pre-defined smb.conf file of which some of it I can change through the samba's own gui (workgroup, shares etc). The other strange thing it's doing is using a userlist, a list of users who are allowed access. Is this correct? 

Thanks :D

---

### Post by CharlesA on 2010-11-30
It sounds like your setup is right, it's only the NTFS part that is screwing stuff up, since they don't work with Linux permissions.

---

### Post by pricetech on 2010-11-30
Try this;  In a terminal type:

sudo smbpasswd username (substituting your username)

You'll be prompted for your password 3 times, once by sudo and twice by smbpasswd.

Try to access the shares again.

I've run into this on every computer I set up with Samba since Lucid.  It appears to be a bug of some sort.

Let us know.

---

### Post by SaintDanBert on 2010-11-30
"ntfs" under linux offers other options. I would start there. Make sure that you get what you really want after connecting and mounting the ntfs file systems and accessing the various contents from the "server" workstation. You can make this work, but I'd consider converting your ntfs file systems to a linux friendly file system if they will mostly get used in the manner you describe.

See this 
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

and this 
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions).

You can configure SAMBA to share the entire drive, folder trees, specific folders, or specific files (and printers). Create those shares with settings that you want and then make sure that the specific linux workstations user can access whatever it is in a useful manner. You can login as anyone and then use **su name ... pwd** to become some other user for testing.

See this:
[http://www.unixmen.com/linux-tutorials/1060-how-to-configure-samba-using-a-graphical-interface-in-ubuntu](http://www.unixmen.com/linux-tutorials/1060-how-to-configure-samba-using-a-graphical-interface-in-ubuntu)

SAMBA has configuration that does all sorts of mapping among the various workstations and "usernames". 

For example, user "smith" from workstation "foo" wants to connect to a share "files" on workstation "bar." 
[list]
[*]Samba can map all foo requests to a specific user defined on bar.
[*]Samba can map smith from foo to a specific user defined on bar
[*]Samba can map all smith from any workstation to a specific user defined on bar
[*]Samba can force user=framis for all requests to the files share regardless of the identity of the requesting user (after whatever mapping might have happened)
[/list]

You might implement "smbpublic" "smbpower" and "smbwizard". Where "smbpublic" is anyone from the wide world; "smbpower" gets more access than public but less than wizard; and, "smbwizard" can do almost everything (SAMBA won't let you give away full access.)

There are several good books and articles about SAMBA file and printer configuration.

---

### Post by Sepher on 2010-12-04
I've got it sharing fine now, it's just the NTFS permissions stopping me accessing the drives. Force user is having no effect. Not sure what else to try?

---

### Post by Morbius1 on 2010-12-04
Why not post the output of the following commands so we can see how you are set up:
```
net usershare info --long
```
```
testparm -s
```

---

### Post by Sepher on 2010-12-04
> **Morbius1 said:**
> Why not post the output of the following commands so we can see how you are set up:
```
net usershare info --long
```

Result:

```
[external hdd]
path=/media/External HDD
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

```
testparm -s
```

Result:

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[Storage Drive 2]"
Processing section "[Storage Drive 1]"
Processing section "[Data]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	workgroup = HOME_NETWORK
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
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

[Storage Drive 2]
	path = /media/External HDD
	read only = No
	guest ok = Yes

[Storage Drive 1]
	path = /media/Iomega HDD
	read only = No
	guest ok = Yes

[Data]
	path = /home/pandora/Data
	read only = No
	guest ok = Yes


```

I didn't know my external harddrive was shared twice, I thought I turned it off and was just sharing it through samba? Thanks for looking into this!

---

### Post by Sepher on 2010-12-04
The only way I can get it to somewhat work is to map the root user (who is the owner of the NTFS drives) to one of the user's from the windows machine. But it still leaves me the problem of accessing with two or more users, as I want my partner to access these shares from her PC too which is also windows.

---

### Post by Morbius1 on 2010-12-04
Samba has two ways to share directories.
This is called Samba Usershares ( aka Nautilus-shares ):
> [external hdd]
path=/media/External HDD
comment=
usershare_acl=Everyone:F,
guest_ok=yThis is called Samba Classic-shares:
> [Storage Drive 2]
    path = /media/External HDD
    read only = No
    guest ok = YesBoth methods are Samba and both methods will work but it's really not a good idea to use both on the same target folder. I would get rid  of the Usershare since you already have so many Classic-shares. Just go back into nautilus and "unshare" it.

I'm going to guess that these two external drives are formatted in ntfs:
> [Storage Drive 2]
    path = /media/External HDD
    read only = No
    guest ok = Yes

[Storage Drive 1]
    path = /media/Iomega HDD
    read only = No
    guest ok = YesIf they are then they will mount with you as owner and with permissions for only you to access them. "force user = your-user-name" will make the remote user appear to be you and should resolve this issue:
> [Storage Drive 2]
    path = /media/External HDD
    read only = No
    guest ok = Yes
[COLOR=Blue]    force user = your-user-name[/COLOR]

[Storage Drive 1]
    path = /media/Iomega HDD
    read only = No
    guest ok = Yes
    [COLOR=Blue]force user = your-user-name[/COLOR][COLOR=Blue]*Change your-user-name to your actual login user name on the box with the shares - I'm guessing it's: *[/COLOR]pandora

Save smb.conf and in the terminal restart samba:
```
sudo service smbd restart
```If that doesn't fix it them post the output of these two commands:
```
 ls -dl /media/"External HDD"
``````
 ls -dl /media/"Iomega HDD"
```

---

### Post by Sepher on 2010-12-06
> **Morbius1 said:**
> Samba has two ways to share directories.
This is called Samba Usershares ( aka Nautilus-shares ):
This is called Samba Classic-shares:
Both methods are Samba and both methods will work but it's really not a good idea to use both on the same target folder. I would get rid  of the Usershare since you already have so many Classic-shares. Just go back into nautilus and "unshare" it.

I'm going to guess that these two external drives are formatted in ntfs:
If they are then they will mount with you as owner and with permissions for only you to access them. "force user = your-user-name" will make the remote user appear to be you and should resolve this issue:
[COLOR=Blue]*Change your-user-name to your actual login user name on the box with the shares - I'm guessing it's: *[/COLOR]pandora

Save smb.conf and in the terminal restart samba:
```
sudo service smbd restart
```If that doesn't fix it them post the output of these two commands:
```
 ls -dl /media/"External HDD"
``````
 ls -dl /media/"Iomega HDD"
```

Adding that force user = pandora to the drives did the trick mate. That user account [Pandora] is the owner of the NTFS drives. Not sure how to turn the nautilus share off, as I've right clicked on the drive and turned sharing off but not to bothered about it, as it works! 

Thanks again ;)

---

### Post by SaintDanBert on 2010-12-07
> **CharlesA said:**
> 
...
Always use the right (bam) hammer for the job.
...


If your only tool is a hammer, you tend to think of every problem as a nail.

The hammer was a perfect tool until someone invented the screw.
(double meaning intentional)

If at first you don't succeed, get a bigger hammer.

~~~ 0;-Dan

---

### Post by CharlesA on 2010-12-07
> **SaintDanBert said:**
> If your only tool is a hammer, you tend to think of every problem as a nail.

The hammer was a perfect tool until someone invented the screw.
(double meaning intentional)

If at first you don't succeed, get a bigger hammer.

~~~ 0;-Dan

Haha. ;)

It's a ban hammer, but still. :twisted:

---

### Post by SaintDanBert on 2010-12-08
> **CharlesA said:**
> Haha. ;)

It's a ban hammer, but still. :twisted:

That swishing sound is me searching pages to learn about "ban hammers".
Never heard the term before. Hmmmm.

~~~ 0;-Dan 

I forgot one:
"You can drive screws with a brick and it still works as a fastener,
but such a screw is as poor a nail as the brick makes for a hammer."

---

