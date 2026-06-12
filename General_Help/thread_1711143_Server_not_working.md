---
title: "Server not working?"
date: 2011-03-20
forum: General Help
---

### Post by ReInspired on 2011-03-20
Hey guys, I am really new to ubuntu, so I am sorry if my terminology is not correct.

Anyway, I am using the server in ubuntu for my test server for my site, instead of having to use Xamp on windows.

So I had my website in var/www which was working just fine.

But then I needed to share the www folder so that I could put files onto it from my windows 7 machine.

So I had some trouble but I finally got it to share properly so that I could read and write files to the folder.  

But now I can access my server. I get this error when I type int he IP 
> **Forbidden**

 You don't have permission to access /index.html on this server.
  Apache/2.2.16 (Ubuntu) Server at jordan-desktop.local Port 80

Can Anyone help me?  I am running ubuntu 10.10, and I used this guide to setup the www folder share.   [http://ubuntuforums.org/showthread.php?t=290653](http://ubuntuforums.org/showthread.php?t=290653)

---

### Post by jerenept on 2011-03-20
Please explain exactly what you did to "share" the /var/www folder with Windows.
I think it may be the key to your problem.

You may want to try using FTP rather than SMB/Windows sharing.

---

### Post by ReInspired on 2011-03-20
I did exactly what it said to do here, [http://ubuntuforums.org/showpost.php?p=1699849&postcount=2](http://ubuntuforums.org/showpost.php?p=1699849&postcount=2)

---

### Post by Script Warlock on 2011-03-20
you might try the permission with chmod 644

---

### Post by ReInspired on 2011-03-20
> **Script Warlock said:**
> you might try the permission with chmod 644
no, that didnt work, still got the same error, and i couldnt write to the folder from the network

---

### Post by jerenept on 2011-03-20
found something...

try running ```
sudo chmod a+rx /var/www
```

The problem can sometimes happen if Apache is not permitted to Read/Write the files in /var/www, that should fix it.

---

### Post by ReInspired on 2011-03-20
> **jerenept said:**
> found something...

try running ```
sudo chmod a+rx /var/www
```The problem can sometimes happen if Apache is not permitted to Read/Write the files in /var/www, that should fix it.


Alright, I tried that, it didnt work either, Its got to be something with the permissions, because it was working fine before that

---

### Post by ReInspired on 2011-03-21
Anyone?

---

### Post by ReInspired on 2011-03-21
anyone know what to do? sorry i am very new to ubuntu

---

### Post by vivek.pandey on 2011-03-21
check out this link
[http://ubuntuforums.org/showthread.php?t=1700049](http://ubuntuforums.org/showthread.php?t=1700049)

---

### Post by ReInspired on 2011-03-21
> **vivek.pandey said:**
> check out this link
[http://ubuntuforums.org/showthread.php?t=1700049](http://ubuntuforums.org/showthread.php?t=1700049)


hey thanks, I got it working, but now I have a different problem.

I have a website under my www folder so it looks like this var/www/website

now when When I edit the files in the website on my windows machine and save them to my ubuntu machine through networking, i cant access var/www/website anymore, untill I go into the foler permissions and change them to read and write.  Which makes it work again, atleast untill I save a file, then I have to do it all over.

Any ideas why? hope that made sense

---

