---
title: "Aaargghhh.  Java"
date: 2006-02-21
forum: General Help
---

### Post by Mark76 on 2006-02-21
I need the java runtime environment for a chatroom in a forum I visit but I can't seem to find the right download for my distro (5.10 x86).

Help? :?

---

### Post by simon_is_learning on 2006-02-21
[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)

Linux (self-extracting file)

you'll recive a .bin file.

sudo chmod + x "filename"
(make it executable)

then ./"filename" 
(mount the file)

It will install it self

---

### Post by Mark76 on 2006-02-21
Erm... I'm really new at this.  How do I do this sudo thing?

---

### Post by Jedeye on 2006-02-21
you can put sudo before any comand to give it root privilages. It will follow by asking for your password.

---

### Post by Mark76 on 2006-02-21
Sorry, I'm lost. What do I need to open first?

---

### Post by Jedeye on 2006-02-21
It would probably be easier to open up System>Administration>Synaptic package manager and run a search for j2re1.4 there is also j2re1.4-mozilla-plugin... just check the boxes and hit apply

---

### Post by Jedeye on 2006-02-21
almost forgot... check out Automatix it makes it easy to install a lot of things [http://ubuntuforums.org/showthread.php?t=66563]("http://ubuntuforums.org/showthread.php?t=66563")

---

### Post by Mark76 on 2006-02-21
It'd be nice if there was a download link

---

### Post by simon_is_learning on 2006-02-21
sorry if I gave you the hard way :oops: 

sudo means in ubuntu - act as root.
root is the equivolent to XP-Administrator.

sudo is used in the terminal.

Automatix may be the best choice for you. 

If you are looking for a download link its 
> 
wget [http://www.fuckbirdflu.com/automatix/automatix_5.4-3_i386.deb](http://www.fuckbirdflu.com/automatix/automatix_5.4-3_i386.deb)

wget is an app that lets you download using a program. And you have to write it in the terminal

Just follow the HOWTO, and you'll soon realize how it works.

And again - you need to be in the terminal. 
It's better to get used to it then to rely on GUI for everything.
also I find it faster.

Good luck

---

### Post by ajgreeny on 2006-02-21
It's worth getting to know the terminal as it will probably get you out of a few scrapes over time.  I have seen people say that automatix installs lots of unwanted progs as well as those you want and need.

I would go the synaptic method personally but it's your choice.

---

### Post by Mark76 on 2006-02-21
What am I doing wrong here?

> mark-williams@ubuntu12345:~$ sudo chmod + x e-1_5_0_06-linux-i586.bin

---

### Post by Perfect Storm on 2006-02-21
Automatix is one way tro do it another is this:

Open terminal (Application tab ---> Accessories ---> terminal) and write:

```
 sudo gedit /etc/apt/sources.list 
```

Now add the lines:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

Save it.
Go back to the terminal and write:

```

sudo apt-get update
sudo apt-get install sun-j2re1.5

```


To get the newest Java from suns homepage:

Download Download JRE 5.0 Update 6 (jre-1_5_0_06-linux-i586.bin file): [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)

Open the terminal:

```
 cd /where/you/saved/the/file
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
sudo update-alternatives --config java

```

Choose: 3        /usr/lib/j2sdk1.5-sun/bin/java

Testing:
```

java -version

```

also write **about: plugins** (without the space between : and p) in your browser to see if it's installed.

You might add Java Control center to your Apllication launcher:

Open the terminal:

```

smeg

```

In the left tree-viewer click **System Tools** and then **New Entry**

Fill it out:

Name: Java Control Center
Comment: whatever you want
Command: sh /usr/lib/j2re1.5-sun/bin/ControlPanel
Icon: You might find a good icon for this on the web or use the one I've added.

Press ok and close down the menu editor.

---

### Post by simon_is_learning on 2006-02-21
[http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)

sorry:
chmod a+x jre-1_5_0-linux-i586.bin

Then I also think that you'll need firefox-plugins.

You will find them using synaptic packet manager. It is an graphical tool for the apt-get program.

---

### Post by Mark76 on 2006-02-21
I've lost the damned terminal now :x

---

### Post by Perfect Storm on 2006-02-21
where you at and which of the howto are you following?

Terminal: Applications tab ---> Accessories ---> Terminal.
Right click on it and pick **add this to launcher panel** so you have the terminal right at your hand.

---

### Post by Mark76 on 2006-02-21
I don't know.  I'm just completely lost :(

---

### Post by Perfect Storm on 2006-02-21
Okay, just start all over and pick one of the way to install java and lets take it from there.

---

### Post by Mark76 on 2006-02-21
Okay, I've found it.

Now... I have the installation package for jre.  Tell me EXACTLY what to type in the terminal

---

### Post by Perfect Storm on 2006-02-21
If you copy and paste your terminal output it will make it a bit easier to help ;)

---

### Post by Mark76 on 2006-02-21
mark-williams@ubuntu12345:~$

That's what I see when I open it

---

### Post by Perfect Storm on 2006-02-21
Okay then download: Download Download JRE 5.0 Update 6 (jre-1_5_0_06-linux-i586.bin file): [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)

When downloaded type

```
cd Desktop
```
if you saved the file to the desktop

---

### Post by Mark76 on 2006-02-21
Okay, I changed directory to desktop.  now?

---

### Post by Mark76 on 2006-02-21
What exactly is the file name for this thing (jre) anyway?

---

### Post by Perfect Storm on 2006-02-21
Now we need to enable sources in your repo. to get full access to all the packages avaible for Ubuntu (around 18000). Why we need that? Because some of the packages we need to build a java package is not avaible by default, so we need the terminal again:

```
sudo gedit /etc/apt/sources.list
```

Where you can see lines with one # infront of their names, remove that # (but not where there is two of them).

Also add:

[b]## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
[/b]

Save it.

In terminal:

```
sudo apt-get update
```

Now for installing java:

```
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
sudo update-alternatives --config java
```

---

### Post by Mark76 on 2006-02-21
I can't do it.  I just can't :'(

---

### Post by Perfect Storm on 2006-02-21
Why not?

---

### Post by Mark76 on 2006-02-21
Actually I typed that before your last message

---

### Post by Perfect Storm on 2006-02-21
Okay this might be a little bit huge if you're new and building your own package.

The easy way is like this, but it only grant you update 5 and not update 6.

```
sudo gedit /etc/apt/sources.list

```

add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

save it.

```
sudo apt-get update
sudo apt-get install sun-j2re1.5
```

Then java installed.

---

### Post by Perfect Storm on 2006-02-21
[QUOTE=Mark76]Actually I typed that before your last message[/QUOTE]

ah okay, I just missed lol

---

### Post by Mark76 on 2006-02-21
Java is working :D

Now for Opera :lol:

---

### Post by Perfect Storm on 2006-02-21
Just add the lines for opera as shown above.

Then

```
sudo apt-get install opera
```

To launch opera, type opera in the terminal

You might look at this for plugins: [http://ubuntuforums.org/showthread.php?t=76236&highlight=opera](http://ubuntuforums.org/showthread.php?t=76236&highlight=opera)

---

### Post by Mark76 on 2006-02-21
How do I add Opera to my desktop/pulldown menus?

---

### Post by Perfect Storm on 2006-02-21
Simply right click on the desktop and click create launcher. Fill out the formel. Where it says Command, you put the same command to start opera as you did in the terminal.

For application tab, type

```
smeg
```
(or Applications tab ---> System Tools ---> Applications Menu Editor)
and you'll get the menu editor

---

### Post by Mark76 on 2006-02-21
I keep getting this every time I launch Opera

> Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not start plug-in executable 'operamotifwrapper'.
/usr/lib/netscape/plugins-libc6/operamotifwrapper-3
Please install Motif.

Plug-in path
(Path can be modified in Preferences dialog)

/usr/lib/opera/plugins
/usr/lib/mozilla/plugins
/usr/lib/netscape/plugins-libc6

---

### Post by Perfect Storm on 2006-02-21
Did you check the link I gave you?
I'm not an expert on opera, so you might use the search tool on the forum.

---

### Post by Mark76 on 2006-02-21
Damn.  Still having problems.

Downloaded Opera and JRE using automatix.  But now my browser crashes every time I log into the chat room I needed JRE for.  In Opera AND Firefox :mad:

---

### Post by Mark76 on 2006-02-22
Maybe if I knew the path to point Opera to

---

### Post by Perfect Storm on 2006-02-22
Try:

```
sudo update-alternatives --config java
```

Choose: 3 /usr/lib/j2sdk1.5-sun/bin/java

See if it helps.

---

