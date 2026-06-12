---
title: "Question !!!"
date: 2012-02-24
forum: General Help
---

### Post by Amer syr on 2012-02-24
hi :
I just need some help please :
(Ubuntu 11.04):
when I try to get any software from (Ubuntu software center) , I get this message :
The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

and it asks me to repair problem ...... when I press repair , I get this message :
Package operation failed

The installation or removal of a software package failed.
-------------------------------------------------------------------------------
what should I do to repair this problem ???

---

### Post by hakermania on 2012-02-24
Answer !!!




















OK, kidding...
Press Ctrl+Alt+T and then type:
```
sudo su
```
and press enter. Type your login password (it won't show anything, not even *** but it's normal) and press enter. After this, type
```
apt-get install -f
``` and press enter. Post back the results!

---

### Post by westie457 on 2012-02-24
Did you try ```
sudo apt-get install -f
```

You will be asked for your password, nothing will show on the screen as you are typing it.

If any errors post them here in [code] tags by clicking the # symbol and pasting between the brackets.

Thank you.

---

### Post by 23dornot23d on 2012-02-24
You need to open a terminal - something like lxterminal or konsole

then type in

[B]sudo apt-get update

sudo apt-get -f install[/B]



The first command just makes sure everything is uptodate .....

The second command tries to fix any problems it finds ..... 

Then post back any results that you get in between code tags ....

Some one may be able to help further - if there are any other problems ...

Hope this helps ... ;)

---

### Post by Amer syr on 2012-02-25
thank you all , but problem hasn't solved
I think I have to reinstall ubuntu

---

### Post by oldos2er on 2012-02-25
Three people have requested information from you to help solve your problem, wouldn't you rather help them help you than reinstall? It's up to you.

---

### Post by Amer syr on 2012-02-25
> **oldos2er said:**
> Three people have requested information from you to help solve your problem, wouldn't you rather help them help you than reinstall? It's up to you.

[SIZE=3]excuse me oldos2er .... I did all things they told me to do ....... but the problem hasn't solved yet ....
can you help me if you know the answer ???

I am so thankful for people who tried to help me .
but the problem is still existing


[/SIZE]

---

### Post by forrestcupp on 2012-02-25
The people helping you wanted you to post the output that you got in the terminal after entering those commands. Sometimes entering the commands doesn't work, and you'll get an output that explains what is going on. If the commands don't just fix it, we need to know what the terminal output was so we can help troubleshoot what's going on.

When they said to post the results, they didn't mean for you to say that the result was that it didn't work. By results, they meant the output you get in the terminal after entering those commands.

---

### Post by Amer syr on 2012-02-25
> **forrestcupp said:**
> The people helping you wanted you to post the output that you got in the terminal after entering those commands. Sometimes entering the commands doesn't work, and you'll get an output that explains what is going on. If the commands don't just fix it, we need to know what the terminal output was so we can help troubleshoot what's going on.

When they said to post the results, they didn't mean for you to say that the result was that it didn't work. By results, they meant the output you get in the terminal after entering those commands.
[SIZE=3]thank you for explaining Mr. forrestcupp
this is what i got in terminal[/SIZE]


```

root@PHANTOM-PC:/home/phantom# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  smbclient
Suggested packages:
  cifs-utils
The following packages will be upgraded:
  smbclient
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/13.7 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error: parsing file '/var/lib/dpkg/status' near line 17449 package 'x11-apps':
 field name `Original-Maintainer8' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

---

### Post by cortman on 2012-02-25
> **Amer syr said:**
> [SIZE=3]thank you for explaining Mr. forrestcupp
this is what i got in terminal[/SIZE]


```

root@PHANTOM-PC:/home/phantom# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  smbclient
Suggested packages:
  cifs-utils
The following packages will be upgraded:
  smbclient
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/13.7 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error: parsing file '/var/lib/dpkg/status' near line 17449 package 'x11-apps':
 field name `Original-Maintainer8' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

Ok, here's a set of instructions to fix it. Follow these carefully.

Open a terminal and run

```
gksu gedit /var/lib/dpkg/status
```This will open the file "status" in the gedit text editor. In gedit, click the "Search" button, and select "Go to line". Go to line 17449. Find the line near 17449 that says

```
Original-Maintainer
```and put a colon

```
:
```right after maintainer. For example, my status file reads

```
Original-Maintainer: Sebastien Bacher <seb128@debian.org>
```Add the colon, save it, and run

```
sudo apt-get update
```and post if any errors appear, although this should fix it.

---

### Post by Amer syr on 2012-02-25
> **cortman said:**
> Ok, here's a set of instructions to fix it. Follow these carefully.

Open a terminal and run
.
.
.
.

[SIZE=2]Thank you very much Mr.cortman
this is the result
[/SIZE]```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  smbclient
Suggested packages:
  cifs-utils
The following packages will be upgraded:
  smbclient
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/13.7 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 158237 files and directories currently installed.)
Preparing to replace smbclient 2:3.5.8~dfsg-1ubuntu2 (using .../smbclient_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb) ...
Unpacking replacement smbclient ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/smbclient_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/smbclient_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by Amer syr on 2012-02-25
[SIZE=2]**Can some one help me to solve this problem ???**[/SIZE]

```

phantom@PHANTOM-PC:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  smbclient
Suggested packages:
  cifs-utils
The following packages will be upgraded:
  smbclient
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/13.7 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y

(Reading database ... 158237 files and directories currently installed.)
Preparing to replace smbclient 2:3.5.8~dfsg-1ubuntu2 (using .../smbclient_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb) ...
Unpacking replacement smbclient ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/smbclient_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/smbclient_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)




```

---

### Post by collisionystm on 2012-02-25
Do this 

Sudo apt-get clean 

And then try to install the package again

---

### Post by Amer syr on 2012-02-25
[SIZE=3][COLOR=Black][B]Thank you very much Mr.collisionystm . It's done.
[/B][/COLOR][/SIZE][COLOR=Black][SIZE=3]**):P):P):P**[/SIZE][/COLOR]

---

### Post by Amer syr on 2012-02-25
Thank you all . It's done
):P):P):P

---

### Post by collisionystm on 2012-02-25
Your welcome =)

---

### Post by oldos2er on 2012-02-26
Threads merged, please don't start more than one thread per question.

Also please use the default font when posting. From the forum's posting guidelines: "Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. [size=2][COLOR=pink]Funky[/size][/COLOR] non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser."

---

