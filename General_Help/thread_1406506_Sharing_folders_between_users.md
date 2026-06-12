---
title: "Sharing folders between users"
date: 2010-02-14
forum: General Help
---

### Post by sunrise-7 on 2010-02-14
I am using Ubuntu 9.10 desktop.
I set up my main user- admin and loaded the folders of files I would be working on and the relevant additional programs.
Now, I would like to set up a second user so that someone else can use the computer with access to many of my files and folders, but not all, which would defeat having a second user.
I have set sharing preferences for all of my folders.
I have giving most rights to my second user.
Yet the second user cannot even see ANY of my folders when they sign-in.
Any suggestions. Thanks.

---

### Post by Ordes on 2010-02-14
what u mean with "allowed sharing"? u changed the permissions for those files, or you allowed samba share?

1. if samba share, than they are in your network
 smb://127.0.0.1  (localhost) or
 smb:// your internal-IP

2. If permissions, than u have to make sure the user has permission to the whole path. e.g your /home/user would have 700 > groups & others cannot access, therefore they cannot access subfolder /home/user/documents

700 = read(4) + write (2) + execute (1) for users, groups=0; others=0; XYZ = User, Group, Others

You can make 
chmod -R 710 /home/user (means groups will have execute rights, like opening the folder, but they cannot read the content);
Make symbolic links of the folders u allow them to  have access and put them into their home. Than give a 750 or 770 for those folders. Depending if you want them to give read or read and write permissions.


also the users have to be inside the assigned "group";
chown -R user:group folder  [>> -R = recursive; for included folder content]

---

### Post by azertyh on 2010-02-14
hi,
sharing your home folder is not recommended.
but you can create a folder that all users have access. i do that by typing these commands :

```
john@ordinateur:~$ sudo -s
[sudo] password for john:
root@ordinateur:~# addgroup partageurs
root@ordinateur:~# adduser john partageurs
root@ordinateur:~# adduser mary partageurs

root@ordinateur:~# echo "umask 0002" >> /etc/profile

root@ordinateur:~# mkdir /home/Partage
root@ordinateur:~# chgrp -R partageurs /home/Partage
root@ordinateur:~# chmod -R g+rwx,o-rwx /home/Partage
root@ordinateur:~# chmod -R g+s /home/Partage
root@ordinateur:~# exit
exit
john@ordinateur:~$
```

the explanation of these commands is in this **french** tutorial :  [HTML]http://doc.ubuntu-fr.org/tutoriel/dossier_de_partage?s[]=partager&s[]=dossier[/HTML].

---

### Post by Ordes on 2010-02-14
with the right permissions, there is nothing to worry

---

### Post by sunrise-7 on 2010-02-16
I've been away from e-mail for a few days.
Thanks for the replies and attempts.

1. I have set up second and third users to Share some of my laptop or desktop files and folders for a decade with Windows XP, in seconds, with never a problem. I was hoping something comparable was possible in Ubuntu. Answer seems to be "Very Wrong"!

2. I had done many searches through the forums on the topic of sharing between users ... and consistently received NO answers, then, I posted.

3. An online Linux Manual is likely available, but I don't see one on this site. Would be a huge help. Even better if there were tutorial sections for newbies, general reference, and persons like myself who are doing a MAJOR conversion of thousands of files from a Windows system to a Linux one including learning the use of new, and the idiosyncracies of Linux versions of programs formerly used on Windows.

