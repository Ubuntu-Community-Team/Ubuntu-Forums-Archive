---
title: "installing a driver for my printer"
date: 2010-11-14
forum: General Help
---

### Post by No Names Please on 2010-11-14
Lexmark impact s305

I downloaded this file from the maker: lexmark-inkjet-09-driver-1.5-1.i386.deb.sh.tar.gz

There were no instructions on how to install this, and I have no clue.

Help! 

Thanks.

---

### Post by TeoBigusGeekus on 2010-11-14
Double click it and open it with the archive manager. Extract it somewhere, say your desktop.

If its a .deb file, just double click it and it will install automatically.

If it's a .sh file, it is a script. Right click it, select properties>permissions>Allow file to be executed. The navigate to your desktop via terminal and execute it, i.e.
```
cd ~/Desktop
sh nameoffile.sh
```

If it's none of the above, it's probably a source folder. Extract it in your desktop and compile it yourself, i.e.
```
cd ~/Desktop/NameofFolder
make
sudo make install
```

---

### Post by No Names Please on 2010-11-14
Sorry, but none of these worked.

I double clicked after extracting and an install program launched -- but came to a grinding halt when it asked for my administrative password -- which it rejected over and over and over. I only have the one password -- the one I use to install repository programs and reopen my screensaver. Most baffling.

Then I tried the sh thing. It too launched the install program, and I had the same result.

Then I tried the make thing. I figured "nameoffolder" represented the place where the extracted tar.gz file should be, so I created a folder called Lexmark and moved the extracted file there, and then tried the make line. No luck. The response was "No targets specified and no makefile found.  Stop."  Then I tried returning the extracted file to the desktop, make again, and same result. 

So nothing.

Note that the maker's website says that the file is specifically for Ubuntu. I found some instructions in German which I don't understand, and tried to follow them by following the coding instructions, and still the same thing.

Am I now SOL?

And why should people have to go thru these conniptions to make a driver designed for Linux work? With XP, it is OK and forget about it.

---

### Post by TeoBigusGeekus on 2010-11-15
By googling the filename of your driver, I've come up with this.
So, just extract it, navigate to its folder and give the command mentioned (preceded with sudo - that's what # means)
```
sudo ./lexmark-inkjet-[xx]-driver-[x.x.x]..i386.deb.sh
```

---

### Post by TNT1 on 2010-11-15
> **No Names Please said:**
> 

Then I tried the make thing. I figured "nameoffolder" represented the place where the extracted tar.gz file should be, so I created a folder called Lexmark and moved the extracted file there, and then tried the make line. No luck. The response was "No targets specified and no makefile found.  Stop."  Then I tried returning the extracted file to the desktop, make again, and same result. 





Cause it's already compiled.

---

