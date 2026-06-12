---
title: "need help with file transfer"
date: 2006-04-25
forum: General Help
---

### Post by TreetopClimber on 2006-04-25
my problem is on how to copy my files to the proper folder for use on my site, with windows it was easy just put them on a disk and copy them over to the server via the cdrom, I have tried that with this and it tells me I dont have permission to write in these folders (I dont own them) bull, I do I just dont know how to fix this. Another thing is my ubuntu pc and my windows pc are on the same IP so I dont believe I can ftp them to my server shell... or can I? Or how do I fix this ownership issue? Or how do I set the correct permissions for /var/www which is the localhost so I can copy my files from disk to it? Please if anyone can help. Thanks in advance, TT

---

### Post by orev on 2006-04-26
Not exaclty sure what the question is, but....

You are trying to upload new .html, .php, image, or other files to a web server, right?  Normally, as you mentioned, ftp would be the method.

I guess I don't understand how both computers have the same IP if one is a web server, and has DNS pointing to it, and the other is a production machine.  If you have a static IP through your ISP in order to serve pages from the one box your other computer should have another IP...

I don't think I'm understanding...

---

### Post by Bradley17 on 2006-04-26
Im not sure either what you mean but to change ownership of files in ubuntu 

sudo chown system_username / file_location

To change file permissions 

sudo chmod 777 (or the permissions you want) / file_location

---

### Post by TreetopClimber on 2006-04-26
[QUOTE=Bradley17]Im not sure either what you mean but to change ownership of files in ubuntu 

sudo chown system_username / file_location

To change file permissions 

sudo chmod 777 (or the permissions you want) / file_location[/QUOTE]

To answer both your questions first, I have my setup through a cable router .. now when I had them enter the mac addresses for the network they werent sure on how to set it up with multipal addresses so I have 4 pc's on 1 IP since they were incompotent. That will be fixed after I move, which will be in a month so until then I will have them still all on the same IP, which stinks cuz it kills my bandwidth but my site is still in the new born stages... lol. Anyways (Bradley17) you answered my question on file changes and I thank you, this is all very new to me. I appreciate both your reply's, TT

---

### Post by Bradley17 on 2006-04-28
[QUOTE=TreetopClimber]To answer both your questions first, I have my setup through a cable router .. now when I had them enter the mac addresses for the network they werent sure on how to set it up with multipal addresses so I have 4 pc's on 1 IP since they were incompotent. That will be fixed after I move, which will be in a month so until then I will have them still all on the same IP, which stinks cuz it kills my bandwidth but my site is still in the new born stages... lol. Anyways (Bradley17) you answered my question on file changes and I thank you, this is all very new to me. I appreciate both your reply's, TT[/QUOTE]


happy 2 help mate

---

### Post by TreetopClimber on 2006-04-28
> but to change ownership of files in ubuntu

sudo chown system_username / file_location

To change file permissions

sudo chmod 777 (or the permissions you want) / file_location

I tried this in several different combinations with no luck. Could you be more specific in this discription? I am also having a problem with the sound card not being reconized by ubuntu, it worked fine under windows OS so there must be some conflict some where that I dont know how to fix. I have read several of the how to forums, similar to this problem but again none have helped. But the files are more important to me at this point... cant run a site if ya cant load the info :(

---

### Post by Bradley17 on 2006-04-28
[QUOTE=TreetopClimber]I tried this in several different combinations with no luck. Could you be more specific in this discription? I am also having a problem with the sound card not being reconized by ubuntu, it worked fine under windows OS so there must be some conflict some where that I dont know how to fix. I have read several of the how to forums, similar to this problem but again none have helped. But the files are more important to me at this point... cant run a site if ya cant load the info :([/QUOTE]


Rite, hmm yea my box is running apache2, and i know that you need decent permissions to execute stuf. so heres an example of a file on desktop

ownership .for example i have a user called "me" and i had a file like below. 

sudo chown me /home/me/me.tar.gz

and for permissions

sudo chmod 777 /home/me/me.tar.gz

---

### Post by fotter on 2006-04-28
Hi, I take it that the Ubuntu machine you're using is serving the pages?

If they're in /var/www/ then you won't be able to write to this folder without either being root or changing the permissions. If you're the only person who wants/needs to be able to write to that folder, then simply type the following in a teminal window:

sudo chown <your-username> /var/www/

Now you should have the permissions needed to copy the files across using Nautilus (the gnome browser) or a terminal window (e.g. 'cp yourfile.html /var/www/') as you please.

---

### Post by TreetopClimber on 2006-04-29
"fotter" I tried this exactly like you posted using terminal.
myusername@myserver:~$ sudo chown username/var/www/
password: (I type that in)
and this is what happens
chown: too few arguments
try `chown --help' for more information
so in the next line I type (chown --help') and then get this
> 
dont know what that is or what should be written?
I have also tried it like this
myusername@myserver:~$ sudo chown username /var/www/ 
and get the same result as the first. So I dont know whats up.
I have installed 
apache2
php4
mysql-server
libapache2-mod-auth-mysql
php4-mysql
phpmyadmin
all the basics for my server. I have no problems uploading my sql files from disk to the database. And I know how to set permissions there. Just the files for my site need to be put in the localhost for use, which are on disk, since I cant use ftp. Like I stated before I had no problems doing it this way with windows, so there should be a simple way of doing it here with ubuntu. Just need the right combo of comands I suppose.

---

### Post by TreetopClimber on 2006-05-06
Ok to answer my own question!! Since I have figured it out, its not sudo chmod 777 /var/ its sudo chmod 0777 /var/ or any other file and also you dont need to chown anything.

---

### Post by jtibau on 2006-05-14
I think it would've been better to do:
```

sudo chmod 0777 /var/www

```
The reason being that you now have given your whole /var folder 777 permision. I'm gonna guess you don't know what this exactly means, so I'll explain. Now anyone gaining access to your machine can do anything to your /var folder. Even erase it entirely.
For more info you might want to read the man page for chmod:
```

man chmod

```
Man pages are a bit complicated to read at first, but it is very handy to get used to them. They hold in-depth knoledge of howto use each command you might need in your system.
I don't quite remember the exact sintax (of chmod) but instead of giving all permisions to everyone, you could've given all permissions to you and only you. :)

---

