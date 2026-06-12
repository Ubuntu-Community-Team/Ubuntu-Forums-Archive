---
title: "How to creat new folders in filesystem?"
date: 2009-08-07
forum: General Help
---

### Post by masoud23 on 2009-08-07
hello

I want to be able to create new folders in filesystem. I want this to be permanently so i don't have to do it every time.

---

### Post by pastalavista on 2009-08-07
In terminal type```
sudo mkdir /foldername | sudo chown username /foldername
```

'foldername' to be changed to whatever you want to name it. 'username' is your logon name.

---

### Post by masoud23 on 2009-08-07
yes but how do i do it so i can do it directly in nautilus. i want to be able to open nautilus (filemaneger) and go to filesystem and create new folder directly without writing command in terminal every time.

---

### Post by pastalavista on 2009-08-07
You can run Nautilus as root (Alt-f2 -> gksu nautilus) and then you can right-click and create folders and edit permissions in the 'properties' dialog. You need have root permissions to create the folder, but after you've changed the owner to yourself (instead of root) you can then create and delete files inside it as a normal user. The '/' directory will always belong to root. Can't change that.

---

### Post by Cheesemill on 2009-08-07
Just right-click and select 'Create Folder'
 
 
By default you only have write access to your home folder, you only need to use a terminal command or 'gksudo nautilus' if you need to create a directory outside of your home folder, which you shouldn't have to do except in certain rare circumstances.
 
Where are you trying to create a folder and why?

---

### Post by fennec_fox on 2009-08-07
I've never really played around with it but, that ***might ***be something you can do by adding yourself to the sudoers file using the users and groups gui or  'sudo visudo' 

in system - admin - users and groups 
I believe you can give yourself root privileges and it writes the line into the sudoers file

Alternatively ***(I really don't recommend this) ***you can use  sudo visudo and add the line
username  ALL=(ALL) NOPASSWD: ALL
(replace username with your exact username)

I ***think*** that will work.

That said, ***I do not recommend the second way I mentioned or giving yourself root at all.* **
It makes it much easier to damage the system. What are you trying to do that you want to add folders to / ? There might be a better way

---

### Post by masoud23 on 2009-08-08
I am new to ubuntu 9.04, i run 7.10 before and there to run php files at (used Apache and Mysql) localhost i hade to place them at filesystem/var/www and I used to create new folders there to put my files in. Is there another way to do this?

---

### Post by nurvzy on 2009-08-08
A setup I like to use with Apache is to add a symbolic link in /var/www to a directory in my home directory.  

For example:
```

cd ~
mkdir Websites
cd /var/www
sudo ln -s /home/[login]/Websites Websites

```
(replace [login] with your actual user name)

Then you just add files in your /home/login/Websites directory normally and they'll appear when you navigate to [http://localhost/Websites](http://localhost/Websites) in your browser.

---

### Post by masoud23 on 2009-08-20
> **nurvzy said:**
> A setup I like to use with Apache is to add a symbolic link in /var/www to a directory in my home directory.  

For example:
```

cd ~
mkdir Websites
cd /var/www
sudo ln -s /home/[login]/Websites Websites

```
(replace [login] with your actual user name)

Then you just add files in your /home/login/Websites directory normally and they'll appear when you navigate to [http://localhost/Websites](http://localhost/Websites) in your browser.

It dosen work. I don't find a www map in ubuntu 9.04 so I change the command to: 
```

mkdir websites
cd /var/local
sudo ln -s /masoud/[my login]/websites test1.php

```
OBS: masoud = home. The test1.php file is there in websites but when i run: [http://localhost/masoud/websites/test1.php](http://localhost/masoud/websites/test1.php) i get: 
The requested URL /masoud/websites/test1.php was not found on this server.
Apache/2.2.11 (Ubuntu) Server at localhost Port 80

---

### Post by masoud23 on 2009-08-20
> **nurvzy said:**
> A setup I like to use with Apache is to add a symbolic link in /var/www to a directory in my home directory.  

For example:
```

cd ~
mkdir Websites
cd /var/www
sudo ln -s /home/[login]/Websites Websites

```
(replace [login] with your actual user name)

Then you just add files in your /home/login/Websites directory normally and they'll appear when you navigate to [http://localhost/Websites](http://localhost/Websites) in your browser.
sorry i found www map but it still don't work

---

