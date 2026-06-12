---
title: "mounting to a windows share"
date: 2006-04-24
forum: General Help
---

### Post by jazee on 2006-04-24
How do you  mount to a windows share from ubuntu. I have tried: 
sudo mount -t smbfs //192.168.1.15/music /mnt/music
smbmount //guardian/music /mnt/music
smbmount //guardian/music /mnt/music -o ip=192.168.1.15
sudo mount -t -o username=administrator,password=password //guardian/music /mnt/music
sudo mount -t smbfs //guardian /mnt/music 

almost everyone returns these errors

-without password-

Anonymous login successful
24716: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

-or-

-with a password-

24725: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

---

### Post by jazee on 2006-04-24
So no one has any ideas on my delema at all?

---

### Post by Ramses de Norre on 2006-04-24
[Try this]("http://ubuntuguide.org/#automountnetworkfoldersall")
And do you have smbfs installed?

---

### Post by unnes on 2006-04-24
I just successfully did this today, so hopefully what worked for me will work for you too. I couldn't get on the network using "Network Servers" in the Places menu, so I went to the terminal. The folder I was trying to mount was shared publicly as "movies" on my laptop, which has a local IP of 192.168.2.4. So I used the following terminal commands:

> sudo mkdir /media/laptopmovies
sudo mount //192.168.2.4/movies /media/laptopmovies/

And it worked fine, no password or anything required. Hope this helps!

---

### Post by jazee on 2006-04-25
Ok cool. I got it to work using ramses meathod. I tryied yours unnes and still got the same error. Thanks for the help.

---

