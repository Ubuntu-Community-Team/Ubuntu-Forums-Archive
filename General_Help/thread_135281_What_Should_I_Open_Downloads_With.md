---
title: "What Should I Open Downloads With?"
date: 2006-02-23
forum: General Help
---

### Post by Mark76 on 2006-02-23
The ones here

[http://dagobah.ucc.asn.au/mozplugger/](http://dagobah.ucc.asn.au/mozplugger/)

---

### Post by Mustard on 2006-02-23
Is there a reason why you can't get mozplugger using the Synaptic Package Manager?  I ask this because thats the normal way someone on Ubuntu would install mozplugger.

If for some reason you **have** to have that version of mozplugger, then you need the .deb version (that is the version that has the .deb file extension).  To download, click on the link in Firefox and save to Desktop.

When you have it on Desktop, you would need to do these commands to...

```
cd ~/Desktop
#This will change the working directory in terminal to the Desktop
```

```
sudo dpkg -i insert_package_name_here.deb
#the dpkg command will handle the installation of the .deb, and check for any dependencies that need to be installed along with the package in question
```

If the .deb of mozplugger from the above website doesnt work you will need to compile from source, using the version at that website that ends in the .tar.gz extension.  Now we are moving into an area that is not so simple to explain.

You would really save yourself a lot of grief by going to the Synaptic Package Manager in your System>>Administration>>Synaptic menu and using the search button to find mozplugger, then right clicking on it and choose Install.  Then hit apply and *voila*..packaged is installed.

---

### Post by Mark76 on 2006-02-23
What do I have to use to open a download of Opera TP9?

---

### Post by Mark76 on 2006-02-23
I wish to God there was a program that acted as an install wizard :(

---

### Post by Mustard on 2006-02-23
I would read over this link that explain the installation of opera


[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

You want the .deb package for Opera.

[http://www.opera.com/download/](http://www.opera.com/download/) 

Some insight into how you went with the last question you asked would be good too.  Did the answers solve your problem?  Did you find Synaptic Package Manager?

For general information on doing a host of things on Ubuntu, you could try looking at this guide...
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

---

### Post by Mark76 on 2006-02-23
I found synaptic package manager.  But synaptic package manager isn't finding Opera 9

---

### Post by Mustard on 2006-02-23
[QUOTE=Mark76]I wish to God there was a program that acted as an install wizard :([/QUOTE]

Welcome to the world of linux. :)

Synaptic Package Manager is pretty easy to use and has over 17,000 packages for you to install on your system.

It's more the choice of programs that you want to install that is leading to you having to jump through hoops to install stuff.

---

### Post by Mustard on 2006-02-23
[QUOTE=Mark76]I found synaptic package manager.  But synaptic package manager isn't finding Opera 9[/QUOTE]

Well...yes..there is no getting around that.  If you want to use Opera, then you have to install it outside of Synaptic Package Manager.

---

### Post by Trab on 2006-02-23
use AutoMatix to install opera...??

---

### Post by mcduck on 2006-02-24
You can get opera with synaptic/apt-get if you add this line to your sources.list: 'deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free'

Edit: this might help you too: [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

