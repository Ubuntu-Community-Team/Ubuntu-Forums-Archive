---
title: "How to download and extract a file"
date: 2012-07-18
forum: General Help
---

### Post by pstonge on 2012-07-18
Hey guys, I am kinda new to linux, and I am using ubuntu 11.10 server at work, and we need to upgrade our helpdesk software, so after doing some research we want to go with OTRS helpdesk. But I am having a hard time on the first step, which is to download a tar.gz 'source' file then extract it to /opt. 

My question is, how do i download this file with ubuntu server, its not like just typing in a web browser and clicking it. haha so I am having a hard time.
 
Can anyone help me out with this, 
[http://www.otrs.com/open-source/get-otrs/software-download/](http://www.otrs.com/open-source/get-otrs/software-download/) 
that is the link to get the file that i need, but again, how do i get that onto my server to extrace and move the file. 
 
Thanks everyone.

---

### Post by steeldriver on 2012-07-18
you can use wget

---

### Post by Primefalcon on 2012-07-18
a command line browser is lynx, which will allow you to browse web pages and even download files....
to install simply type
```
sudo apt-get install lynx
```

however if you know the full url you could just use wget

to extract a file simply use tar -xf <filename>

then move the extract files to where you want using cp or mv

---

### Post by Xero Xenith on 2012-07-18
In this case the commands you would need to use are (modified very slightly from above)

```
wget http://ftp.otrs.org/pub/otrs/otrs-3.1.7.tar.gz
tar -xf otrs-3.1.7.tar.gz -C /opt
```

(wget is simple, just downloads it. The -C on the tar command puts it where it needs to be without using mv. You will need to put "sudo" in front of the last one if you're not already root.)

---

### Post by pstonge on 2012-07-18
Thank you so much guys, I am about to try this out...

---

### Post by pstonge on 2012-07-18
Alright so i have tried both of these;

sudo wget [http://ftp.otrs.org/pub/otrs/otrs-3.1.7.tar.gz](http://ftp.otrs.org/pub/otrs/otrs-3.1.7.tar.gz)
 
&
 
sudo wget [http://www.otrs.com/open-source/get-otrs/software-download/otrs-3.1.7.tar.gz](http://www.otrs.com/open-source/get-otrs/software-download/otrs-3.1.7.tar.gz) 
 
and both times i get this,
 
Resolving [ftp.otrs.org]("ftp://ftp.otrs.org").... 178.63.12.4
Connecting to [ftp.otrs.org|178.63.12.4|80]("ftp://ftp.otrs.org|178.63.12.4|80")......
***then it just times out, and restarts and times out...

i get the same output when i try both URL's but obvouslty the www. has resolving [www.otrs.com]("http://www.otrs.com") instead of [ftp.otrs.com]("ftp://ftp.otrs.com"), but w/e they both resolve, but then hang when connecting...

I am using this in a Virtualbox. I do have an address, from our network. 10.x.x.x, 
 
I am able to ping [www.google.com]("http://www.google.com") with good replys, so i have connection. 
 
I am able to ping, the [www.otrs]("http://www.otrs"), but not the [ftp.otrs]("ftp://ftp.otrs").
 
I am confused as to why this will not download, i have connection to atleast the www. site, so i should be able to download it from there, right?
 
Thanks 
Paul

---

### Post by Primefalcon on 2012-07-18
he meant put sudo in front of tar... not wget

and 

```
wget http://ftp.otrs.org/pub/otrs/otrs-3.1.7.tar.gz
```

worked for me

---

