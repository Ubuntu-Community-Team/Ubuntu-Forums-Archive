---
title: "Different Permissions for Files Created in Win7?"
date: 2012-07-07
forum: General Help
---

### Post by feed5000 on 2012-07-07
I'm hosting a Windows 7 program's data files on my Ubuntu box. All the permissions start out okay.

But when the program generates new data files (from Win7), the permissions (on Ubuntu) are:
[LIST]
[*]Owner: Create & Delete
[*]Group: Access
[*]Others: Access
[/LIST]

I need the new files to be made with 'Create & Delete' for at least the Group, and preferable for Others too. But I can't figure it out!

---

### Post by Redblade20XX on 2012-07-07
What is the file system you  are holding the shared data on?

-Red

---

### Post by CharlesA on 2012-07-08
> **Redblade20XX said:**
> What is the file system you  are holding the shared data on?

-Red
This info would help immensely. Is it on an ext or NTFS partition?

---

### Post by Morbius1 on 2012-07-08
It would also be helpful if we are talking about a Samba share on the Ubuntu box since it is not altogether clear to me from your description if this Win7 is on another partition or on another PC. But I confuse easily so .....

---

### Post by OM55 on 2012-07-08
Hello feed500,

From your description I will assume that you are using a Linux server, Windows 7 client and on the Linux server you use a Samba server to create the shares.

If so, you may only need to tweak your Samba configuration file on the Linux server: /etc/samba/smb.conf
and add the following lines (not inside any of the user definitions, so it will affects all users):

```
; Forcing all shared folder access to be user 'feed500'
    force user = feed500

; Forcing all files created to allow read/write access to everyone
    force create mode = 0666

; Forcing all folders created to allow read/write/execute access to everyone
    force directory mode = 0777
```

In the code above I assumed that the Linux server is constantly running with one active user (I used your username 'feed500' as an example). If that is not the case, than do not use the first line - 'force user'.
To make the change take effect you will need to restart your Samba server:

```
/etc/init.d/samba restart
```The above code will force the permission of all files and folders created using ANY samba share to a predefined permission. In this case full permissions (777 = read/write to owner, group and others).
If you want to set different permissions per each user, move those lines to the relevant user share definitions, located also in that smb.conf file.

If you need to change back the permissions of a file that was already created, use: chmode +7 <filename>

And to change the ownership of an existing file use:

```
chown <to_user>:<to_group> <file name>
```This can also be done recursively, on an entire folder and its subfolders:

```
chown -hR <to_user>:<to_group>
```Hope that helps.

---

### Post by Morbius1 on 2012-07-08
** First you don't want to use a "force user" just anywhere until you determine what kind ( Classic Shares or Usershares ), what type ( Private or Public ), and how many shares he has.

** There is no "samba" service in Ubuntu it's now smbd and nmbd.

** And it's not in init.d any longer it's in init since it's an upstart job so it's a "sudo service smbd restart" 

** And I have no idea what this means:
> If you need to change back the permissions of a file that was already created, use: chmode +7 <filename>
A better approach would be to get some facts first - I know, I know - How old fashion:

** Is this in fact a network question and are we talking about samba or something else?

** If it is a samba question then how are you configured and what type of samba shares did you create. The output of the following commands will tell us that:
```
testparm -s
``````
net usershare info --long
```

---

### Post by feed5000 on 2012-07-11
The configuration options provided by OM55 solved the problem. Thank you.

Here's the output of my testparm for the working configuration:
```
[global]
workgroup = FFED
security = SHARE
[PDS]
comment = PDS Data
path = /home/ffedadmin/PDS
force user = ffedadmin
force group = ffedadmin
read only = No
guest ok = Yes
browseable = No
```

To clarify on the some of the questions asked:
-It is an ext filesystem.
-I am using Samba to serve it to Win7 client computers.

Thank you who looked at this, especially OM55 and Morbius1.

---

