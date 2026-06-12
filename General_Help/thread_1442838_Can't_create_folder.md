---
title: "Can't create folder"
date: 2010-03-30
forum: General Help
---

### Post by Datamac on 2010-03-30
I can't create a folder in the home directory.  It seems I don't have the permissions to create a folder in my home directory.  This is a new installation.  I want to be able to create subfolders in my home folder.  Also, I want to be able to modify configuration files in the etc folder.  Can anyone help me with this problem?

---

### Post by coolcaseley67 on 2010-03-30
hi 
 
could you clear up ??
 
- do you mean as the home folder which has in it the your doc eg ??
 
thanks

---

### Post by Datamac on 2010-03-30
Yes, I think this is where I want to create my sub folders.  I want to be able to create the sub folders "home/www".

---

### Post by ravikalsi27 on 2010-03-30
just use nautias scrpits........to get privileges............
or use command from root:

"chmod 770 /home/username"

---

### Post by Datamac on 2010-03-30
I am still not sure I understand what you mean?  I do understand how to use command line commands for other O/S's and therefore may need to get a list of commands that apply to this O/S.  But somehow with this basic understanding of mine I am not confident that I will be able to retain the permission level needed to accomplish my task.

---

### Post by Datamac on 2010-03-30
Okay,  I tried "chmod 770 /home/username" and got nothing.  I am not familiar with nautias scrpit

---

### Post by 98cwitr on 2010-03-30
^^^need the sudo command there bud.

sudo chmod a+x /home/*

---

### Post by oldos2er on 2010-03-30
Instead of /home/www, which implies a user named www, create /home/user/www, where "user" is your user name. You have full write privileges in /home/user.

To edit files in /etc, you need admin privileges, so use ```
gksu gedit /etc/somefile
```

---

### Post by Datamac on 2010-03-30
Now, thanks to YOU bud!   You got my brain a thinking!  I got the directories created by using sudo mkdir.  

Would you know anything about setting up a webserver?

---

### Post by coolcaseley67 on 2010-03-30
hi
 
"Would you know anything about setting up a webserver" .
 
no not an idea , sorry .
 
ps mark this post as soved in thead tools .

---

### Post by 98cwitr on 2010-03-30
> **Datamac said:**
> Now, thanks to YOU bud!   You got my brain a thinking!  I got the directories created by using sudo mkdir.  

Would you know anything about setting up a webserver?

google LAMP server...easy tutorials

---

### Post by akakingess on 2010-03-30
Plus, doesn't the WWW folder usually go under var within the filesystem, or is that just the default or the way that I did it? Either way you do need to change the permissions and possibly use the -R argument for recursive, which should change the subdirectories as well.

---

