---
title: "How to install 'VLC'?"
date: 2006-05-07
forum: General Help
---

### Post by sidy on 2006-05-07
Hello, 

I've just installed ubuntu on my PC.

Can you tell please, how to install VLC, from the beginning?

I am on root.

Sidney

---

### Post by olsonar on 2006-05-07
do

```
sudo gedit /etc/apt/sources.list
``` 
and uncomment (remove the # from) the lines that look like this:

```
#deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
``` 
yours may say breezy instead of dapper. makes no difference.

now do:

```
sudo apt-get update
``` 
and then:

```
sudo apt-get install vlc
```


BTW, running in root is dangerous. just precede any command you need to execute as root with 'sudo' instead.

---

### Post by sidy on 2006-05-07
Hello,

After the update to be done I did:

sudo apt-get install vlc

then came up the following:

Reading package lists... Done
Building dependency tree... Done
E: Coudn't find package vlc

What shall I do now, please?

Sidney

---

### Post by sidy on 2006-05-07
I Am Still Waiting For Help Please!

---

### Post by bramvandijk on 2006-05-16
1. Make sure you have uncommented the lines with universe and multiverse in /etc/apt/sources.list (that is, removed the # in front of the lines)
2. Fire up synaptic from the menu
3. Press the "reload" (? could be another name, I use a Dutch version) button, it should be the big one on the left
4. Press "search"
5. type "vlc" and press enter
6. find the package "wxvlc" in the list and click te box left of it
7. Press the "apply" button

After these steps you will find VLC in the "Sound and Video" submenu

Note that I am at work right now, using XP, so details might be wrong...

---

### Post by sidy on 2006-05-19
It is working.

I did what u said.

Thank you.

---

