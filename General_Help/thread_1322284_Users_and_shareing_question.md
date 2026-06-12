---
title: "Users and shareing question?"
date: 2009-11-10
forum: General Help
---

### Post by stroyeror on 2009-11-10
Users and sharing question?  

OK i have a computer set up that i use for network storage.  I log in is a John but I have a another person that I want to be able to access the files on that computer.  i already have the files that i want to be shared under John and i can access them from another computer buy logging as John trough the network.  But how do i go about creating another user on the network storage computer and allowing that user to access those folder/files that are in John's home folder when they log in from the network.

Thanks.



Also here is a link to another post about another problem.
[http://ubuntuforums.org/showthread.php?t=1323120](http://ubuntuforums.org/showthread.php?t=1323120)

---

### Post by stroyeror on 2009-11-11
Bump

---

### Post by Iowan on 2009-11-11
Is it an Ubuntu machine set up as NAS? How are files shared (NAS, SAMBA, FTP, ...)? Will second user log directly into machine? If so, (s)he will need to have account set up via **adduser**. Optionally, (s)he could be added to a group (john?) that is has access to the files.

---

### Post by stroyeror on 2009-11-12
The files are being shared by samba.  And no the second user will not log in directly into the machine, the user will log when trying to access the shared files over the network.  

To access those folders that are being shared over the network i add the other user to the John Group? and when then acces that shared folder they then log in with there user name and pass?  Is that how you do it?

Thanks

---

### Post by stroyeror on 2009-11-12
Ok so adding the user to the John group does not work any ideas what i'm doing wrong?  or am i going about this the wrong way?

---

### Post by capscrew on 2009-11-12
> **stroyeror said:**
> Users and sharing question?  

OK i have a computer set up that i use for network storage.  I log in is a John but I have a another person that I want to be able to access the files on that computer.  i already have the files that i want to be shared under John and i can access them from another computer buy logging as John trough the network.  But how do i go about creating another user on the network storage computer and allowing that user to access those folder/files that are in John's home folder when they log in from the network.

Thanks.



Also here is a link to another post about another problem.
[http://ubuntuforums.org/showthread.php?t=1323120](http://ubuntuforums.org/showthread.php?t=1323120)


I would make all users part of a single group (mine is called smbusers) and use the *force group *parameter in the share definition.

All users should be able to access the defined share (use smbpasswd).  If you want to limit the creation and deletion of files and subdirectories use extended permissions of the files and directories (i.e. chmod 3770 <filename>)

The best place for information on this is [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://us6.samba.org/samba/docs/").

The best doc to read is [**_[COLOR="DarkSlateGray"]this[/COLOR]_**]("http://us6.samba.org/samba/docs/man/Samba-Guide/").

Edit:  It is important to understand that ALL users that will be logging in to the Samba server MUST be have a Linux login/pass (or a domain wide login/pass) and a smbpasswd on the server.

---

### Post by stroyeror on 2009-11-12
So what you are saying is i need to create a new group called  smbusers. But i dont understand what you mean by use the *force group *parameter in the share definition. 

 I understand that that the user that is logging in over the network needs to have a user name and pass on that machine locally.

Basically what is the easy way of having folders in one account that you are already shared and you make another account locally on the computer and you want he other person to log in with that account over the network to access the samba shares of that original account that has the samba shares.

Thanks

---

### Post by stroyeror on 2009-11-12
ok i have found this 

[http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/)


_Below is step six_
Now open a terminal in Ubuntu and enter the command:[INDENT] sudo smbpasswd -a username 
[/INDENT]This will add a SMB user.  

Should that above give the other person access to the shares that are in john's account.  The other person should then be able to log in with there user name and pass to be able access that network folder?  OR is this wrong?

Thanks again

---

### Post by capscrew on 2009-11-12
> **stroyeror said:**
> 
So what you are saying is i need to create a new group called smbusers. But i dont understand what you mean by use the force group parameter in the share definition.

When you configure the shares (in the smb.conf file), one of the parameters is ***force group***.  The man pages ```
man smb.conf
```

Provide insight```
 force group (S)
          This specifies a UNIX group  name  that  will  be  assigned  as  the
          default primary group for all users connecting to this service. This
          is useful for sharing files by ensuring that all access to files  on
          service  will  use  the  named group for their permissions checking.
          Thus, by assigning permissions for  this  group  to  the  files  and
          directories within this service the Samba administrator can restrict
          or allow sharing of these files.

```
This assumes that you have set the file permissions correctly on the server.
> 
I understand that that the user that is logging in over the network needs to have a user name and pass on that machine locally.

Basically what is the easy way of having folders in one account that you are already shared and you make another account locally on the computer and you want he other person to log in with that account over the network to access the samba shares of that original account that has the samba shares.

It might be best if you don't think of the shares as being *in a user account*.  Shares are shares and the user has the right to access them. 
> 


ok i have found this 

[http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/)


_Below is step six_
Now open a terminal in Ubuntu and enter the command:[INDENT] sudo smbpasswd -a username 
[/INDENT]This will add a SMB user.  

Should that above give the other person access to the shares that are in john's account.  The other person should then be able to log in with there user name and pass to be able access that network folder? 
Maybe.  :-)> 
 OR is this wrong?

The rights to access another users home directory is a file permissions issue, not a Samba issue.

It appears all you want is P2P sharing.  The tut doesn't go far enough.  You have to create a user account that can access your home directory.  You can test whether that user can access the directory you want to share.  If it works locally you should be able to access it remotely (over the network).

---

### Post by stroyeror on 2009-11-12
ok i have added the the new user to the john group.  And that group is selected in the permission tab in the group section but still can not get to access locally or remotely.

---

### Post by stroyeror on 2009-11-13
Thanks i have it all working now

---

### Post by capscrew on 2009-11-13
> **stroyeror said:**
> Thanks i have it all working now

Great!  For the benefit of others, what steps did you take to gain success?

---

### Post by stroyeror on 2009-11-13
Create a new user. And add that user to the john group. or to some other group that you want to create. Then log out and log in under that user name.  (dont know why i had to do this i did) log back into the original account and in the permission tab selct the group you want to have access to access to that folder in the group section.

Hope that makes sense.

also here is the other issue I'm having.
[http://ubuntuforums.org/showthread.php?t=1323120](http://ubuntuforums.org/showthread.php?t=1323120)

---

