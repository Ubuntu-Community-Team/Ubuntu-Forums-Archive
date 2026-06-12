---
title: "root password confusion"
date: 2011-03-03
forum: General Help
---

### Post by papabehr on 2011-03-03
I am trying to install a lexmark 5600 printer driver.  It asks me for my root administrator password.  I enter the only password on the system as it is my home computer and I am the only user.  I get error message stating it is the wrong password.  I am confused.

---

### Post by CharlesA on 2011-03-03
The root account isn't enabled by default in Ubuntu. You use "sudo" (or "gksudo" if it's a graphical application) to run commands with root privlages.

See here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by papabehr on 2011-03-03
Thank You, one more question, I am in the linux learning stage.  The program or driver I am trying to install is (/lexmark-inkjet-[xx]-driver-[x.x.x]..i386.deb.sh).  What command line do I use to install the driver in the terminal.

gksudo "WHAT ELSE"......

---

### Post by ameximes on 2011-03-03
Short answer

install packages with apt or synaptic.
install deb packages with dpkg.

A causerie about Package Management Systems.
If you want to install anything on Ubuntu (or any distro provide a package management system) first, look if your repositories provide this.

For Ubuntu (or and Debian-like system) you will use apt.
@console
```
apt-get install package-name
```
@desktop
System > Administration > Synaptic Package Manager

If your repositories doesn't provide a package which you are looking for, second opinion is deb packages.
@console
```
dpkg -i package-name.deb
```
@desktop
Just double click on it.

If you have not a deb package then follow the installation steps of your software. 


> /lexmark-inkjet-[xx]-driver-[x.x.x]..i386.deb.sh

I don't know what it is, a deb package en capsuled with sh script?

what is the type of that file?
what is the output of 
```

less /lexmark-inkjet-[xx]-driver-[x.x.x]..i386.deb.sh

```

Is that a single file or a package (tar, zip etc.) ?

Anyway, now you have the key points of managing software on Ubuntu. 

Ask to google if you really want to learn 
["what is package management system linux"]("http://www.google.com.tr/search?hl=tr&client=ubuntu&hs=05z&channel=cs&q=what+is+package+management+system+linux&aq=f&aqi=&aql=&oq=")
["ubuntu package management system"]("http://www.google.com.tr/search?hl=tr&client=ubuntu&hs=nQf&channel=cs&q=%22ubuntu+package+management+system%22&aq=f&aqi=&aql=&oq=")
["what is synaptic"]("http://www.google.com.tr/search?hl=tr&client=ubuntu&hs=ZRf&channel=cs&&sa=X&ei=AUJwTbvoHsPNsgam0aGDDw&ved=0CBYQvwUoAQ&q=what+is+synaptic&spell=1")
"[apt howto]("http://www.google.com.tr/search?hl=tr&client=ubuntu&hs=bRf&channel=cs&q=apt+howto&aq=f&aqi=&aql=&oq=")"

"[ubuntu repositories]("http://www.google.com.tr/search?hl=tr&client=ubuntu&hs=XmK&channel=cs&q=ubuntu+repositories&aq=f&aqi=g1&aql=&oq=")"

---

### Post by CharlesA on 2011-03-03
> **papabehr said:**
> Thank You, one more question, I am in the linux learning stage.  The program or driver I am trying to install is (/lexmark-inkjet-[xx]-driver-[x.x.x]..i386.deb.sh).  What command line do I use to install the driver in the terminal.

gksudo "WHAT ELSE"......

It's a shell script that installs a deb (I think).

To install it, you can run this:

```
sudo ./lexmark-inkjet-[xx]-driver-[x.x.x]..i386.deb.sh
```

You can also use tab completion to save some typing - type lex and hit tab. :)

---