I DID find a version, saved from my second last major attempt, 10 years ago at
[http://stommel.tamu.edu/~baum/programming.html]("http://stommel.tamu.edu/%7Ebaum/programming.html")
and a better, more relevant one at:
[http://www.debian.org/doc/manuals/reference/ch01.en.html#_filesystem_permissions](http://www.debian.org/doc/manuals/reference/ch01.en.html#_filesystem_permissions)

I am really not looking to spend weeks learning how to program enough to be a technical administrator.


4. I appreciate the coding suggestion provided by azertyh
I have 12 folders with 38,000 files and wish to share 2/3rds with an associate, yet not make them a full administrator. I have the files and folders in MY User group accessed by MY password. It seems wasteful to duplicate the folders in storage to provide two sets, which defeats the purpose of Sharing, if the other person has write permissions, yet we are saving in TWO locations! Sorry if I am missing something here.

5. I DID set up Permissions both within the System/Administration/Users and Groups/
Manage Groups/Group Settings ... as well as within my HOME folder, not the Root, both with newly assigned Groups and using what I had with a new User designation added. At one point I got to a point where a message indicated that my filenames were too long to share (??!!) yet I could find no guideline for length. I DID shorten the filenames of the major folders, generating much future work in changing interfile links, unless I change them back. Nothing still worked, so I backed out everything, eliminated the added User, added Groups, and removing the Share designations on the folders. A lot of time taken for what can hopefully, someday, be simple.

6. A statement like "Just set the Preferences correctly and it will work" is like saying "All we need is world peace and we won't have any wars!" If it were THAT easy, I would have done it in the first 15 minutes, not after more than 6 hours of monkeying and searching and reading. I'm not the only one at this stage.

7. Maybe I am the odd person out who actually considers Sharing their desktop or laptop and the rest of the Linux community simply keep their computers to themselves, unless sharing with someone on a network or more distant. The use of Samba is unintelligible to me. Why? I have used Samba for 2 years to communicate daily between Windows XP and Ubuntu 6.04, on the SAME computer. My understanding is that Samba is used for Windows-Linux communication, not Linux-Linux .. but, I could be wrong.

At this point I don't wish to risk messing up what I have with more experimentation and I don't have the time to delve into the programming, as the point of the conversion was to SAVE time lost through continual Windows maintenance. I am leaving further involvement until I find a local Linux hero, or more time.

---

### Post by ubername on 2010-02-16
I am not sure I understand what you are trying to do - Can I set out what I think you may be trying to achieve, and then see if we can help? It is quite confusing trying to clearly state what is going on with the overlap of meaning of words like 'sharing' 'permissions' 'loaded the files' 'given the user rights' etc.

Is the scenario:

One computer - no need currently to share files/folders over a network.

Two (or more) users. One ('Admin') you have used to copy the files onto the computer?

Suppose you have copied them into a folder within the 'Admin' user's home folder.
 Logged on as Admin, go to your file manager program (which is called Nautilus in normal Ubuntu. If you can see the folder, right click on it and select properties. Go to the permissions tab and (for testing purposes) let 'others' have 'read-and-write' access. It may be called 'create and delete files' depending on which version of Nautilus you are using.

Now, logout of Admin and login as your other user. To see the files which you have just allowed the user to see, go to the file manager (Nautilus) and, from the other users 'home folder, you need to go up one level in the folder hierarchy.
You should be in a folder called 'home, with two sub-folders, one named admin and one named whatever the other user is called. Go into admin and see if you can access the files.

If this is what you have already tried and is not working, apologies, but it wasn't clear from your first post.

---

### Post by Morbius1 on 2010-02-16
OK, I'll be the first one to admit that I'm very confused.

I still don't know if by "sharing" you're talking about sharing directories across your home network or accessing directories between local users on the same box.

In your original post , for example you stated this:
> Now, I would like to set up a second user so that someone else can use the computer with access to many of my files and folders, but not all, which would defeat having a second user.
I have set sharing preferences for all of my folders.This first sentence implies access to folders between two local users.
The second sentence implies sharing folders across the network.

Perhaps it's the phrasing between windows and linux or if you're using KDE not Gnome but sharing has two different meanings.

---

### Post by sunrise-7 on 2010-02-17
Yes, Ubername, you have ALL of the details correct as I was attempting to outline them.
Yes, I did everything exactly as you have itemized, except, did not find any access to ANY of the folders in the HOME directory from the second user.

If there is still any confusion with terms, NO, I am not using a network, only ONE computer.

This would seem to not be a simple problem, or I would have found the answer before coming here, or, a simpler one would have surfaced here. Terminology IS a critical element to understanding on all the Forum pages and thanks for considering that. Reading rather than skimming is also important and a few special people do that.

I am satisfied with setting this aside for now and encouraging whomever can contribute to the programming to add in a routine that would make such an endeavor, setting up a second user on the same computer, a choice rather than a code editing process.

---

### Post by ubername on 2010-03-10
Hi 
Sorry for the time to respond.

What you are trying to do is quite normal, and if it is not working as I have described above, then unfortunately there is something broken with your installation. Without a lot more information this will be hard to fix. Depending on how you have installed Ubuntu it might well be easier to do a fresh install.

Just one point though: In your post you mention not having any access to the shared folders from the second user's home (at least, I think that's what you described.) Please note that you will not see the folders in the second users home. You need to use Nautilus to navigate up to the directory above the second user's home directory and then 'down' to the 'admin' user's home directory. The path name would be /home/admin, but please note you do not need to type this anywhere if you are using nautilus (depending how you have nautilus set up, you may see two buttons above the file display pane, one saying home and then one saying admin, if you are in the right place).

---

