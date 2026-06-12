---
title: "Copying user profile"
date: 2009-07-14
forum: General Help
---

### Post by jfreak53 on 2009-07-14
Ok here is the scenario I would like to do.  I have 3 pc's that I have to redo constantly because of prying fingers.  So what I want to do is make a template profile and once in awhile manually using my admin user copy that template over the top of the user profile that is used by the users.  How can I do this, copy a profile completely, settings and all, basically the whole dir with program settings.  I tried just copying all files in the home dir but I got a bunch of errors, one being the .htdc file I think it was and another that I cannot remember.  Is there a way to do this?

Thanks in advance.

---

### Post by jfreak53 on 2009-07-15
Anyone got anything for me?  I found a lot of backup ways using a tarball to make a backup.  But I want an actual profile that I can log into and make changes to that I can then copy to another one.  In another thread they said that this can break things?  Howso?

---

### Post by vinutux on 2009-07-15
copying /home/yousername is idile solution....but 

i did't get u....make it clear........

which apps profile u want to copy..etc

---

### Post by jfreak53 on 2009-07-16
All of them, I want to make an exact duplicate of the current user, program settings and gnome and system settings, all the settings of the one user for programs and system I want to copy to the other, completely, leaving nothing out.  Sorry if I wasn't clear in what I was looking for.

---

### Post by scouser73 on 2009-07-16
Hi, I have been using a program called Pybackpack to backup my home folder, this can also be used to backup any files to drives or removable media.

