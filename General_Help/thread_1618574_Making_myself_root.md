---
title: "Making myself root?"
date: 2010-11-10
forum: General Help
---

### Post by Ntwiles on 2010-11-10
Hey guys. I'm developing a website locally so apache2 is installed under /etc/. Whenever I have to make changes to the config file inside there, I have to open up my terminal, type 'gksudo nautilus', and then navigate to that folder. I've tried making myself root by editing Users and Groups settings but I can't seem to give myself privileges to write to that folder. Is there a way to do this?

---

### Post by sisco311 on 2010-11-10
And what's your issue?

Learn how file permissions work, learn to use sudo or su, check out the official Ubuntu server guide...

---

### Post by Habitual on 2010-11-10
sudo gedit /path/to/file is an easy work-around.

Of course, you can substitute gedit for another editor.

Good luck.

Per the suggestion at [http://ubuntuforums.org/showpost.php?p=10100660&postcount=7](http://ubuntuforums.org/showpost.php?p=10100660&postcount=7)

gksudo should be used.
Thanks yetiman64

"Stability of the system is more important than convenience for the user" is the lesson I got from this thread.

---

### Post by Ntwiles on 2010-11-10
No issue, It's just an inconvenience. I know how both file permissions work and how to use sudo, thank you. There's no way to make myself root for good?

Yeah I've found lots of good work-arounds, I'd just like to find a way so that I don't have to go through all that if possible.

---

### Post by holiday on 2010-11-10
> **Ntwiles said:**
> No issue, It's just an inconvenience. I know how both file permissions work and how to use sudo, thank you. There's no way to make myself root for good?

Yeah I've found lots of good work-arounds, I'd just like to find a way so that I don't have to go through all that if possible.

$ sudo su
[sudo] password for <you>: ****
# 

You're in.

People are going to scream about how dangerous it is, but if you're setting up an Apache server, you probably know what you're doing.

---

### Post by lisati on 2010-11-10
The "root" account is disabled by default in Ubuntu. As others have pointed out, sudo/gksudo is the preferred way of temporarily elevating your user privileges.

Have a look here for more information: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by yetiman64 on 2010-11-10
> **Habitual said:**
> sudo gedit /path/to/file is an easy work-around.

Of course, you can substitute gedit for another editor.

Good luck.
**gksudo** is best to use with a graphical application such as gedit. With some graphical apps (particularly nautilus) using sudo can render the system unbootable due to unwanted changes to the  file ~/.ICEauthority. [--See here--]("http://www.psychocats.net/ubuntu/graphicalsudo") for more info. Or check "Graphical Sudo" section of link #4 in my sig.

> There's no way to make myself root for good?Posting instructions for root logins is a definite no-no here.

Check these links for why,

[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580) #12 Don't in particular

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

and

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by uRock on 2010-11-10
Ctrl+L will bring up the address bar in nautilus, if that helps you navigate after opening nautilus with the gksudo command.

If you are having to use gksudo nautilus a lot, then maybe creating a launcher for it will be helpful. That is what I did.

---

### Post by sisco311 on 2010-11-10
> **Ntwiles said:**
> No issue, It's just an inconvenience. I know how both file permissions work and how to use sudo, thank you. There's no way to make myself root for good?


If you don't know how to use your OS, in a secure way, without being prompted for a password too often, then learn how file permissions work and how to use sudo and/or su. 

Sorry for repeating myself.

> **Ntwiles said:**
> 
Yeah I've found lots of good work-arounds, I'd just like to find a way so that I don't have to go through all that if possible.

Learn.

---

### Post by Ntwiles on 2010-11-10
I can understand for sure that you guys don't want people screwing up their computers, but I know what I'm doing. Or better yet, I know enough to know when I don't know what I'm doing. 

But it looks like the mentality is "if you don't know how, you're not supposed to know how". So I'll take that as a challenge (:

---

### Post by sisco311 on 2010-11-10
> **Ntwiles said:**
> I can understand for sure that you guys don't want people screwing up their computers, but I know what I'm doing. Or better yet, I know enough to know when I don't know what I'm doing. 

But it looks like the mentality is "if you don't know how, you're not supposed to know how". So I'll take that as a challenge (:

I guess, we have a vague answer for any vague question.

We are here to help. If you have any concrete questions, please feel free to ask.

---

### Post by lisati on 2010-11-10
One of the rules of this forum is that we don't provide "log in as root" information, which, of course, would help you avoid using sudo and the seemingly constant prompt for your password.

Please go back and read the link I posted earlier: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by holiday on 2010-11-11
> **Ntwiles said:**
> I can understand for sure that you guys don't want people screwing up their computers, but I know what I'm doing. Or better yet, I know enough to know when I don't know what I'm doing. 

But it looks like the mentality is "if you don't know how, you're not supposed to know how". So I'll take that as a challenge (:

It's your computer. You go against the community's recommendations then you have to take full responsibility. That is motivation to learn. It's easy to take a backup.

I understand that some here think me wrong to tell you how to become root. Most people would never ask. 

But you asked. I told you the answer. My choice is to either tell the truth or to keep the secret.

This is an open community. There must be no secrets.

---

### Post by dcstar on 2010-11-11
> **Ntwiles said:**
> Hey guys. I'm developing a website locally so apache2 is installed under /etc/. Whenever I have to make changes to the config file inside there, I have to open up my terminal, type 'gksudo nautilus', and then navigate to that folder. I've tried making myself root by editing Users and Groups settings but I can't seem to give myself privileges to write to that folder. Is there a way to do this?

Ubuntu is built around a particular security model that does not allow root login/access by default.

Simply install the **nautilus-gksu** package and you will never have to use a shell for this again.

---

### Post by aysiu on 2010-11-11
Create a keyboard shortcut for ```
gksudo nautilus
``` and there's your convenience.

---

### Post by oldos2er on 2010-11-11
> **holiday said:**
> There must be no secrets.

There are no secrets. A simple google search will yield the info the OP is seeking; it's not promoted here on the forums because it subverts Ubuntu's security model.

"sudo su" or "sudo -i" should be sufficient; if they're not, maybe the OP could explain why.

---

### Post by uRock on 2010-11-11
That is why we post the RootSudo link in threads like this. It explains the ins and outs of root and sudo, to include how to use them to get things done.

---

### Post by Verbeck on 2010-11-11
why don't you change the document root & directory to some place in your home folder?

```
sudo gedit /etc/apache2/sites-available/default
```change *DocumentRoot /var/www* to DocumentRoot */home/username/Public* and
<Directory* /var/www/*> to <Directory */home/username/Public/*>

---

### Post by CharlesA on 2010-11-11
> **Verbeck said:**
> why dont you change the document root to something in your home folder?

sudo gedit /etc/apache2/sites-available/default

Wouldn't that screw with the permissions even more, since www-root needs to be able to access the files there?

Also it's gksu for graphical apps. :P

@OP: On my web server I changed the owner of the document root inside /var/www/ to my user and gave it 775 permissions.

```
sudo chown user:user /var/www/somefolder
sudo chmod 775 /var/www/somefolder
```

---

### Post by Verbeck on 2010-11-11
> **CharlesA said:**
> Wouldn't that screw with the permissions even more, since www-root needs to be able to access the files there?


i've changed it to /home/www and am not having any problems.maybe its something else i did... :confused:

---

### Post by CharlesA on 2010-11-11
> **Verbeck said:**
> i've changed it to /home/www and am not having any problems.maybe its something else i did :confused:

Well, yer home directory is 775 IIRC, so it could be read by all, but if it's encrypted, that's a whole other bag of rocks. :P

---

### Post by Verbeck on 2010-11-11
> **CharlesA said:**
> Well, yer home directory is 775 IIRC, so it could be read by all, but if it's encrypted, that's a whole other bag of rocks. :P

aah.. i keep it outside my home folder with 775 :D

---

### Post by CharlesA on 2010-11-11
> **Verbeck said:**
> aah.. i keep it outside my home folder with 775 :D

Ah. Gotcha. :)

---

### Post by Ntwiles on 2010-11-11
> **CharlesA said:**
> Wouldn't that screw with the permissions even more, since www-root needs to be able to access the files there?

Also it's gksu for graphical apps. :P

@OP: On my web server I changed the owner of the document root inside /var/www/ to my user and gave it 775 permissions.

```
sudo chown user:user /var/www/somefolder
sudo chmod 775 /var/www/somefolder
```

Thanks for the information. I manage to change the permissions manually through graphical interface. Where I get trouble is when I have to edit httpd.conf, or modify the apache2 modules installed/enabled, which are all over the place. 

I'm just curious, I keep hearing about 'subverting Ubuntu's security model'. Who's security are we talking about? Mine or Ubuntu's? I'm not trying to do anything illegal, I'm just trying to make using Ubuntu more convenient. If there's a reason Ubuntu developers don't want us logging in as root for any reason, I'm sure they know what they're doing. Otherwise, I'd like to do it. Thanks for the information guys.

---

### Post by CharlesA on 2010-11-11
I've always done virtualhosts in httpd.conf.

Ubuntu uses sudo instead of enabling the root account, and that's the prefered method of doing stuff with root privlages.

If you decide to enable the root account and use it all the time, do so out yer own risk.

---

### Post by Habitual on 2010-11-11
> **yetiman64 said:**
> **gksudo** is best to use with a graphical application such as gedit. With some graphical apps (particularly nautilus) using sudo can render the system unbootable due to unwanted changes to the  file ~/.ICEauthority. [--See here--]("http://www.psychocats.net/ubuntu/graphicalsudo") for more info. Or check "Graphical Sudo" section of link #4 in my sig.

noted, quoted, and corrected. Thank you.

---

