---
title: "A little help with users and file permissions?"
date: 2010-11-08
forum: General Help
---

### Post by Hawkoon on 2010-11-08
I have four local user accounts on my system (A, B1, B2 and C) and I would like to restrict file access as follows:
A can access everyones files
B1 can access B1 and C
B2 can access B2 and C
C can access only C

How can I do that? I read about umask and groups but I cannot see yet how to achieve the desired behaviour.

I hope soemone can give me some pointers.

Thanks,
Hawkoon

---

### Post by searchfgold6789 on 2010-11-08
You can achieve this by putting the users into groups, and changing the ownerships of the files to the specified group.
I'm not sure how to tell you how to do this though. Try ```
man chown
```

---

### Post by 3Miro on 2010-11-08
Make four users: A with group A, B1 with group B1, B2 with group B2, and C with group C.

Let the umask for A be 077 (only user A can access files from A). Then for B1 and B2 use umask 007 (B1 and B2 can access files from their own folders and members of groups B1 and B2 can access those files as well). For C you can use 007 or 000 (last one meaning anyone can access files that belong to C).

Then you can make A member of groups B1, B2, and C, so that A can access files for everyone. Since B1, B2 and C are not A, they will not be able to access A's files.  If you use 007 for C, then make A, B1 and B2 members of group C, so that they can access C's files. C is not a member of any of the other groups so C always falls in the umask 7 category (i.e. cannot access).

Hope this is not your homework.

---

### Post by Hawkoon on 2010-11-08
> Hope this is not your homework. 

Thanks for your help 3Miro. No worries, this is a new hobby of mine. I havent been to school for a long time, maybe I ought to do that again if I wanna take this "hobby" further. I used those abstract account names to focus on what my problem is.

It is clear now how groups work, thanks for the explanation. But how can I have user dependant umask values? I run an old 8.10 Ubuntu. I have the /etc/profile file and in there is only a single umask value at the very end (umask 022) that applies to all users.

I read about .bashcr in the user space to implement a user specific umask, but I dont get that file when I create a user account. Besides that, I dont know if a user must be granted write access to his/her .bashcr file. If yes, the user could alter the umask but he/she should not be able to do that on my system.

---

### Post by 3Miro on 2010-11-08
umask counts only as a default setting for newly created files. Not all files in your folder have to comply with the umask, for example in Ubuntu all files use umask 022, which means that they have permission 644 (or 755 for folders), however, .ssh has 700 permissions. You can create the .bashrc files in every user's home folder and set it as 600, which will disallow for anyone else to modify it (except root of course). In the .bashrc you can set different umask for every individual user.

---

### Post by Hawkoon on 2010-11-08
OK, it is partly working now. The custom umask is only applied when creating files from a terminal session. If I download a file, create one with OpenOffice or via right-click in Nautilus, the system wide umask 0022 is applied again. Do you know what else I need to change so that every file create by a user goes through my custom umask?

Thanks for your help, I am almost there.

---

### Post by 3Miro on 2010-11-08
In order to make changes to .bashrc permanent, you have to logout and then back in. .bashrc is read on login for every individual user and doesn't update on the fly (I think there is a special command for it, but I am not sure).

---

### Post by Hawkoon on 2010-11-08
> **3Miro said:**
> In order to make changes to .bashrc permanent, you have to logout and then back in. .bashrc is read on login for every individual user and doesn't update on the fly (I think there is a special command for it, but I am not sure).

I do logout and then back in. When I create a file from a terminal like ```
gedit file1
```
then file1 has the permissons that I specify in ~/.bashrc - so that is working fine.

But if I create a new OpenOffice file, my user umask in .bashrc is ignored, instead umask 0022 (the system default) is used. Looks like I need to change the umask in some other place too, but where?

---

### Post by 3Miro on 2010-11-09
Unless there is something in GDM, I don't know. The only think that I can think of is that GDM (graphical login) somehow bypasses .bashrc. On my desktop, I don't use GDM, just a shell and startx and umaks works.

---

### Post by Morbius1 on 2010-11-09
3Miro, I don't know if you can confirm this but as I recall umask is the default but it can be overridden if the process or application was written to do so. I think that OpenOffice has it's own ideas of how files should be saved.

I'm doing this from memory so I will not be offended if you tell me I'm wrong :wink:

---

### Post by 3Miro on 2010-11-09
> **Morbius1 said:**
> 3Miro, I don't know if you can confirm this but as I recall umask is the default but it can be overridden if the process or application was written to do so. I think that OpenOffice has it's own ideas of how files should be saved.

I'm doing this from memory so I will not be offended if you tell me I'm wrong :wink:

If I don't forget, I will test Open Office and umask tonight. Other than that, I really don't know. One would think that the environment should be able to specify umask independent of the applications, but still, you may be right.

---

### Post by Hawkoon on 2010-11-09
> **3Miro said:**
> If I don't forget, I will test Open Office and umask tonight. Other than that, I really don't know. One would think that the environment should be able to specify umask independent of the applications, but still, you may be right.

So I dumped ~/.bashrc now and created ~/.profile instead with my custom umask and now it is working. My umask is now used for any application creating files (well, I tested it with Firefox, Gimp, terminal and OpenOffice).

I probably should copy the other stuff in /etc/profile into ~/.profile just in case ~/.profile superseeds /etc/profile.

---

### Post by 3Miro on 2010-11-09
> **Hawkoon said:**
> So I dumped ~/.bashrc now and created ~/.profile instead with my custom umask and now it is working. My umask is now used for any application creating files (well, I tested it with Firefox, Gimp, terminal and OpenOffice).

I probably should copy the other stuff in /etc/profile into ~/.profile just in case ~/.profile superseeds /etc/profile.

Great, I learned something new.

---

