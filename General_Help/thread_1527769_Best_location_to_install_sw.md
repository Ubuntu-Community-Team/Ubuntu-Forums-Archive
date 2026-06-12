---
title: "Best location to install s/w"
date: 2010-07-09
forum: General Help
---

### Post by HughJarse on 2010-07-09
Where should you install software?
There isn't a "Program files" directory.

---

### Post by blur xc on 2010-07-09
> **HughJarse said:**
> Where should you install software?
There isn't a "Program files" directory.

Normall when you isntall software it put's its files where they belong automatically.

What are you doing?

BM

---

### Post by davidmohammed on 2010-07-09
very true - thats windoze thinking.

Download software from known repositories such as from software center or getdeb.  These install and configure automatically.

You rarely have to download and compile software.  Even then, just follow the normal installation instructions - normally something like sudo make install

---

### Post by ov3rcl0ck on 2010-07-09
If it asks you to put it in a folder either put it in your home folder or in the Opt folder. the /usr folder is where most of the application data goes for most linux installs but the way its layed out makes it hard for a new comer to understand, and the symlinks are touchy so don't screw with the /usr directory till you know what you're doing with it.

---

### Post by HughJarse on 2010-07-09
Was trying to install HJ split but it doesn't work. Will use my Windows pc for that job.

---

### Post by blur xc on 2010-07-09
> **HughJarse said:**
> Was trying to install HJ split but it doesn't work. Will use my Windows pc for that job.

eh - hem... 
> OS requirements for **HJSplit**:  	OS: Win95/98/98SE/Me/2000/NT/XP/2003/Vista/7  

I don't see Ubuntu or any Linux OS listed.  Could try it in Wine though...  
```

sudo apt-get install wine
```

right click the .exe file and clikc intall w/ Wine- ymmv

BM

---

### Post by HughJarse on 2010-07-12
> **blur xc said:**
> eh - hem... 


I don't see Ubuntu or any Linux OS listed.  Could try it in Wine though...  
```

sudo apt-get install wine
```

right click the .exe file and clikc intall w/ Wine- ymmv

BM

[http://www.freebyte.com/hjsplit/]("http://www.freebyte.com/hjsplit/")
Second link on page is Linux

---

### Post by HughJarse on 2010-07-12
The real answer I was after was, 
Software gets installed to eg) **etc** folder or **bin** or whatever ubuntu uses. I know you shouldn't need to know but it would be nice to see where files get placed, in case you want to tidy up your system or something.
The issue with this one was it was asking me where I wanted to unpack it/install it.

---

### Post by bodhi.zazen on 2010-07-12
See :

[img]http://www.techbu.com/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg[/img]

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

Package managers (apt / apt-get / aptitude/ synaptic) will take care of everything for you.

If you are installing something outside of the Ubuntu repositories, there is not Universial standard. IMO you should use

/usr/local

For example , /usr/local/bin

Some systems prefer you use

 /opt

---

