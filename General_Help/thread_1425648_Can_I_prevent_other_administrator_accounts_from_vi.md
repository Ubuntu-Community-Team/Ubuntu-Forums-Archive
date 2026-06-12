---
title: "Can I prevent other administrator accounts from viewing my files?(permissions)"
date: 2010-03-09
forum: General Help
---

### Post by mahela007 on 2010-03-09
I just noticed that even if I remove read and write permission for my files, another user can access those files if they use 'sudo'. Am I doing something wrong? 
The ls -l for the folder containing my file (let's call is myfile') looks like this.
"```
-rw-------  1 username groupname   43 2010-03-09 20:23 myfile
```"

I logged into another account I have made for myself (which had admin privileges) and then did 
```
sudo nano /username/home/myfile
```
and ... the file was opened and I was able to read it. So what's the point of having user permissions if someone can bypass them by using sudo?

---

### Post by kanikilu on 2010-03-09
That's just how it works - and not just on Ubuntu/Linux...every OS I use (Windows, OS X and Ubuntu) all have various forms of "administrators" who have complete control over the system and files.

You're supposed to only give admin/root/sudo to users you trust with the system completely. For everyone else, put them in restricted user groups and they will not be able to read a file like in your example.

---

### Post by Topsiho on 2010-03-09
If you don't want another user to be able to read and/or write your files, why do you give him/her administrator privileges?

Like: I lock my house, but please, here are the keys, to someone who passes by.

Topsiho :)

---

### Post by sinchan_ on 2010-03-09
Yesterday I was installing ubuntu server 9.10 and setup ofered me to encrypt my user files, saying that only my user was able to access, and the folder is unmounted after log off

hope this helps

regards

---

### Post by falconindy on 2010-03-09
Solution: Treat sudo with respect and approach with the trepidation it warrants.

Your post reflects an attitude all too commonly found in Ubuntu users, given that the root account is not accessible by default. Overusage of sudo becomes the norm.

---

### Post by undecim on 2010-03-09
An administrator is someone who is given complete control over your system. If you files are on a hard drive attached to a computer, any admin can view them.

To protect your files you have to encrypt your home directory, but even then your files can still be viewed by other admins if you are logged on.

The only way to keep other admins from viewing your files is to not give administrative privileges to other user.

---

### Post by sebastianabate on 2010-03-09
> **Topsiho said:**
> If you don't want another user to be able to read and/or write your files, why do you give him/her administrator privileges?

Like: I lock my house, but please, here are the keys, to someone who passes by.

Topsiho :)

Actualy there are situations where you need to give someone access to certain parts of your house, but not to all (like a gardner, or a pool boy, who must access your property's periphery, but not to the house)

The same apply to your PC, you may need to give to a user permission to install software, or start and stop services, but you dont want to give to him/her full control access. In Windows you can achive this denying specific permissions (you can actualy deny an administrator user the "take ounership" right, and prevent him/her access files without your permission). I dont know a way to do this on *nix.

---

### Post by cjhabs on 2010-03-09
> **sebastianabate said:**
> Actualy there are situations where you need to give someone access to certain parts of your house, but not to all (like a gardner, or a pool boy, who must access your property's periphery, but not to the house)

The same apply to your PC, you may need to give to a user permission to install software, or start and stop services, but you dont want to give to him/her full control access. In Windows you can achive this denying specific permissions (you can actualy deny an administrator user the "take ounership" right, and prevent him/her access files without your permission). I dont know a way to do this on *nix.

You can edit the /etc/sudoers file and control which commands individual users can perform using sudo.
Please be careful doing this!

---

### Post by mahela007 on 2010-03-09
I'm not giving my permissions to another user. I just have two accounts for myself and just out of curiosity, I wanted to check if another account would be able to access files with insufficient permissions by using sudo. Turns out it can. 
Personally, I believe this is the wrong approach. I believe that admins shouldn't be able to access or modify the files of another user without permission. (but that creates a problem of editing system files belonging to root doesn't it? ).
Anyway, how do you encrypt your home folder? Is it possible to do this after installation ?

---

### Post by Roasted on 2010-03-09
> **mahela007 said:**
> I just noticed that even if I remove read and write permission for my files, another user can access those files if they use 'sudo'. Am I doing something wrong? 
The ls -l for the folder containing my file (let's call is myfile') looks like this.
"```
-rw-------  1 username groupname   43 2010-03-09 20:23 myfile
```"

I logged into another account I have made for myself (which had admin privileges) and then did 
```
sudo nano /username/home/myfile
```
and ... the file was opened and I was able to read it. So what's the point of having user permissions if someone can bypass them by using sudo?

If you don't want a user to access your files, why do they have the root password?

---

### Post by mahela007 on 2010-03-09
As I said, both accounts on the PC are mine.. but I get your point. DO you know how to encrypt the home folder?

---

### Post by sebastianabate on 2010-03-09
> **cjhabs said:**
> You can edit the /etc/sudoers file and control which commands individual users can perform using sudo.
Please be careful doing this!

Yes, with sudo you can control which commands can be executed, but I dont think that you can control which directories or files can be accessed. And the ugo permissions don't prevent the access, becouse with root rights you can access any file, regardless of access restrictions.

---

### Post by rnerwein on 2010-03-09
hi
there are some unix/linux distros on the marked. i know bitbull for solaris ( and that's not cheep ! )
it's like a class B system ( google orange book ). there you can permissions down to single commands.
you can give any user - even root special permissions. but there you got secure adminstrators. not
only one person because the rights of them are splited too.
no fun to work on those systems ( i did it ).
ciao

oh yeah - it's a ticked to hell to get only a normal aplication to be able to run on those systems.

---

### Post by sebastianabate on 2010-03-09
> **mahela007 said:**
> As I said, both accounts on the PC are mine.. but I get your point. DO you know how to encrypt the home folder?


It's a PITA, but you can encrypt your home after the installation following this howto

[http://jacob.hoffman-andrews.com/README/index.php/2009/12/08/howto-encrypt-an-existing-home-directory-on-ubuntu-karmic-koala/](http://jacob.hoffman-andrews.com/README/index.php/2009/12/08/howto-encrypt-an-existing-home-directory-on-ubuntu-karmic-koala/)

I recomend you to try Truecrypt ([www.truecrypt.org](www.truecrypt.org)), with it, you can "Creates a virtual encrypted disk within a file and mounts it as a real disk", and anything you put on that virtual disk will be crypted on the fly.

---

