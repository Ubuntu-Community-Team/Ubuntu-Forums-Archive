---
title: "adding a directory for new users"
date: 2011-04-17
forum: General Help
---

### Post by seventwenty on 2011-04-17
Hi, 

When i create a new user i want this user to have a public_html directory created in their home.
Any help would be grateful, thanks.

---

### Post by coffee412 on 2011-04-17
In your directory /etc/skel you can create files or directories and it will put it in the new users home directory when you create an account. I have not had to do this yet but according to documentation that is what the directory is for. skel is short for skeleton directory. Here is a link to explaining it:

[http://ezinearticles.com/?Linux-System-Administration-Training---User-Setup-in-Etc-Skel-Directory---Linux-Commands-Training&id=1788295](http://ezinearticles.com/?Linux-System-Administration-Training---User-Setup-in-Etc-Skel-Directory---Linux-Commands-Training&id=1788295)

Hope that helps.

coffee

---

### Post by kiyop on 2011-04-17
[coffee412's #2]("http://ubuntuforums.org/member.php?u=1060897") is better.

```
man adduser.conf
```
Below is my old post.

[COLOR=gray]If you want to make directory manually, log in with the newly created account and type in terminal
```
mkdir public_html
```Do you want to configure so that public_html directory is automatically created under /home/(user name)  and it is broadcasted on internet when a new user is generated?[/COLOR]

---

### Post by Spyderkid on 2011-04-17
> **kiyop said:**
> [coffee412's #2]("http://ubuntuforums.org/member.php?u=1060897") is better.

```
man adduser.conf
```
Below is my old post.

[COLOR=gray]If you want to make directory manually, log in with the newly created account and type in terminal
```
mkdir public_html
```Do you want to configure so that public_html directory is automatically created under /home/(user name)  and it is broadcasted on internet when a new user is generated?[/COLOR]

You'll need to use Sudo if your making it in the /home folder

---

### Post by yetiman64 on 2011-04-17
> **Spyderkid said:**
> You'll need to use Sudo if your making it in the /home folder

Sorry Spyderkid, but a definite NO to what you just said. /home/<user>/ is owned by its user, not root, hence sudo is **not needed** with that command. Using sudo will give ownership of public_html to root and not the user.

Note, the terminal defaults to the folder /home/<user>/. And issuing the command will therefore put the public_html folder there and not in /home (which is owned by root).

---

### Post by seventwenty on 2011-05-05
> **coffee412 said:**
> In your directory /etc/skel you can create files or directories and it will put it in the new users home directory when you create an account. I have not had to do this yet but according to documentation that is what the directory is for. skel is short for skeleton directory. Here is a link to explaining it:

[http://ezinearticles.com/?Linux-System-Administration-Training---User-Setup-in-Etc-Skel-Directory---Linux-Commands-Training&id=1788295](http://ezinearticles.com/?Linux-System-Administration-Training---User-Setup-in-Etc-Skel-Directory---Linux-Commands-Training&id=1788295)

Hope that helps.

coffee

Thanks, that's what i was looking for. I new there was a directory for doing this but couldn't remembre the name of it.

---

