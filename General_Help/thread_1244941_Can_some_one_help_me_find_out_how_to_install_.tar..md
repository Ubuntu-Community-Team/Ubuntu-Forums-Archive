---
title: "Can some one help me find out how to install .tar.gz files?"
date: 2009-08-20
forum: General Help
---

### Post by Khazzy on 2009-08-20
I still have no idea what I'm doing in ubuntu, and I've had to go through finding multiple programs just to find out how to run one. If someone could help me find out how to install .tar.gz files, it would be much appreciated.

---

### Post by mthalis on 2009-08-20
[http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually](http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually)

---

### Post by dhughes on 2009-08-20
If you download a file called "filefoo.tar.gz"

To unpack it use Terminal, change to the directory or path where the file is located, type the command tar using the appropriate options after "tar" ```
tar zxvf filefoo.tar.gz
``` 

 If you saved it to your Desktop you would use this ```
tar zxvf /home/mycoolusername/Desktop/filefoo.tar.gz
```

A whole lot of crap flies by on the screen.

You now have an unpacked file, and even more stuff.

 Pretty much the gist of it is, do this next, in order.

./configure

make

make install



Even better, here is a link to a much better explanation: [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by Gen2ly on 2009-08-20
Ok, I'm not for over complicating things but the basic: ./configure; make; make install, may not always be a good idea.  There can be alot of options that go along with a program some that are needed for functionality.  Look for a README file or INSTALL file first and see if the authour has a recommendation.  If there isn't dig through the Makefile/config file, comb the home page and get the details.

---

### Post by CatKiller on 2009-08-20
> **Khazzy said:**
> I still have no idea what I'm doing in ubuntu ... If someone could help me find out how to install .tar.gz files, it would be much appreciated.

Installing from some file off the Internet isn't really the best approach to take if you're inexperienced. Installing through the package manager (System &#8594; Administration &#8594; Synaptic Package Manager) would be a much better approach.

A .tar.gz file is just a compressed archive, like a .zip file. What's inside it is anyone's guess. You might have downloaded source code, in which case you'll need to compile it before you can use it, or you might have just downloaded a collection of files that can be run as soon as you've extracted them. Since you've not said what you've downloaded, or what application it's for, anything we tell you is just speculation.

---

### Post by Khazzy on 2009-08-21
Okay, heres whats going on: I tired to download a game called Phun Physics Sandbox.
I was told I needed a program called Alien to properly install it.
But to install Alien, I need to download something called libpng3 but it was in .rpm
So to open .rpm  I need to download a program that can convert them
I found a conversion program but I have no idea how to install it because it's in the .tar.gz file.
I've done all the things you guys have suggested but I'm about ready to just fall to tears because nothing I try to download or run works >_<

I have no clue if I have a compiler or not or how to find one, please, for the love a sanity, I just wish I had some one to help me here, I mean I've looked for tut's and nothing helps. I am confused ottah my mind.

---

### Post by Cheesemill on 2009-08-21
Alien **is** the program that you use to convert rpm files.
 
You can install alien by simply typing the following into a terminal:
```
 
sudo apt-get install alien

```

---

### Post by lykeion on 2009-08-21
> **Khazzy said:**
> Okay, heres whats going on: I tired to download a game called Phun Physics Sandbox...


You shouldn't need to convert any rpm packages with alien to install Phun.

The **easiest way to install Phun** is to download it from getdeb here: [http://www.getdeb.net/app/Phun](http://www.getdeb.net/app/Phun) 

Alternatively you could download it from the Phun homepage, but then you have to make sure you have all dependencies installed to be able to run it. (installing the debian package from getdeb takes care of that automatically for you)

Hope this will help you...

Note: You'll find Phun in the Applications menu under Games

---

