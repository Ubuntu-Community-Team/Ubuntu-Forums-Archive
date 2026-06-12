---
title: "Tool to load software downloaded from a internet site?"
date: 2010-02-23
forum: General Help
---

### Post by wlamore on 2010-02-23
Tool to load software downloaded from a internet site?
 
Does anyone know where in gnome desktop the tool for installing software downloaded from the internet or off a cd disk>
 
Thanks for the help

---

### Post by oldsoundguy on 2010-02-23
not a good idea to use some internet site that is not part of the system as a source for software.

And all of the Ubuntu software is in the repositories .. you don't install off of a cd.

Your software is in the software store or under system> administration> synaptic package manager.

---

### Post by akakingess on 2010-02-23
> **oldsoundguy said:**
> not a good idea to use some internet site that is not part of the system as a source for software.

And all of the Ubuntu software is in the repositories .. you don't install off of a cd.

Your software is in the software store or under system> administration> synaptic package manager.

Not necessarily, I remember when Chromium first came out and you had to download it. You do want to trust the site/CD/source that you are installing from, but can/has been done. 

What is the type of software that you are trying to install? Is it compressed, a bin file, or what? Just let us know what it is and we can know whether you need to use the console or you can use something else.

---

### Post by wlamore on 2010-02-23
Thanks it is a spanish dictionary from an internet site that openoffice word processor directs you to.  when you pick it for download, it just says "get it".  
[http://extensions.services.openoffice.org/es/project](http://extensions.services.openoffice.org/es/project)
 
If you can tell me how to download it from the site and what download tool in gnome ubuntu will install it to office, it would be very helpfull.  
 
I am missing something in my reading.
 
thanks

---

### Post by akakingess on 2010-02-23
I just took a quick look, but it looks like they are all zipped files, so you can just download it to your home folder, and unzip it to the Open Office plugins folder, but I will have to find that unless you already know where it is. Let me know if you know where Open Office tells you to install it to, or if you need me/us to figure it out. I will await your reply before digging any further. 


EDIT: Just saw the post from 2hot6ft2, thanks for posting that, because that is much easier ;)

---

### Post by 2hot6ft2 on 2010-02-23
How about this from the comments page for the spanish dictionary there.
> openoffice spanish dictionary for ubuntu

Hi all,
for ubuntu users, type:
```
sudo apt-get install myspell-es
```
to install the spanish dictionary for openoffice


---

### Post by wlamore on 2010-02-23
I appreciate the informaition but I do not follow it without a gui tool that will download and open and install to OpenOffice word processor.  It downloads with "get it" in suse 11.2 and uses a tool found in Yast that opens it automatically and installs it? 
 
Can you clarify why Yast can do this and Ubuntu gnome cannot.  
 
Not critical of Ubuntu, just new to getting around it and using it to do what I want to do. 
 
Thanks

---

### Post by 2hot6ft2 on 2010-02-23
> **wlamore said:**
> I appreciate the informaition but I do not follow it without a gui tool that will download and open and install to OpenOffice word processor.  It downloads with "get it" in suse 11.2 and uses a tool found in Yast that opens it automatically and installs it? 
 
Can you clarify why Yast can do this and Ubuntu gnome cannot.  
 
Not critical of Ubuntu, just new to getting around it and using it to do what I want to do. 
 
Thanks
Well you haven't said just what the file is you're trying to install .tar .deb or whatever. Your link goes to a page with a lot of stuff.
Ubuntu uses software repositories if you want to do the same thing with a gui then go to
System > Administration > Synaptic Package Manager
Click on it
Enter your password and hit enter
search for myspell-es
Right click on it and select install
Click on Apply
Click on Apply

There you've done the same thing as opening a terminal
Applications > Accessories > Terminal
and using
```
sudo apt-get install myspell-es
```
Hitting Enter
entering your password and hitting enter

If you download a .deb then double clicking on it installs it. Instead of saving it to your pc you can have an application open it and install it. GDebi is the app. for installing it. So just choose open with GDebi

---

