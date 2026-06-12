---
title: "Skype and others..."
date: 2005-02-12
forum: General Help
---

### Post by mips on 2005-02-12
I have read the forums and other resources and I'm lost. I took the plunge this morning and formatted my old WinXP partition and did a Ubuntu install.

So far I like it but I'm battling to install apps. I would love to simply click on a file and it must install but it seems Linux is not very friendly in this way, I'm willng to learn though.

How do I install  "skype_1.0.0.1-1_i386.deb"   ??? I need an idiots guide here. I have installed  "libqt3c102-mt", I think via Synaptic. What now ?  ](*,) 

The same goes for firefox, I downloaded the latest version but battling to install it.

Any assistance would appreciated.

Thanks
mips ]

---

### Post by machiner on 2005-02-12
Welcome to the world of computing...

To install software in the Ubuntu system is light years ahead of windows in form and functionality.

You can either use a terminal ( apt-get install <program> )
or run Synaptic (as you have seen already) and search for your appy.

apt runs off a list called "sources.list" this file contains the servers and directories that house all the software you could possibly want (ahem! more on this later) . You cannot install software if the repository list does not contain the server that contains that software...

unless you download a src file or otherwise packaged program and install it yourself, which is just as easy.

In order for you to take advantage of this functionality please search for repositories or goto the unofficial Ubuntu help reference (how-to in this forum). You will find a wealth of knowlege and you will see that indeed you do have the capability to :

"I would love to simply click on a file and it must install but it seems Linux is not very friendly in this way, I'm willng to learn though."


Happy Computing.

---

### Post by mips on 2005-02-12
Thanks, I did read all the how-to docs but i was still lost.

Ok, I got skype working with "sudo dpkg -i skype_1.0.0.1-1_i386.deb". This is a far cry from simply clicking on the file !!! A average windows user would have given up a long time ago. These things have to be made friendlier if linux wants to stand a chance as a user friendly desktop OS.

How do I add the App to my desktop or apps toolbar, the learning curve is steep....

Where am I supposed to stored all these installed apps ? Surely there is a "correct" folder for them ? bin etc ?

I understand the principles of a repository and adding one to Synaptic. How would you find a repository for Skype, I assume their is none. Can you use a normal web/ftp site as a repository ? Also figure out you can use apt-get for stuff in the repository.

I would like to add packages downloaded on my local system available in Synaptic or something of the sort and then just click on them to install ???

I will try FireFox next, may the force be with me...

cheers
mips

---

