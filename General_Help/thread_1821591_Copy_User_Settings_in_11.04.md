---
title: "Copy User Settings in 11.04"
date: 2011-08-09
forum: General Help
---

### Post by rchar66 on 2011-08-09
Hi everybody,

I'm looking for the easiest or cleanest way to copy a user's settings to a new user's settings. I don't need to copy any files from the original user, but setting up a home directory would be great.

If it's done at the command line, that would be just fine. I'm very familiar with working at the command line.

Thanks,
Richard

---

### Post by drewsus on 2011-08-09
Are you looking to duplicate these settings for a new, seperate user, or do you want to, for instance, reinstall the OS but retain most user specific settings?

---

### Post by ankspo71 on 2011-08-09
Hi,
The /etc/skel directory can be used to copy your settings into. Everything placed in /etc/skel will be used as default files, directories, and settings for all "future" users. This has no effect on current users on the system. [http://www.linfo.org/etc_skel.html](http://www.linfo.org/etc_skel.html)

Now when a user account is created with 'adduser' or 'useradd' those files in /etc/skel will be added to their home folders.

james@Kubuntu:~$ **sudo adduser johndoe**
[sudo] password for james: **<my sudo password>**
Adding user `johndoe' ...
Adding new group `johndoe' (1002) ...
Adding new user `johndoe' (1002) with group `johndoe' ...
Creating home directory `/home/johndoe' ...
[COLOR="Red"]**Copying files from `/etc/skel' ...**[/COLOR]
Enter new UNIX password: **<johndoe's password goes here>**
Retype new UNIX password: **<johndoe's password goes here>**
passwd: password updated successfully
Changing the user information for johndoe
Enter the new value, or press ENTER for the default
        Full Name []: **John Doe**
        Room Number []: 
        Work Phone []: 
        Home Phone []: 
        Other []: 
Is the information correct? [Y/n] **y**

---

### Post by drewsus on 2011-08-09
Ah, thats helpful stuff for me! Thanks my man!

---

### Post by rchar66 on 2011-08-09
What I want to do is duplicate my settings only for one user. I don't want to have every new user use the same settings as me.

Thanks,
Richard

---

### Post by drewsus on 2011-08-09
then make a copy of skel before you modify it... then modify it, make a new user and then change it back...

---

### Post by fdrake on 2011-08-09
i may b ewrong but all users configurations  are stored in the users home folder and are hidden(.*). that said if you do :
(let's say we have 2 user john & mary. we want mary to have johns settings)
```

# cp -R /home/john/.* /home/mary/
# rm -r /home/mary/.*
# chown -R mary /home/mary/*

```
login to mary's account and you shall see john's congirurations.
2 things to notice:
1-attention doing this may also import (configuratiosn) from firefox and other programs.
2- the hidden files from john's home directory, may not be all config file. but just hidden files created by john(files that he does not want to share.).

---

### Post by drewsus on 2011-08-09
> **fdrake said:**
> i may b ewrong but all users configurations  are stored in the users home folder and are hidden(.*). that said if you do :
(let's say we have 2 user john & mary. we want mary to have johns settings)
```

# cp -R /home/john/.* /home/mary/
# chown -R mary /home/mary/

```
login to mary's account and you shall see john's congirurations.
attention doing this may also import (configuratiosn) from firefox and other programs.

I dont think that will work as file permission may be set for the original user. 
If you do: 
```
echo $UID
```
you get 1000 for the first user, and I believe one higher for each new users. If you copy these to a different users home directory, all your permissions will be messed up. 
That being said, you can do recursive "chown" commands after the fact to fix this im sure. 
Just a heads up/something to think about.

---

### Post by fdrake on 2011-08-09
> **drewsus said:**
> I dont think that will work as file permission may be set for the original user. 
If you do: 
```
echo $UID
```
you get 1000 for the first user, and I believe one higher for each new users. If you copy these to a different users home directory, all your permissions will be messed up. 
That being said, you can do recursive "chown" commands after the fact to fix this im sure. 
Just a heads up/something to think about.

that's what id did : root chown the file to mary from john.

uid, pass and stuff like that aren't stored in the home, so there should be no problem.

---

### Post by drewsus on 2011-08-09
ha, so you did, my bad. 
at least he knows why now.

---

### Post by fdrake on 2011-08-09
this reminds me of when ppl want to partition their home folder so they can make an image of it and back up their configurations without doing that all over again in case of a crash. i am trying this on 2 useless users on my machine and let you know.

---

### Post by rchar66 on 2011-08-10
> **fdrake said:**
> i may b ewrong but all users configurations  are stored in the users home folder and are hidden(.*). that said if you do :
(let's say we have 2 user john & mary. we want mary to have johns settings)
```

# cp -R /home/john/.* /home/mary/
# rm -r /home/mary/.*
# chown -R mary /home/mary/*

```
login to mary's account and you shall see john's congirurations.
2 things to notice:
1-attention doing this may also import (configuratiosn) from firefox and other programs.
2- the hidden files from john's home directory, may not be all config file. but just hidden files created by john(files that he does not want to share.).

Thanks fdrake, this is what I was looking for.

I'm assuming I should do these commands after I create the new user, correct?

Thanks to everyone for there input as well.
Richard

---

### Post by fdrake on 2011-08-10
> **rchar66 said:**
> Thanks fdrake, this is what I was looking for.

I'm assuming I should do these commands after I create the new user, correct?

Thanks to everyone for there input as well.
Richard
There is a problem with my commands. I tested them so I don't suggest u to follow them.
Don't why but it looks like the chown com has changed my whole home folder.
.*   was interpreted as /..

---

### Post by ankspo71 on 2011-08-10
Wow, I didn't know chown was that sneaky. This is a surprise to me too. I looked it up and found out that '-R' and '.*' can't be used with chown, because chown will recursively follow every file or directory that begins with a dot, including working its way back up into the '..' parent directory. And on the same link it talks about how the '-R 'and '*' chown command ignores hidden files.

Here's the info I found:
[http://serverfault.com/questions/156437/how-to-chown-a-directory-recursively-including-hidden-files-or-directories](http://serverfault.com/questions/156437/how-to-chown-a-directory-recursively-including-hidden-files-or-directories). 

I just followed Hamish Downer's example and it worked for me.

PS: Now that I have read what you posted, I'm not sure why you would want to delete Mary's files after you just copied them there from John's folder.

---

### Post by fdrake on 2011-08-10
> **ankspo71 said:**
> Wow, I didn't know chown was that sneaky. This is a   [INDENT][/INDENT]surprise to me too. I looked it up and found out that '-R' and '.*' can't be used with chown, because chown will recursively follow every file or directory that begins with a dot, including working its way back up into the '..' parent directory. And on the same link it talks about how the '-R 'and '*' chown command ignores hidden files.

Here's the info I found:
[http://serverfault.com/questions/156437/how-to-chown-a-directory-recursively-including-hidden-files-or-directories](http://serverfault.com/questions/156437/how-to-chown-a-directory-recursively-including-hidden-files-or-directories). 

I just followed Hamish Downer's example and it worked for me.

PS: Now that I have read what you posted, I'm not sure why you would want to delete Mary's files after you just copied them there from John's folder.

You're right . It should have been first remove then copy...
About chown dot behavior, I did not know that either. Probably would be better use
 /.???* so you don t not get the /..  expression.

---

