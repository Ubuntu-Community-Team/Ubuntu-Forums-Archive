---
title: "Some help with Ubuntu server please"
date: 2012-09-03
forum: General Help
---

### Post by krai havok on 2012-09-03
Hi everyone. 

OK so I have always wanted a dedicated server that I could have at my house that I could store my stuff on and maybe have access to from over the internet, so I decided to set up a file and FTP server at my house using some old parts I had laying around. This is something I have never done before however and now, after switching out some motherboards with different cases, installing different hard drives and other parts and finally getting the stable version of ubuntu server to boot I am now faced with having to actually set up the ftp and file server, and I have no idea where to go now. I found some tutorials on how to set up the different parts the network and give different commands but I am not really following what they are asking me to do. 

Does anyone have any idea where I can find a noobs step by step guide on how to set up an ftp and file server? Can anyone tell me what I should be doing now? 

Thank you in advance):P

---

### Post by Old_Grey_Wolf on 2012-09-03
They instructions are not easy. You should secure it if you expose it to the Internet. For the FTP server [https://help.ubuntu.com/12.04/serverguide/ftp-server.html](https://help.ubuntu.com/12.04/serverguide/ftp-server.html)

---

### Post by drdos2006 on 2012-09-03
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings on your network.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.590_all.deb
###  	web site is here: http://sourceforge.net/projects/webadmin/webmin_1.590_all.deb
Install with :
sudo dpkg -i webmin_1.590_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to your server to edit files, create shares, startup daemons etc..

regards

---

### Post by krai havok on 2012-09-05
OK so I finally got Ubuntu server loaded onto a terminal, and got the GUI to go with so that I wouldnt feel so damn lost lol. 

Anyhoo so now I want this guy to by a file and FTP server for my home and when I go elsewhere. 

So here is my next question - does anyone have a step by step tutorial on how to set this guy up as a file and FTP server? I clicked on the link given in this thread and it comes up as page not found. 

Keep in mind that when it comes to Linux I have dabbled (and I mean that in a very loose way) but I am by no means a Linux Jedi, so any help or a finger in the right direction would be grand.

Thank you

C

---

### Post by kevinthecomputerguy on 2012-09-05
dont click this:
[https://your_server_ip:10000/](https://your_server_ip:10000/)

click this:
[http://woodel.com](http://woodel.com)

-Kevin

---

### Post by krai havok on 2012-09-07
> **kevinthecomputerguy said:**
> dont click this:
[https://your_server_ip:10000/](https://your_server_ip:10000/)

click this:
[http://woodel.com](http://woodel.com)

-Kevin

Kevin,

You sir are a scholar and a gentleman. 

That tutorial was excelent. Both concise and easy to follow. i managed to make it to the end of the second page (about 4 hours worth of reading / putting into practice the instructions. It was totally worth it. I am not done yet however, I have just come to a point where I am not entirely sure my head is not going to explode from all the info I just crammed into it. So for now - I rest. 

Thank you again sir!!

PS - you were right webmin is quite powerful

Chris

---

### Post by kevinthecomputerguy on 2012-09-07
:- )

---

### Post by krai havok on 2012-09-09
Hey Kevin, another question ...

While I have gotten the server set up and can access it through webmin via the [http://static](http://static) ip address:10000, for some reason the name of the server is not "playing nice" (as so aptly put in the tutorial) with the static ip address. In other words I can't seem to access it using the name of the server. The IP can access it, and I even tried putting in the ip address.com and it went to the web area that was set up (/var/www) like it was supposed to. 


I thought maybe it was a mispelling of my domain name, and I thought I went back and checked but I dont know if I check every area that you can check.

Any words of advice on this?

---

### Post by lisati on 2012-09-09
My experience of webmin suggests that http[COLOR="Red"]s[/COLOR]://my.site:10000 usually works better; if I use plain http, webmin won't let me in.

---

### Post by krai havok on 2012-09-09
Hey thanks for the reply.

I tried the http"s" (without the quotes of course) and still got nothing. I am not really sure what else to do about it to be honest. 

Also, I have noticed that when uploading and downloading stuff to and from the server I am not allowed to send stuff that is in a folder. Although I have just learned how to access the FTP through windows explorer, and found that you can just copy / paste stuff. Is that how we do it? I haven't tried on folders yet but I was just wondering if that was the way to do it. And for that matter when I am somwhere else (like at a friends house) and I want to upload stuff, do I have to do it through webmin or is there another way? I am sure these questions and more will all be answered through the tutorial but I am asking them as they come to me. 

Thank everyone for their patience and answers

Chris

---

### Post by kevinthecomputerguy on 2012-09-10
If I seem short its because I'm replying from my phone.

For folders you can zip them into a zip file and then upload them via webmin, or use ftp copy / paste, or better yet you will learn Sftp later in the guide.

For naming you will learn lots on page 3 via samba, but the bigger picture here is advanced, there is nothing wrong with your servers name, there just isn't a dns server in place telling your other computers how to find your Linux box, so until you finish page 3 and until you learn more about dns, just keep using the ip. But you issue may be solved (bandaide) after sambas setup.

---

### Post by krai havok on 2012-09-13
Thank you for the reply Kevin

and thank everyone who tried to help me.

I am going on in the guide and will see where it gets me - if I have any other questions at that point I will let yall know.

You guys are awesome!!:guitar:

---

