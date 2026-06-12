---
title: "Sage error with jsmath"
date: 2010-01-23
forum: General Help
---

### Post by AkiraBergman on 2010-01-23
Sage included in the 64b Karmic does not work properly. 

I compiled and installed Sage in /opt directory by unpacking it into that directory and issuing the command 'make'. It took few hours on my i5 machine. It works fine but gives the frequent warning when Help-Tutorial buttons are pressed in notebook();

> In order for jsMath to be able to load the additional components that it may need, the jsMath.js file must be loaded from a server in the same domain as the page that contains it.  Because that is not the case for this page, the mathematics displayed here may not appear correctly.

I noticed that the sage documents are stored in my user/Documents directory. The notebook() browser has the link;

[http://localhost:8000/home/admin/0/#](http://localhost:8000/home/admin/0/#)

There are two threads under sage+jsmath keywords at Ubuntu-Forums, but they are old;

[http://ubuntuforums.org/showthread.php?t=987954&highlight=sage+jsmath](http://ubuntuforums.org/showthread.php?t=987954&highlight=sage+jsmath)
[http://ubuntuforums.org/showthread.php?t=682038&highlight=sage+jsmath](http://ubuntuforums.org/showthread.php?t=682038&highlight=sage+jsmath)

Is the installation directory wrong? After the installation I noticed the following in the install.log file;

> To install in /usr/local/bin, /usr/local/lib, /usr/local/man and 
/usr/local/include, type

   make install

To install somewhere else, eg, /xxx/yyy/{bin,lib,man,include}, type 

   make install PREFIX=/xxx/yyy


---

### Post by AkiraBergman on 2010-01-23
I changed the default browser from Chrome to Firefox and did not have the error. So it seems this one is a Chrome problem.

Later on I realized that there is a Sage binary for Karmic 64b at the Sage site. That one also works. But the one you compile for yourself is apparently optimized for your machine.

---

### Post by endomorphin on 2010-07-17
I am experiencing this same error using Firefox.

Just compiled and installed Sage 4.5 on Ubuntu 9.10. I get a pop-up message when using the notebook that reads: "In order for jsMath to be able to load the additional components that it may need, the jsMath.js file must be loaded from a server in the same domain as the page that contains it.  Because that is not the case for this page, the mathematics displayed here may not appear correctly."

It appears every time the page is loaded, which is quite frequently when navigating around.

---

### Post by AkiraBergman on 2010-07-17
I got Sage 4.4.1 binary on Ubuntu 10.04(64b) and it works. I think it works on 9.10 as well. Why don't you try the binary Sage package for 9.10 or 10.04, in stead of compiling? Compiling is supposed to optimize Sage for your machine but the binary works pretty good as well.

---