[http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html")

It's well worth taking a look.

---

### Post by vinutux on 2009-07-16
Okey...Alt+F2 the type **[COLOR="Sienna"]gksu nautilus[/COLOR]**

give password and a window pop-up (file browser aka nautilus with root previlage) go to /home Copy your [COLOR="Red"]username[/COLOR] folder (if your usename peter it is /home/peter) and paste it in perdrive or externel harddisk etc

in Other system copy folder and paste it via same way (gksu nautilus)...

.

---

### Post by HotForLinux on 2009-07-16
> **vinutux said:**
> Okey...Alt+F2 the type **[COLOR=Sienna]gksu nautilus[/COLOR]**

give password and a window pop-up (file browser aka nautilus with root previlage) go to /home Copy your [COLOR=Red]username[/COLOR] folder (if your usename peter it is /home/peter) and paste it in perdrive or externel harddisk etc

in Other system copy folder and paste it via same way (gksu nautilus)...

.

Maybe that's what he did before. If so then it doesn't surprise me he got a bunch of errors.
You need to copy hidden files too. Once in nautilus type Ctrl-H or go to its menu and select view hidden files. After that copy everything, the whole user's dir, wherever you want to. That may be a little risky, or work more or less well, if the other  system is not the same with the same version of the applications.

---

### Post by jfreak53 on 2009-07-16
Ok, I did all of that once already.  I, using gksu naut, copied everything from my dir, including hidden files.  No problem there.  But I don't want to paste them onto another computer, on the same pc I want to have another user that I paste them onto, basically another identical user, and no I don't want them using the same home dirs.  I need separate home dirs so the original template stays untouched.  But when I do it this way and paste onto the other user, I get so many errors when logging into the other user it's not even funny.

So my question is, is there an easier way to "DUPLICATE" users on the same install?  Maybe a program out there that does it.  Or something built into ubuntu.  I mean come on, Windows figured it out :lolflag:

Why can't linux??!!  I'm not bashing, I love linux and now ubuntu over windows any day, it's way better.  But I know there has to be a way to do this without problems arising, has to be.  Like I said, Microcrap figured it out in windows, why can't we? :confused:

Thanks for all the ideas guys.

---

### Post by vinutux on 2009-07-17
> **jfreak53 said:**
> Ok, I did all of that once already.  I, using gksu naut, copied everything from my dir, including hidden files.  No problem there.  But I don't want to paste them onto another computer, on the same pc I want to have another user that I paste them onto, basically another identical user, and no I don't want them using the same home dirs.  I need separate home dirs so the original template stays untouched.  But when I do it this way and paste onto the other user, I get so many errors when logging into the other user it's not even funny.

So my question is, is there an easier way to "DUPLICATE" users on the same install?  Maybe a program out there that does it.  Or something built into ubuntu.  I mean come on, Windows figured it out :lolflag:

[COLOR="Red"]Why can't linux[/COLOR]??!!  I'm not bashing, I love linux and now ubuntu over windows any day, it's way better.  But I know there has to be a way to do this without problems arising, has to be.  Like I said, Microcrap figured it out in windows, why can't we? :confused:

Thanks for all the ideas guys.

I think.....Duplicate user is an crazy idea ...
perhaps there is a fix...just googling it....

---

### Post by renkinjutsu on 2009-07-17
you can probably set something up where they can all share ONE home folder.. It's not uncommon for people to mount the same /home folder on multiple machines over NFS .. but you can mount it locally if all the users are on the same machine.

---

### Post by hyperdude111 on 2009-07-17
You can use remastersys to make an exact imgae of your current system then install it else were.

---

### Post by HotForLinux on 2009-07-22
> **jfreak53 said:**
> ... and no I don't want them using the same home dirs.  I need separate home dirs so the original template stays untouched.  But when I do it this way and paste onto the other user, I get so many errors when logging into the other user it's not even funny.

So my question is, is there an easier way to "DUPLICATE" users on the same install?  Maybe a program out there that does it.  Or something built into ubuntu.  I mean come on, 

I don't understand ver y well what you say and want.
What are you calling home dir?? The "/home" dir or the "/home/myself" or whatever and wherever else "home dir" of each user?

Maybe copying the contents of one dir into the other is not working because some hidden files have the name of the original user in them....I don't know. But you should check and also try several times copying little by little more files each time to see which one or which group is giving the problem.

_**Also**_ you should be careful about what you are doing with the permissions of each file?
You haven't explaines here what and how are you doing it. Please be much more clear and don't explain thinks like a story, but step by step with accuracy.

---

### Post by jfreak53 on 2009-07-24
Ok what I'm doing is this.  I'm creating a user in ubuntu with limited permissions.  Then I log into the user change all the options and make it exactly configured the way I want it to be for that user.  Then I log out and go back into my admin user.  I then create a new user with the same permissions as the last user I just created.  I then after logging in once to this NEW user I log out and go back into my admin and go to the file manager.  I then show all hidden files.  Then I just select everything from my first user, the one I call the template user and then copy it and paste it in the directory of the second user.  By user directory I mean, /home/user not just /home.  I mean the actual directory with all the settings of that user. I copy everything in that directory like /home/user/* to /home/user2 and that's it.  When it starts it gives me errors.  Oh it will start after a few errors but if I remember right the settings for the desktop aren't the same.

---

### Post by michy99 on 2009-07-24
Files created in user1's home will be owned by user1. If you copy them to user2's home, they are still owned by user1. I don't think this idea will work at all. You would have to chown every file that you copy over. I guess maybe it could work if you did that.

---

### Post by NewbieNik on 2009-07-24
Jfreak,

Can't help you, but just to say Windows never solved this, the only reason this works in Windows is because the security is so....."wanting" (Trust me, I am a MCSE..sorry guys, traitor in the midst)
Linux has a lot more security to the user so copying another users folder into place won't work, however I'm sure someone here can tell you how to make a generic new user template with all the settings you wnat or need.

---

### Post by HotForLinux on 2009-07-25
Let's say you have this user: admin
and want to create user1, user2 with same preferences and configs.

GO STEP BY STEP

**admin:**
0. Log in admin.
1. admin creates user1 and user2.
2. Log out admin.

**user1:**
3. Log in as user1, through the graphical login (if you want those users to use the graphical desktop)
4. Configure his desktop and change its preferences as you like.
5. Log out user 1

**admin:**
6. Log in admin
7. _Before_ user2 logs in (you don't need him to log in now!) Copy all /home/user1, including hidden files, to /home/user2 like this:

```
you@belice:~$ **sudo cp -a --remove-destination  /home/user1/*   /home/user2/**

```8. Have a look to all the details: owner, group, permissions, links,.... you  can from the list of hidden files in both user's directories:
 
 ```

[B]cd /home/user1
ls -a|grep ^[.]|xargs ls -dl[/B]

[COLOR=Gray]and[/COLOR]

[B]cd /home/user2
 ls -a|grep ^[.]|xargs ls -dl[/B]

```Do you see that everything is identical?
But you don't want it identical, right?. You want it _symmetrical_

9. With super powers, change ownership of all the files in user2's home that belong to user1 and only those (not the root thing

```
you@belice:~$ **sudo chown -Rh --from=user1 user2:user2 /home/user2/**

```[B]

user2:[/B]
10. Log in

**11. Post results**

---

### Post by jfreak53 on 2009-07-27
I will try this last post and post back how it worked! Thanks! :P

---

