---
title: "Need help sharing folder with other local user"
date: 2010-01-11
forum: General Help
---

### Post by kseise on 2010-01-11
My wife and I share a computer that houses our family photos etc.  Since I am the geek, I am in charge of downloading the camera.  I want to share the photos under my /home/username/Pictures file with my wife.  Can someone help me with this?  I have tried chmod 0755 and chmod 0777.  Neither one works.  I get a permission denied error when trying to access as her.

---

### Post by garryknight on 2010-01-11
You could both access the directory if it's owned by a group that you both belong to. You could set up a group specifically for that purpose, or use the existing 'users' group. You can use whatever GUI dialog your version of ubuntu provides for adding the two of you to that group, or you could use the command line.

Since you don't say whether you use Gnome, KDE, or another desktop, I can't help you with the GUI option. But if you're happy using the command line to do the job, here are the commands you'd need:

su
[enter password]
chgrp users /home/username/Pictures
usermod -G users myusername
usermod -G users herusername

This is the standard Unix way of handling situations like yours and is why we have both users *and* groups on the system.

---

### Post by kseise on 2010-01-11
Thank you for the reply.  I am using gnome if that helps.  I did try what you said from the commandline.  I still get the following error.
```
$ cd /home/username/Pictures
cd: 1: can't cd to /home/username/Pictures

```

Any other ideas?

---

### Post by Morbius1 on 2010-01-11
Pardon the interruption but I think garryknight meant to mean your username.

If you logon with the username kseise, then the command would be:

cd /home/kseise/Pictures

---

### Post by kseise on 2010-01-11
> **Morbius1 said:**
> Pardon the interruption but I think garryknight meant to mean your username.

If you logon with the username kseise, then the command would be:

cd /home/kseise/Pictures

Thanks.  I know that though.  I was just keeping it generic for anyone who might read this in the future.  But yes, I was using /home/kseise/Pictures and it still doesn't work.  Any other ideas?

---

### Post by Morbius1 on 2010-01-11
What is the output of the following command:

```
ls -l /home/kseise
```

---

### Post by kseise on 2010-01-11
The relavent part is:
> drwxr-xr-x  91 kseise users      4096 2010-01-11 14:38 Pictures

---

### Post by kseise on 2010-01-11
Interesting thing happening now.  I am being told that I am not in the Sudoers list.  I am the only admin on the machine.  I am connecting by ssh.

---

### Post by mongo72 on 2010-01-11
Is it perhaps a permission problem on the home directory in which the Pictures sub-directory lives?

Try making sure the /home/username directory has execute permissions in addition to to the Pictures subdirectory.

---

### Post by polki@mac.com on 2010-01-12
I think you need to use -a (append) together with -G when using usermod. 'usermod -G somegroup' makes you a member of that group only.

---

### Post by garryknight on 2010-01-12
Whoops, sorry! My fault. I should have remembered that. Shows how long it is since I used usermod.

**kseise**: You can type 'groups' in a console to see which groups you're a member of. If you're only in the users group now, here's a list of the groups I belong to, which should be similar to what your list would have been before using the usermod command:

users adm dialout cdrom sudo audio video plugdev lpadmin admin sambashare

To get membership of the sudo group, I expect you need to be root when you issue the usermod command. So you can do
```

sudo usermod -a -G users,adm,dialout,cdrom,sudo,audio,video,plugdev,lpadmin,admin,sambashare kseise

``` to reinstate your group ownership.

---

### Post by michy99 on 2010-01-12
You can't use sudo to add yourself to the admin group because you have to be in the admin group to use sudo. You need to boot into a recovery session and add yourself to the admin group from there.

---

### Post by kseise on 2010-01-18
You are absolutely correct.  You need to have the -a switch with the -G switch.  Getting back on the sudoers list was a pain.  Grub2 now hides the menu by default.  

[LIST=1]
[*]Here is how to get into the recovery shell in Karmic (9.10)
[*]Reboot the machine.  
[*]Hold down SHIFT while it is rebooting
[*]When you see the menu, pick the recovery console option.
[*]Once you are in the recovery console, run "visudo".  Find the line that says

root    ALL=(ALL) ALL

[*]add a line like this:
username    ALL=(ALL) ALL 

right beneath it.  Don't forget to delete that line when you are finally done and running normally again.
[*] hit CTRL+X to exit
[*] hit enter to accept the default save-as target
[*] Reboot as normal
[*] When the machine comes back up, add youself to the administrator group and whatever else you need. (If someone can list the default groups, that would be tremendously helpful for this situation).  My groups were "kseise adm dialout cdrom plugdev fuse lpadmin admin sambashare users"
[*] You might need to logout and log back in to make all the changes take effect.
[/LIST]
 
With all of that said, I still have a problem.  I have created a symlink in her /home/wife directory to link Pictures to the /home/kseise/Pictures directory.

My wife can browse the folder while logged into the desktop, but I want to be able to share if by means of sshfs.  No matter how I try to make this work, I get a variety of errors.  My closest effort gives me a message about not having permission to access this folder.  Any help?

---

