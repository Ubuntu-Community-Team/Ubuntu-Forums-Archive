---
title: "need help with apache/user..."
date: 2009-12-02
forum: General Help
---

### Post by KennyJ on 2009-12-02
I installed ubuntu 9.10 yesterday and apache 2 this morning..

This is my first time to have a non-windows OS and so far I love it...

I can view the index.html page in the browser but it won't let me edit the html file and save it.  I get an access denied.  I created a new user with the path of /var/www but it wouldn't save as that, it changed it to /home/www

This is probably a very easy thing to do, I'm just new to the server side.  I've been designing sites for about 5 years now and want to move to the server side of things.

Any help would be greatly appreciated.

Thanks

---

### Post by endBc on 2009-12-02
/var/www is not owned by you so obviously you've no rights to write to it.

```
sudo <command>
```

---

### Post by KennyJ on 2009-12-02
What command would I use?  I want to open the file in a text editor and be able to save.  I also want to save images to that folder (I can find the command to move a folder) But I don't know how to open in text editor and save.

Or do I need to just create the site in /home/www then move the folder?

I just thought it would be easy as in update the file and save then see immediate update.

---

### Post by endBc on 2009-12-02
```
gksudo gedit /var/www/index.html

```If the application you are going to launch doesn't have a GUI, use sudo ( previous post ).
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) should give you the basic idea of what sudo is and why you need it.

---

### Post by KennyJ on 2009-12-02
Thanks!  that worked.

Is it possible to create an alias folder? /home/user/www that goes to /var/www/ ?

---

### Post by endBc on 2009-12-02
A link ?

```
ln -s /var/www ~/www

```

---

### Post by KennyJ on 2009-12-02
will I need to do anything permission wise?

---

### Post by endBc on 2009-12-02
You'll still need to use sudo as the privileges doesn't change when you create a symbolic link.
Actually, have you tried to enable Apache module called userdir ? In that way you could have a public folder in your home directory which could be accessible from [http://localhost/~user]("http://localhost/%7Euser").

---

### Post by KennyJ on 2009-12-02
no I have not.  Do I need to install that module?  Or is it included?

---

### Post by endBc on 2009-12-02
Enable:
```
sudo a2enmod userdir

```

Open /etc/apache2/httpd.conf and append with the following:
```
<IfModule mod_userdir.c>
    UserDir Public
</IfModule>
```

Create the folder and restart Apache:
```
mkdir ~/Public && sudo /etc/init.d/apache2 restart
```

---

### Post by Jive Turkey on 2009-12-02
You can take ownersip of /var/www with the chown command, ie:
```
sudo chown -R username:username /var/www
```
the -R makes it recurse to the subfolders and you must replace "username" with the user you are giving ownership to.

---

### Post by KennyJ on 2009-12-02
> **Jive Turkey said:**
> You can take ownersip of /var/www with the chown command, ie:
```
sudo chown -R username:username /var/www
```the -R makes it recurse to the subfolders and you must replace "username" with the user you are giving ownership to.

Thanks alot!  It worked!  Much easier

---

### Post by KennyJ on 2009-12-02
> **endBc said:**
> Enable:
```
sudo a2enmod userdir

```Open /etc/apache2/httpd.conf and append with the following:
```
<IfModule mod_userdir.c>
    UserDir Public
</IfModule>
```Create the folder and restart Apache:
```
mkdir ~/Public && sudo /etc/init.d/apache2 restart
```

After all of that it said user not found when I went to ~kenny

But another method worked.  thanks for your help.  your other steps worked and now I know a few more commands.

---

