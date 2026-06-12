---
title: "Apache Server Help"
date: 2010-10-15
forum: General Help
---

### Post by abhjos on 2010-10-15
Hello,

I am using Ubuntu 10.10 and have install PHP and Apache on the machine. Server is working properly without any issues. When I create the foder in /var/www/ and put my project in new folder under /www folder I get the error message Page not found on server, I know that the page is there. How can I access the Project file from the folder in the browser.

Please help me with this.

Thank you,
AJ

---

### Post by abhjos on 2010-10-15
Help please.

---

### Post by crichard on 2010-10-15
Could you please tell us, What are the error messages are you getting? What it shows when you try to access [http://localhost](http://localhost)

---

### Post by abhjos on 2010-10-15
I am getting error as page not found on the server when I try to open [http://localhost/WebProject/Project/Index.html](http://localhost/WebProject/Project/Index.html)

---

### Post by crichard on 2010-10-15
> **abhjos said:**
> I am getting error as page not found on the server when I try to open [http://localhost/WebProject/Project/Index.html](http://localhost/WebProject/Project/Index.html)

I asked you what it shows when you access this [http://localhost](http://localhost)

It helps me to figure out whether apache is working or not.. That's why I asked you..  I recommend you to keep your files in a local folder like public_html because in /var/www every time it asks root access.

---

### Post by abhjos on 2010-10-15
When I type [http://localhost](http://localhost) I get "It's Works" page. I am sure Apache is working just fine.
please guide me properly as where shall I keep my project files and how can I access the project from browser.

---

### Post by crichard on 2010-10-15
Ok, that means your apache is running... That's fine.. Try this [tutorial]("http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/") & contact me, if you've any problems..

---

### Post by btindie on 2010-10-15
Please post the output of
```
sudo tail -f  /var/log/apache2/error.log
```
assuming that's where you've got apache to log errors to.
 
Also, have you set the directory/file permissions so apache can read the files?

---

### Post by abhjos on 2010-10-15
I have checked the tutorial and have installed using the same steps. My concern is I need to user Folders in /var/www/ where I can keep different projects and access them accordingly in Browser, also I am the root user for the machine so I have complete access to all the folders and files.

---

### Post by abhjos on 2010-10-15
Help please.

---

### Post by perspectoff on 2010-10-15
Firewalls? Port forwarding? Virtual server configs?

Setting up an Apache server is not necessarily plug and play.

RTFM.

---

### Post by crichard on 2010-10-15
Then, it relates to permission issues. Grant that folder to access by all, 

```
sudo chmod 777 (folder name with proper location)
```

For example, If a folder named website1 stored inside public_html which is located at  /home/user/public_html/

Then, the the command would be

```
sudo chmod 777 ~/public_html/website1
```

The above command will make that folder  read, write and execute by everyone.

---

### Post by Roasted on 2010-10-15
Not sure what your goal is with Apache, but I can at least tell you what I did if it makes things easier. By default /var/www doesn't allow a typical user (aka, you) to have read/write permissions unless you change them accordingly. I didn't like that idea, and decided to create sub folders within /var/www. I have several folders, so let's throw a few out there:

Ghost
Mist
Skynet
Area51

This is nice because when I need to link somebody to something on my machine, I just do [http://externalIP/skynet](http://externalIP/skynet), or whatever the folder is. All of these folders my user has RWX (7) rights to. That way I leave the permissions of /var/www alone, but within /var/www I have for example, /var/www/skynet, and skynet being MY folder (and not root) I can access just fine.

---

### Post by perspectoff on 2010-10-15
I don't like to give 777 (read/write/execute to everyone) permissions to anything on a server.

Most things can stay as root. However, I have found that some of my server packages have to have their folders allow read/write/execute permission for the www-data user (or group) in addition to root.

 sudo chown -R root:www-data /var/www

for example (although I am usually more precise in which folders I allow to have www-data ownership).

---

### Post by perspectoff on 2010-10-15
> **Roasted said:**
> Not sure what your goal is with Apache, but I can at least tell you what I did if it makes things easier. By default /var/www doesn't allow a typical user (aka, you) to have read/write permissions unless you change them accordingly. I didn't like that idea, and decided to create sub folders within /var/www. I have several folders, so let's throw a few out there:

Ghost
Mist
Skynet
Area51

This is nice because when I need to link somebody to something on my machine, I just do [http://externalIP/skynet](http://externalIP/skynet), or whatever the folder is. All of these folders my user has RWX (7) rights to. That way I leave the permissions of /var/www alone, but within /var/www I have for example, /var/www/skynet, and skynet being MY folder (and not root) I can access just fine.

Kind of like an easy WebDAV, huh? Elegant, simple, quick -- heck I'm going to try that with a glass of Chianti!

---

### Post by crichard on 2010-10-15
> **perspectoff said:**
> I don't like to give 777 (read/write/execute to everyone) permissions to anything on a server.

Most things can stay as root. However, I have found that some of my server packages have to have their folders allow read/write/execute permission for the www-data user (or group) in addition to root.

 sudo chown -R root:www-data /var/www

for example.

Exactly, even I don't like to give Full permissions to the folder which is inside  File System. That's why I asked the thread starter to keep the files inside ~/public_html folder, but he tends to keep it inside /var/www. Let's see if it works for him. Otherwise we'll assist him to run his local server properly.

---

### Post by abhjos on 2010-10-15
This is my personal computer which I have. I am a developer and working on several projects and want to keep everything in proper order so want to keep all in /var/www/ and would create several folders as I need so I can access them over browser. Please help me with this. I hope I am clear with my question

---

### Post by abhjos on 2010-10-15
Any Help please.

---

### Post by crichard on 2010-10-15
What's the output of the below command?

```
ls -l /var/www
```

---

