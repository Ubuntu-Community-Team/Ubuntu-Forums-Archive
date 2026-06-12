---
title: "Can't Access Share"
date: 2012-03-27
forum: General Help
---

### Post by PlatinumVengeance on 2012-03-27
Hello All,

This is my first thread, as I am both new to the forums and very new to Ubuntu/Linux.  We have Linux servers at work that I help manage and am still learning, but did not have any part in setting up.

I have created a server at home by setting up Ubuntu 10.04 on an old desktop with a 2TB drive.  I installed Samba and created a Samba share on the drive via smb.conf.  On all of my computer at home I use the same username and password.  Aside from this "server" I have a desktop running Windows 7 and a laptop running Ubuntu 10.04.  From my windows machine I can access the Samba share on the server and all of the directories within it with no problems.  The issue I am having is that on my laptop with Ubuntu I can access the Samba share on the server but I cannot access the directories within the share, I get a "You do not have the permissions necessary to view the contents of *(any directory within the Samba share).

On the share I have the permissions set to 777, so that is why I can access the share on my server from my laptop.  If I change the permissions to 770 I can not even access the share from my laptop.  Which kind of makes sense because I have the permissions set to 770 on all of the directories within the share, so that is why I cannot access them (I can access them if I set the permissions to 777 for all of them, but I do not want to leave them wide open!).

As I said, I am very new to this, and wanted to do this to both learn more about Ubuntu/Samba, and have heard great things about these forums!  Does anyone have any suggestions for me to get me on the right track to figuring this out?

Thanks!

---

### Post by PlatinumVengeance on 2012-03-28
Maybe to simplify my question...I have setup a desktop and a laptop both running Ubuntu 10.04.  I have created a directory on the desktop computer called /u.  I have made that directory a samba share, and can access if from an outside windows pc with the correct credentials just fine.  What do I have to do to be able to access a directory on one Ubuntu pc from another Ubuntu computer?

---

### Post by Morbius1 on 2012-03-28
Please post the output of the following commands:
```
testparm -s
``````
net usershare info --long
```Based on your original description you probably won't get any output of the second command but it's just in case.

[COLOR=Blue]**EDIT:**[/COLOR] Also need the permissions and ownership of the target folder:
```
ls -dl /u
```

---

### Post by PlatinumVengeance on 2012-03-28
Thanks for the reply!  My outputs are as follows:

> **Morbius1 said:**
> testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[Share]"
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
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d

[Share]
    comment = Share on FileServer
    path = /u
    valid users = jared
    create mask = 0777

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

> **Morbius1 said:**
> net usershare info --long
[u]
path=/u
comment=File share on FileServer
usershare_acl=Everyone:F,
guest_ok=y

> **Morbius1 said:**
> ls -dl /u
drwxrwx--- 7 jared root 4096 2012-03-27 17:11 /u

---

### Post by Morbius1 on 2012-03-29
There are two methods you can use to create a Samba share. You are using both methods on the same target folder with different settings. It's possible to use both methods but as you can see it is not  recommended and can be confusing to the client to use both on the same  target. I would choose one method or the other in this case.

This is a Classic Share where the share definition is in smb.conf:
> [Share]
    comment = Share on FileServer
    path = /u
    **[COLOR=Blue]valid users = jared[/COLOR]**
    create mask = 0777[COLOR=Blue]*Only one user is allowed access and only has read access.*[/COLOR]

This is a Samba Usershare created from Nautilus whose share definitions are in /var/lib/samba/usershares:
> [u]
path=/u
comment=File share on FileServer
usershare_acl=Everyone:F,
[COLOR=Blue]**guest_ok=y**[/COLOR][COLOR=Blue][I]From a Samba perspective everyone has access and has both read and write access. Your 0770 permissions will stop that from happening of course but Samba doesn't know that.
[/I][/COLOR]
**[1]** [B]Classic Share
[/B]
If you choose the Classic share you will have to add "jarred" to the samba password database - Windows does not differentiate a local user from a network user but UNIX / Linux / Samba does:
```
sudo smbpasswd -a jared
```How the client accesses this share will depend on what OS it's running:

** Windows will pass the user's actual local login user name and password when it browses the network even if such credentials are not required. This forces the server to process that information.  If you make the samba user name and password match the Windows username and password exactly then the Windows user will gain access without a credentials prompt. If the user name is the same but the password is different he will be prompted for credentials. 

** Linux does not automatically pass the users local login name and password because they think that's goofy so the Linux client will always be prompted for a password.

Just because Samba allows a user access to the share it does not guarantee he will be able to do anything to the contents because of Linux permissions on the individual files and folders in that share.

** [2] Usershare**

If you choose this method you will have to do one of two things in order to access that share.

Unlike Windows which really doesn't have the concept of an anonymous user a Linux client will come across as the user: "nobody". If you don't have an entry in the samba database for the remote user then the Windows user will also be forced through a different mechanism to take on the identity of the user: "nobody". "nobody" in samba correlates to "others" in Linux and with permissions set to 770 Samba will let him in but Linux will not. To fix this:

** Change permissions to allow "others" to access the directory:
```
sudo chmod 0777 /u
```** OR, force all remote users to take on the identity of "jared":

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section - right under the workgroup line:
```
force user = jared
```Save the file and restart samba:
```
sudo service smbd restart
```There are more complicated ways to do this but "force user" is the most efficient.

---

