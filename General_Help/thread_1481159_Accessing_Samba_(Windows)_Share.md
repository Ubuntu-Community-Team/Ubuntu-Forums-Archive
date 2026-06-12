---
title: "Accessing Samba (Windows) Share"
date: 2010-05-12
forum: General Help
---

### Post by de Silentio on 2010-05-12
I am having trouble accessing a samba share when I am trying to upload a file. I'm running Ubuntu NBR 9.1 (this doesn't work on 10.4 either) 
 
The share is a Windows share and I can access the share by typing "smb://server/sharename" when I am in the file explorer, but when I am in Google Docs trying to upload a file, typing in "smb://server/sharename" and pressing Enter doesn't do anything. The "Open" button clicks, but the share never opens.
 
I notice that in the "Places" pane, I don't see a mounted share or the Network location.
 
Any help is appreciated.
 
John Dombrowski

---

### Post by mobi on 2010-05-12
Have you tried to mount it?

---

### Post by de Silentio on 2010-05-12
I didn't mount the share using any commands, but it seems that the share is mounted. I think this because the first time I navigate to an smb share through file explorer, it adds it under places and I can then "unmount" the drive if I want to.
 
Two questions:
 
1. Shouldn't I be able to type in the location, or is this not a feature?
 
2. What method do you recommend for mounting. The problem I have is that the instructions I have found for mounting require a hard coded password, which I don't want, since we are using Likewise and AD accounts (for example, in file explorer when I access the smb share, my username and password are passed through)
 
Perhaps if I give you my scenario it will help.  We are a Windows shop and are integrating some netbooks into a few computer labs (we are a k12 school system).  Everyone is used to using mapped drives to access their home shares and a general network share.
 
There is one of two options that I would like to see happen.
 
1. When a user logs in, a script mounts their home drive (which is defined in the normal spot in AD) and a general network share (which is the same for everybody)
 
2. People can access their home drives by typing smb://server/sharename.  This will allow people to upload documents to the web from Linux.
 
I would like the username and password to be seemless, as it is when I navigate to the share via file explorer.
 
Thanks for the reply,
John

---

### Post by Morbius1 on 2010-05-12
Typing "smb://server/sharename" in Nautilus will mount the share at:

**/home/your_user_name/.gvfs/sharename on server**

---

### Post by de Silentio on 2010-05-12
Thanks morbius, the share is accessible through the File Upload through the .gvsf folder like you said.  
 
I assume that Nautilus is the "File Explorer", do you know what the file explorer is called when I am uploading a file through Firefox (maybe this is part of firefox and not part of Ubuntu?)?
 
I attached a picture of what I am trying to do.  When I have the smb://... in there and press enter, the Open button (which is off the screen in the picture) get's "clicked", but nothing happens.
 
Thanks again.

---

### Post by Morbius1 on 2010-05-12
I'm not familiar with that feature of firefox or google docs.

But in general you need to go to Nautilus ( File Explorer ) and connect to the share first to "mount" it. Then go to the .gvfs folder when the application asks where the file is located that you want to upload.

It's nautilus that does the mounting not the application you're using.

You can automate this process of mounting through Nautilus if the share is on a server that is up prior to booting:

***Step 1: Connect to the Server from Nautilus***

```
smb://server/sharename
```If the server requires authentication then enter it and click on the "remember forever" option before entering "Connect"
Once you have successfully connected go back and unmount the remote share.

***Step 2: ******Create a script that will automate this process:***

Open **Terminal**
Type **gedit**
Enter the following:
```
#!/bin/sh
gvfs-mount smb://Server/sharename
```Save the file as, for example:  /home/user_name/share_name_mount.sh

Exit **gedit**

Back in the terminal make the script executable by issuing the command:
**chmod +x /home/user_name/share_name_mount.sh**

*** STEP 3: Add it to your AutoStart Options***

Go to System > Preferences > Startup Applications > Add > point it to /home/user_name/share_name_mount.sh.

Logoff and logon again and you should have your share mounted to /home/user_name/.gvfs/ automatically ( assuming the server is running ) and you should have a mount icon on your desktop.

When you're in your application point it to the .gvfs folder and not the remote share through smb:// .....

---

### Post by de Silentio on 2010-05-12
Thanks for the informational reply.  I have two problems:
 
1. the .gvfs folder is hidden by default.  Is there a way to mount into different folder?
 
2. This will work for my common share, but our home folders are unique to each person that logs on.  I don't suspect that you have any information about pulling the home directory info from AD.
 
Thanks,
John

---

### Post by NovaWasp on 2010-05-12
Create a directory to put the mounted files either in Nautilus or via command line

```

mkdir mntpoint

```then you can run.

```

sudo mount -t smbfs -o username=username,uid=ilinuxid,gid=linuxid //server/shared_folder mntpoint/

```mount -t smbfs - Windows share
-o - options comma seperated.  Don't use any spaces.
-o - uid and gid are important.  If you don't use them, then you root gets the ownership and you have to sudo to copy files onto the share.

then the server and shared folder and the mountpoint.

If you're in Active Directory, you'll need the domain on the username.  If the domain is DOMN1, then the user name will look like DOMN1\\username.  You need the extra backslash.  The windows domain is not case sensitive. You could type domn1\\username.

Hope that helps.

---

### Post by Morbius1 on 2010-05-12
>  1. the .gvfs folder is hidden by default.  Is there a way to mount into different folder?There is not. You can however create a symbolic link from the .gvfs directory to a "real" directory:

```
mkdir /home/your_user_name/RemoteShare
ln -s /home/your_user_name/.gvfs/"sharename on server" /home/your_user_name/RemoteShare
```

---

### Post by de Silentio on 2010-05-13
Thanks to both Morbius and Novawasp.
 
NovaWasp, I think your solution is viable, except that whenever I try to mount when logged on as a domain user I get the error "Mount: Only root can do that".  I cannot use the sudo command as normal domain users are not part of the root group.
 
I read something about doing a chmod on the /usr/bin/smbmount, but I cannot find this directory to make the change.
 
Do you know how I can make it so normal users can mount folders? 
 
Thanks

---

### Post by NovaWasp on 2010-05-14
Do you have root access to the box and you're trying to configure it to work with a domain login?

In which case you could grant sudo access to an AD group.  
Ask your administrator to create a group like "linuxsudoers" and put you in it.

```

sudo visudo

```

Go to the bottom find admin.

add

```

%wdmn\\linuxsudoers ALL=(ALL) ALL

```
I'm assuming wdmn is the windows domain. 
% starts the line.
\\ is needed because the first slash is an escape character.

Do not use some generic group like Users to grant sudo access or you'll wind up giving everyone in your organization access.

Although, if you are trying to authenticate to a share you don't have access to, you're going to have issues without credentials.  I use that sudo mount command every day with no problem.

---

