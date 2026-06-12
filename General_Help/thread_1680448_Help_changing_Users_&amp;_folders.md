---
title: "Help changing Users &amp; folders"
date: 2011-02-02
forum: General Help
---

### Post by Cpierce on 2011-02-02
I love Ubuntu, and have converted a ton people over to the Linux side. I have some hard drive images saved where I am the sudo user. I would like to be able to use this image so I don't have to go thru the entire installation each time. 

However, I would like to be able to change the user and home folder to the new person's name. I believe I can go to "Users & Groups" and simply change the user name and password. But the home folder has me stumped. I have browsers to save in /home/chuck/downloads, music goes to /home/chuck/music and so on. If I just rename "chuck" to "linda", I believe this would cause all kinds of problems. 

How would I change the home folder to a different name and all the programs paths still work ? Is this possible ?

---

### Post by tredegar on 2011-02-02
> How would I change the home folder to a different name and all the programs paths still work ? Is this possible ?
It's not the _name_ that matters so much as the _permissions_ associated with the UID *number* (mapped to a username, via **/etc/passwd**) and GID *number* (mapped to a group name via **/etc/group**)

To understand how this all works together please take a look at the **/etc/passwd** and **/etc/group** files, and the following commands:

[B]groups 
chown[/B]

Linux is awesome, and surprisingly logical. Once you get your head around it you think "Well *of course* that's the way to do it. Obvious really". But it takes a little homework.

I am sure you will receive further advice from the users of this forum, but this might be a start.

Good luck.

---

### Post by Cpierce on 2011-02-02
Tredegar
Thank you for the info, it is over my head, but I do love to learn about linux. From what you said, it is possible. 

Now I just need to figure out how to do it.

---

### Post by Cpierce on 2011-02-13
anyone know how to do this step-by-step ?

---

### Post by cjhabs on 2011-02-13
check out the "usermod" command.
Changing uid and gid manually can cause various problems, usermod takes care of all the underlying problems.

---

### Post by HiImTye on 2011-02-14
move the files to the owner's folder with:
```
sudo mv -R /path/to/folder /home/username/
```then take ownership of them with:
```
sudo chown -R username /home/username/
```or if you like where they are just take ownership with
```
 sudo chown -R /path/to/folder
```

---

### Post by Philio on 2011-02-14
Programs probably don't care where your user folder is, if you just want to change the username do this:

```
sudo mv /home/olduser /home/newuser
```

```
sudo usermod -l newuser -d /home/newuser olduser
```

This way you'll have the same user account (uid + gid) but just rename the home directory and change the user name.

---

### Post by Cpierce on 2011-02-14
Thanks to all of you. This is great info, and I sure appreciate it.

---

