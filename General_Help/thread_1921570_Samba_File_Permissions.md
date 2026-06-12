---
title: "Samba File Permissions"
date: 2012-02-07
forum: General Help
---

### Post by Joshua on 2012-02-07
I'm having trouble with some file permissions, I think.

I have Samba set up with Winbind and Active Directory authentication.  I've shared the home directories and changed permissions to 750 with the intention of preventing people from seeing what is in other people's home directories.  However, when I browse to my home directory via Windows, it appears that I need to have the world read permissions set to see any files show up - even files that I've created with me as owner and my primary group as the group.

Has anyone ever seen this or solved it?

---

### Post by Joshua on 2012-02-07
I thought this would have an easy answer...

Does anyone know how I might go about troubleshooting this?

Other info that might help is that I have the "hide unreadable" option in the global Samba settings.  So I think it's expected that if I were not the owner or in the group of a file with 0750 permissions, then that file would not appear in the directory when I browse there from a Windows machine.

The confusing part is that I appear to be authenticating correctly with my username because I'm able to see my home directory.  The directory has the same permissions as the files within it (0750), but I can only see files in the home directory if I make sure they are world readable.

---

### Post by ROBarber on 2012-02-08
What is the configuration for the smb.conf file regarding the home directory you want to access from Win machines?
I have something like this:
```

[DirectoryName]
	path = /home/DirectoryName
	writeable = yes
	browseable = yes
	valid users = WinDomainName/WinUserName1 WinDomainName/WinUserName2
	admin users = WinDomainName/WinUserName1
	read list = WinDomainName/WinUserName1 WinDomainName/WinUserName2
	write list = WinDomainName/WinUserName1 WinDomainName/WinUserName2
	comment = DirectoryNamePurpose

```

I have another issue instead. Having this configuration, if **WinDomainName/WinUserName1** made modifications to one file and save it, thus he owns the file, the group permissions are changed from -rw to just -r and if **WinDomainName/WinUserName2** tries to access the file it can be done only in read-only mode.

Is there any modification I have to made to the file permissions, and the group permissions to be persistent without being altered?

I've tried chmod with no avail.

Thanks.

---

### Post by Joshua on 2012-02-09
My home directory is shared with a pretty basic setup.

[homes]
        comment = Home Directories
        writable = Yes
        browseable = No
        create mask = 0750
        directory mask = 0750
        valid users = %D\%S

In your setup, I notice that you use a different slash than I do for separating domain and users.  I don't know if it's necessary, but I think it's supposed to be the one I use above.  Although, I think you can configure that setting with the "winbind separator" option.

Also, if you're having difficulty with permissions when creating files, you can try the "create mask = 0755" or something similar.

However, I've been having trouble with that option in my setup as well.

It's clear that my "hide unreadable = yes" option is what's causing files to disappear, but once they are readable by setting them to be "world readable", they are also editable.  Strangely, though, I cannot change the filename by using the right-click->rename option in the Windows file explorer.

After doing a lot of research and tinkering, I came across a note at:
[https://help.ubuntu.com/8.04/serverguide/C/user-management.html]("https://help.ubuntu.com/8.04/serverguide/C/user-management.html")

Under User Profile Security, it says that you only need to remove the world readable settings at the directory level, and that should prevent access by unauthorized users.  I'll probably go with that method, but it is still seems that Samba isn't recognizing users and groups correctly in my setup.  So I worry I'll run into other problems somewhere else.

---

### Post by Joshua on 2012-02-12
I've discovered something else.  The hide unreadable setting is not functioning properly for an old user with a low uid and gid (below the idmap range).  As I describe above, if hide unreadable is no, then the old user can see all of the appropriate files in his home directory as well as the other shares.  But if it's yes then the user only sees files that are world readable.  (clarification edit: that is he only sees files that are world readable even if he's in the file's group or is the actual owner.)

However, a new user with a uid and gid within the idmap range, seems to work properly with either setting.  Also, there may be something going on with the gid.  A new user with a uid within the idmap range but who is only in a group with a gid below the range, will behave like the old user above.

Lastly, this behavior seems to occur whether or not I include the idmap options in the global section.  The Active Directory Services on the primary domain controller include the Unix attributes for the appropriate users, so I would think Samba would just get those uids and gids from ADS and use them appropriately.  And Authentication with this configuration seems to work properly, samba only seems to have a problem when trying to apply permissions to files.

---

### Post by Joshua on 2012-02-15
I almost don't want to post this because it took me way to long to figure out.

Everything works perfectly if I get rid of winbind.

Windows Server 2008 Active Directory can already be set up with the "Unix Attributes" stuff (which I've already done).

Kerberos and LDAP already provide all the authentication information needed.

PAM works that info into the services that need it.

getent passwd and getent group always worked for me, and some of the Active Directory integration guides just confused me about needing winbind.  If my understanding is correct, winbind is only needed if you don't have Active Directory providing all the "Unix Attributes."

How did I figure this out?  I mistyped a command during testing:
sudo /etc/init.d/winbind strat

All of a sudden all my share permissions (and hidden shares) were behaving properly.  Then I noticed that I stRAt-ed winbind instead of stARt-ing it.

If there's an expert out there who sees this, I'd still be interested in someone confirming that my understanding is correct.

---

### Post by Joshua on 2012-02-15
> **Joshua said:**
> Also, if you're having difficulty with permissions when creating files, you can try the "create mask = 0755" or something similar.

However, I've been having trouble with that option in my setup as well.

ROBarber - After figuring everything out from my last post, I don't have problems with the "create mask" or "directory mask" options.  If I understood your question correctly, those options should allow you to force a user to create files that have permissions that allow other users access.

---

