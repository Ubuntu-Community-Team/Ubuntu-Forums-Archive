---
title: "How to share folders/printers?"
date: 2011-03-12
forum: General Help
---

### Post by rva1945 on 2011-03-12
I have a desktop PC and a notebok, both with Maverick 10.10.

We are two users, I have Administrator privileges. What we need is to have a folder in common where we can create, edit or delete folders and files.

And there's a printer connected to the desktop PC, how can I see it from the notebook? I installed samba but can't get it to work, or I just don't know how to configure it.

I'd appreciate any help

Thanks

---

### Post by howefield on 2011-03-13
Try right clicking on the folder you want to share and select "Sharing options". Check the options as required.

On the machine that has the printer connected to it, try going to System > Administration > Printing and select the Settings option from the Server menu.

Check the box for "Publish shared printers connected to this system" and other options as required. On the other machine go to the same menu and this time select "Show printers shared by other systems".

You might need to reboot, I can't remember if I had to when last I set this up.

---

### Post by rva1945 on 2011-03-13
> **howefield said:**
> Try right clicking on the folder you want to share and select "Sharing options". Check the options as required.

On the machine that has the printer connected to it, try going to System > Administration > Printing and select the Settings option from the Server menu.

Check the box for "Publish shared printers connected to this system" and other options as required. On the other machine go to the same menu and this time select "Show printers shared by other systems".

You might need to reboot, I can't remember if I had to when last I set this up.

Thanks. Didn't know the Publish shared printers.. in the server menu. 

As for the shared folder: where should be that folder created? In my Home/robert (my usser account) folder? I even tried to create a new user "commonfolder", so Ubuntu would create home/commonfolder folder, then logged as commonfolder, grant read and write access to everyone else, but it doesn't work that way (I admit I tried to emulate the All Users folder from Wndws).

That's what I want, to have a folder in common where any user can create/edit/delete folders and files.

Thanks

---

### Post by howefield on 2011-03-13
> **rva1945 said:**
> That's what I want, to have a folder in common where any user can create/edit/delete folders and files.

Sure, you can create the folder in whichever users home folder you wish.

---

### Post by rva1945 on 2011-03-13
> **howefield said:**
> Try right clicking on the folder you want to share and select "Sharing options". Check the options as required.

On the machine that has the printer connected to it, try going to System > Administration > Printing and select the Settings option from the Server menu.

Check the box for "Publish shared printers connected to this system" and other options as required. On the other machine go to the same menu and this time select "Show printers shared by other systems".

You might need to reboot, I can't remember if I had to when last I set this up.

GREAT! as soon as I publish the shared printer in the desktop, then when I went to system/Printing in the ntebook...the new network printer showed up automatically.

Thanks

---

### Post by howefield on 2011-03-13
That's great, thanks for the update.

I'm sure you're aware, but remember the printer can only be accessed via the network when your desktop is switched on and logged in. :)

---

### Post by rva1945 on 2011-03-13
> **howefield said:**
> Try right clicking on the folder you want to share and select "Sharing options". Check the options as required.

On the machine that has the printer connected to it, try going to System > Administration > Printing and select the Settings option from the Server menu.

Check the box for "Publish shared printers connected to this system" and other options as required. On the other machine go to the same menu and this time select "Show printers shared by other systems".

You might need to reboot, I can't remember if I had to when last I set this up.

OK, I shared one folder of my home, "SharedFolder", now I logged into the other user account but I don't see the share.

If I navigate to the folder from that user account, i can create files but the files created by the other user appear as read-only. Does the creator of any file have to grant access to other users? I thought this was automatic.

---

### Post by Morbius1 on 2011-03-13
I'm getting confused. 

Are the users local to the Desktop - multiple local login users sharing a common directory. Or by users do you mean remote samba users. 

I'm going to guess you mean local login users to the desktop. Here's one way:

(1) Create a "Shared" directory
```
sudo mkdir /home/Shared
```(2) Change the group of the shared directory to plugdev ( all local users are members of the plugdev group by default )
```
sudo chown :plugdev /home/Shared
```(3) Change permissions of the shared directory to allow all members of the plugdev group to have access and so that all new files / directories will inherit the plugdev group:
```
sudo chmod 2775 /home/Shared
```So far so good. All local login users will have access and can add to or delete from that directory. What they cannot do is edit anyone else's files. When any user adds a new file to that folder it will save with:
owner = user-name, group = plugdev,  but with permissions of 644: owner can read and write but everyone else can only read.

(4) You're going to have to change the global umask for new file creation by editing:
```
/etc/profile
```And changing the last line to :
```
umask 002
```You're going to have to logout and login again because the profile is read only at login time.

Now every new folder / file will save as 775 / 664 and the group will be plugdev. So all local login users will be able to edit anything in /home/Shared.

---

### Post by rva1945 on 2011-03-13
> **Morbius1 said:**
> I'm getting confused. 

Are the users local to the Desktop - multiple local login users sharing a common directory. Or by users do you mean remote samba users. 

I'm going to guess you mean local login users to the desktop. Here's one way:

