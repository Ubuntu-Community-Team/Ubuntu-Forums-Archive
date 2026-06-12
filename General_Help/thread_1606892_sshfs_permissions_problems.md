---
title: "sshfs permissions problems"
date: 2010-10-27
forum: General Help
---

### Post by Simonpro on 2010-10-27
Hi all,
I'm new to Ubuntu (have previously been using OpenSuSE), and am finding Ubuntu to be nice and easy to use - but I do have one problem, which you guys can hopefully help me solve!

I need to access folders on a remote server, and I did it as follows:
sudo mkdir /media/Remote/
cd /media/
sudo chmod 777 Remote/
sshfs [EMAIL="user@remote.comput"]user@remote.comput[/EMAIL]er:/Folder /media/Remote/

Now the sshfs'd folder appears on the desktop, and is correctly populated with the files on the remote computer.
However, there seems to be some problems with the file permissions. I can delete files on the remote server (either using rm or through nautilus) and I can create files. But I cannot modify files.
For instance, if I open a file on the remote computer using GEdit then when I try to save the changes I make it says that I do not have permission to do this. Same if I drag a local file into the remote folder using Nautilus, if the file already exists then it won't overwrite it. I simply get a permissions error.
I also noticed that when moving files to the remote server (using a command like mv /home/name/myfolder/* /media/Remote/Temp/ ) then it will move the file, but give an error saying that it cannot create the correct permissions.


I didn't have this issue on OpenSuSE, which makes me think that I'm doing something wrong now that I'm using Ubuntu..so I'd be super-grateful if someone could point me in the right direction.:)

Thanks!


PS: Apologies if this is in the wrong forum.


(edit) And before I posted this I did a search for others who had the same issue. I saw a few posts discussing the use of the "sudo adduser (username) fuse", but I tried that and had no luck.

---

### Post by spikoley on 2010-10-27
What are the permissions of the files?  Run the following command and post the results.

```
ls -la /media/Remote/
```

My guess is the files in the Remote folder didn't change permissions when you ran the chmod command.  If the files don't have the correct permissions add the switch -R to the chmod command.

```
chmod -R /media/Remote/
```

Beware because it will recursively change the permissions for every file in that directory.

---

### Post by Simonpro on 2010-10-27
Thanks for your reply!

The results of ls -la are all like the following:
-rwxrwxrwx 1  500  500  2167 2010-10-27 12:01 gdal_arrange.pro
drwxrwxrwx 1  500  500  4096 2010-10-26 09:21 IDL_HNS
drwx------ 1  500  500  4096 2010-10-26 10:46 RT_MSG
drwxr-xr-x 1  500  500 57344 2010-09-30 15:03 TOOLS
drwxrwxr-x 1  500  500 12288 2010-10-27 11:45 WA

The gdal_arrange.pro file is that which I've tried to edit in Gedit, etc. To me the permissions look okay, and are as expected.
I tried running the chmod -R command anyway, and I'm still having the same problem.

What is confusing to me is that exactly the same set of commands that I posed in the OP work fine on OpenSuSE 11.1, but not on Ubuntu 10.10. I like Ubuntu a lot, so really don't want to have to go back to SuSE if I can avoid it!!

Cheers.

---

### Post by spikoley on 2010-10-27
Is your ssh user name part of the 500 group?

> -rwxrwxrwx 1 [COLOR="Red"]**500 500**[/COLOR] 2167 2010-10-27 12:01 gdal_arrange.pro

The permissions are set to 777, so you should have access.  I am not sure what is causing this issue.  Maybe you should create a new group for that folder and add all the users who need access to that group.

---

