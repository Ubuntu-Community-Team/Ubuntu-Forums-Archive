---
title: "I need to connect to the LAN as a server"
date: 2006-05-24
forum: General Help
---

### Post by Isoss on 2006-05-24
I have a LAN of about 7 PCs and 2 linux systems (Ubuntu and Kubuntu) installed on on my Laptop and the other is on my main PC. Both have my websites and I work on both - and yes you can call me a geek - so I need to make both of them as servers. So how can I make Ubuntu a server to which all the other PCs are connected and can deal with it as a webserver (http, ftp, ssh ...). I know this is something done through Places -> Connect to Server ... in Ubuntu and System -> Remote Places -> Add a Network Folder in Kubuntu (of course correct me if I'm wrong!) I am not really familiar with servers and networks .. I've sticked to my PC my whole life and have dealt only with "real" webservers, you konw FTPing and stuff ... so I hope somebody can direct me to the right way and everything concerning ports and service type and whether it's passible to have 2 servers on the same LAN. Thanks in advance. Isos

---

### Post by Isoss on 2006-05-24
I also heard of an exe program for windows which enables other users on the network, who work on windows, to ftp using a unix shell command. I don't know it's name so .. hope some one of you knows!

---

### Post by Isoss on 2006-05-25
Hello ... it's been 17 hours since I last posted! somebody help me!

---

### Post by mybuffalo on 2006-05-26
Hi,

Please try this link on how to setup FTP server
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)
Hope this helps.

It is possible to have multiple servers on the same LAN.

P.S. You may wan to check out this link 
[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

---

### Post by Isoss on 2006-05-27
Ok, thanks a lot. I have installed proftpd and I have the upload and download folders.
Now I need to have access to my [http://localhost](http://localhost) from other computers. 
does any body know how? ... How to view [http://localhost](http://localhost), and how to developer the web files on the server but from another PC. Even if windows.

---

### Post by sYs^ on 2006-05-27
So you want to install a webserver like Apache?

Check this: [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by Isoss on 2006-05-27
[QUOTE=sYs^]So you want to install a webserver like Apache?

Check this: [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)[/QUOTE]

No, I already have it! I've been working on localhost for while and it's time to connect my PC to the network. 
So I have a webserver and all I want is to give access to the other PCs for read and write. I mean like they can access [http://localhost](http://localhost) "on the server" using the browser of course, and have access to the folders so they can modify the files and be able to upload and download.

That's it!

---

### Post by Herman on 2006-05-27
>  I have a webserver and all I want is to give access to the other PCs for read and write Hello, Isoss,   I would have thought that the link from mybuffalo to Frodon's FTP instructions would have done the trick for you.
 It's hard to imagine my link being any help then, but here it is anyway, (just in case it does help), making an [SSH Home Network]("http://users.bigpond.net.au/hermanzone/p11.htm").

It's just simple stuff to help new users get started, it will only take about fifteen minutes to try it between Linux boxes.  You can make every computer in your network an SSH server if you want.
There is a link included for information on SSH for Windows but I haven't tried SSH for Windows myself or heard from anyone who has used it. Hopefully it will allow all your machines to connect. 
Myself I just install Ubuntu or dual boot all computers, and connect all with SSH that way. I don't bother networking Windows, I just access them if needed.

Unless you need Samba, [link 1]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/")...[link 2]("http://hr.uoregon.edu/davidrl/samba.html")

I hope I'm being some help, Regards, Herman

---

### Post by Isoss on 2006-06-04
Hey Herman, thanks a lot it's pretty easy with ssh. I have a connection now between two linux systems and both have ssh server. Now the thing that left is accessing the localhost of the apache server of my PC from my laptop or anyother computer on the network. That is accessing the /var/www/ folder but as a client through the web brower using the index. I hope you understand what I mean. 

Another thing, is it possible to ftp using ssh? I mean using something like gftp to grant me an ftp path between my client laptop and my server pc as if ftping between a normal PC and any webhost!

Thanks.

---