(1) Create a "Shared" directory
```
sudo mkdir /home/Shared
```(2) Change the group of the shared directory to plugdev ( all local users are members of the plugdev group by default )
```
sudo chown :plugdev /home/Shared
```(3) Change permissions of the shared directory to allow all members of the plugdev group to have access and so that all new files / directories will inherit the plugdev group:
```
sudo chmod 2775 /home/Shared
```So far so good. All local login users will have access and can add to or delete from that directory. What they cannot do is edit anyone else's files. When any user adds a new file to that folder it will save with:
owner = user-name, group = plugdev,  but with permissions of 644: owner can read and write but everyone else can only read.

(4) You're going to have to change the global umask for new file creation by editing:
```
/etc/profile
```And changing the last line to :
```
umask 002
```You're going to have to logout and login again because the profile is read only at login time.

Now every new folder / file will save as 775 / 664 and the group will be plugdev. So all local login users will be able to edit anything in /home/Shared.

Thanks, I'll try that. And what about a shared folder in the network? I installed Samba in both PC (both with Ubuntu 10.10).

---

### Post by Morbius1 on 2011-03-13
You're going to have to tell us how you created the share. The output of these commands will tell us that:
```
net usershare info --long
```
```
testparm -s
```

---

### Post by rva1945 on 2011-03-13
> **howefield said:**
> That's great, thanks for the update.

I'm sure you're aware, but remember the printer can only be accessed via the network when your desktop is switched on and logged in. :)

I found it the hard way.

---

### Post by rva1945 on 2011-03-13
> **Morbius1 said:**
> I'm getting confused. 

Are the users local to the Desktop - multiple local login users sharing a common directory. Or by users do you mean remote samba users. 

I'm going to guess you mean local login users to the desktop. Here's one way:

(1) Create a "Shared" directory
```
sudo mkdir /home/Shared
```(2) Change the group of the shared directory to plugdev ( all local users are members of the plugdev group by default )
```
sudo chown :plugdev /home/Shared
```(3) Change permissions of the shared directory to allow all members of the plugdev group to have access and so that all new files / directories will inherit the plugdev group:
```
sudo chmod 2775 /home/Shared
```So far so good. All local login users will have access and can add to or delete from that directory. What they cannot do is edit anyone else's files. When any user adds a new file to that folder it will save with:
owner = user-name, group = plugdev,  but with permissions of 644: owner can read and write but everyone else can only read.

(4) You're going to have to change the global umask for new file creation by editing:
```
/etc/profile
```And changing the last line to :
```
umask 002
```You're going to have to logout and login again because the profile is read only at login time.

Now every new folder / file will save as 775 / 664 and the group will be plugdev. So all local login users will be able to edit anything in /home/Shared.

Thanks, it worked.

"Now every new folder" refers to ANY folder created ANYWHERE by the users, or just the folders/files inside that shared folder?

---

### Post by rva1945 on 2011-03-13
> **howefield said:**
> Try right clicking on the folder you want to share and select "Sharing options". Check the options as required.

On the machine that has the printer connected to it, try going to System > Administration > Printing and select the Settings option from the Server menu.

Check the box for "Publish shared printers connected to this system" and other options as required. On the other machine go to the same menu and this time select "Show printers shared by other systems".

You might need to reboot, I can't remember if I had to when last I set this up.

I created a folder in my home, "sharedfolder", right clicked on it, Sharing options, share this folder, allow others to create...

But in System-Administration-Samba, I only see the shared folders I added using that tool, the same I see in System Administration Shared folders.

And I don't see the folder from the other pc: in Places Network, a Windows Network appears but can't access to it. How can I scan for shared folders in the network?

---

### Post by Morbius1 on 2011-03-14
> **rva1945 said:**
> Thanks, it worked.

"Now every new folder" refers to ANY folder created ANYWHERE by the users, or just the folders/files inside that shared folder?

By changing the global umask to 002 all files saved by everyone everywhere will now save with permissions of 664 - owner and group writable.

But only in /home/Shared will they save with group = plugdev. Everywhere else they will save with owner = group.

---

### Post by Morbius1 on 2011-03-14
> **rva1945 said:**
> I created a folder in my home, "sharedfolder", right clicked on it, Sharing options, share this folder, allow others to create...

But in System-Administration-Samba, I only see the shared folders I added using that tool, the same I see in System Administration Shared folders.

And I don't see the folder from the other pc: in Places Network, a Windows Network appears but can't access to it.
You're using two completely different methods to create Samba shares.

Usershares - a.k.a. nautilus-shares - was what you did when you created the shares from Nautilus. 

Classic-shares was what you did when you created the shares using System-Administration-Samba.

Their share definitions are in two different places. You can see how your shares are defined by using these two commands and I would recommend that you run them and post the output:
```
net usershare info --long
testparm -s
```The first one shows you Usershares, the second one shows you Classic-shares plus how Samba itself is configured.
>  How can I scan for shared folders in the network?They should be visible automatically so there must be a problem. I would run a diagnostic command first on the desktop machine to check for any kind of error:
```
smbtree
```That will display all shares everywhere and output error messages if it finds something wrong.

---

