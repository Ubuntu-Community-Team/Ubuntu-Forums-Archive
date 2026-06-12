---
title: "How can i use sudo without a password for non interactive login using plink"
date: 2010-06-02
forum: General Help
---

### Post by smay84 on 2010-06-02
Before you say you shouldn't do that bla bla bla.  I know why i shouldn't.

However i have a problem with running sudo commands from a non interactive command line script run using plink.

The automated script needs to use chown and give the current user ownership of some files and folders created by another user.

I can't use things like sudo -s etc as it requires that i enter a password.

I have setup public key authorization in order to login.  Do i have to give the root user a password and log in as that.  I would prefer not doing this but if that is the only solution i guess i'll have too.

---

### Post by colorlessprism on 2010-06-02
First the statement:
[IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=IconDialog-Warning1.png[/IMG]Enabling the root account is rarely necessary. Almost everything you need to do as administrator of an Ubuntu system can be done via sudo or gksu.

[IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=info.png[/IMG]HOWEVER:
If you really need a persistent root login, the best alternative is to simulate a root login shell using the following command...

*[FONT="Tahoma"][SIZE="4"]sudo -i[/SIZE][/FONT]*

To enable the root account (i.e. set a password) use:

*[FONT="Tahoma"][SIZE="4"]sudo passwd root[/SIZE][/FONT]*

Use at your own risk!

[IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=dont.png[/IMG]Logging in to X as root may cause very serious trouble. If you believe you need a root account to perform a certain action, please consult the official support channels first, to make sure there is not a better alternative.

[IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=IconWarning3.png[/IMG]Re-disabling your root account

If for some reason you have enabled your root account and wish to disable it again, use the following command in terminal...

*[FONT="Tahoma"][SIZE="4"]sudo usermod -p '!' root[/SIZE][/FONT]*

---

### Post by smay84 on 2010-06-02
Yeh i really didn't want to have to do that.

But i don't see any other way to do a non-interactive login that can use chown.

Is it possible to create a user that owns a directory and anything that is created within that directory?

The current problem is that i have the home directory /home/ftp which is owned by the user ftpadmin.  Then other ftp users have a home directory set to /home/ftp/user1

I want ftpadmin to own any file or folder created by user1.

---

### Post by colorlessprism on 2010-06-02
*i dont know how this will affect a folder in place, i always make a new folder for this process*
 i only know how to make it so all ftp users can access each other subdirectory, but this may work by just having "ftpadmin" in a ftp group.(note: i use this method to share a folder across 4 users on a desktop)

1. Change the umask in /etc/profile so that new files created by users will have write access granted to the group that owns the file:

sudo nano /etc/profile

change the last line so it looks like this:

umask 002

2. Make a new group "ftp" and include any usernames you want (try just adding ftpadmin) to be able to share the files in your shared directory in that group.

System->Administration->Users and Groups->[Manage Groups]->[Add group]

3. give all users in the group full access to the directory, and tell it make all files created within that directory to the group of the directory:

sudo chgrp ftp /home/ftp
sudo chmod 775 /home/ftp
sudo chmod g+s /home/ftp

4. Logout and log back in to make the group changes take effect.

At this point, all users that you added to the group should be able to create files in the shared folder, and edit files created in the shared folder by other users in the "ftp" group. 
users should still be able to access their own file because they own them, ftpadmin should be able to access all files because he is in the ftp group. i am not sure what happens if a user owns a file but he is not in the group that own the file. i would test this on another directory first (dont forget to change the commands to match w/e foldername you test with i.e /home/ftptest

---

### Post by rnerwein on 2010-06-02
hi
i think is that you want to run only some commands via sudo without a password - that's the way to implement it.
as root you have to edit your /etc/sudoers
at the [COLOR=Red]very last line[/COLOR] ( must be the very last line or the rule will be overwritten by other rules) you insert following:
[COLOR=Blue]your_account ALL=NOPASSWD: /path_to_your/command[COLOR=Red],[/COLOR]/path_to_your/other_command ..... etc.[/COLOR]
with command i mean the real commond where you need root-access - not your script !
this will cause the system to run the given commands as root ( sudo /path_to_your/command ) only for your account without asking for a password.
save that file ( be careful that you don't change the permissions of the sudouers file !! )
have fun
ciao

---

