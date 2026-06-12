---
title: "Could somebody help me for once?"
date: 2011-04-28
forum: General Help
---

### Post by twtgd09 on 2011-04-28
I've tried installing foxit reader on 10.10, but when i download the deb and double click, the software center comes up, i click install, the bar fills up, then im given the option to install it again, and whenever i go to office foxit, nothing opens.

---

### Post by KegHead on 2011-04-28
Hi!

Have you downloaded gdebi from the software center, if not do so.

After installing, you can right click on your deb file.

You'll be given instructions.

KegHead

---

### Post by twtgd09 on 2011-04-28
didnt work

---

### Post by hwttdz on 2011-04-28
Or try running 
"gdebi-gtk ?????.deb" from the command line, or even "gdebi ????.deb" and tell us what sort of errors you get. 

In general people can help you if you title your threads something like "installing foxit reader from .deb on 10.10".

---

### Post by KegHead on 2011-04-28
Hi!

Do this on your terminal;


jim@jim:~$ [COLOR="Red"]sudo apt-get install gdebi[/COLOR]
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdebi is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jim@jim:~$ 

And post.

KegHead

---

### Post by kseise on 2011-04-29
It looks like it is installed.  Please open a terminal and run foxit from the terminal.  Please post the output here.

---

### Post by KegHead on 2011-04-29
Hi!

That's my machine!

I'm trying to help twtgd09 install gdebi!

KegHead

---

### Post by sikander3786 on 2011-04-29
Or this might help.

[http://ubuntu4beginners.blogspot.com/2011/04/package-is-of-bad-quality-software.html](http://ubuntu4beginners.blogspot.com/2011/04/package-is-of-bad-quality-software.html)

---

### Post by kseise on 2011-04-29
> **KegHead said:**
> Hi!

That's my machine!

I'm trying to help twtgd09 install gdebi!

KegHead

Oh, my bad.  Well, it "software center" won't install it, why not try using synaptic 

```
alt+f2 synaptic
```
or
open gnome-terminal and type:```
 sudo synaptic
```
or 
open gnome-terminal and type: ```
sudo apt-get install gdebi
```

---

### Post by jmore9 on 2011-04-29
I went here and downloaded the linux version :

[http://www.foxitsoftware.com/downloads/](http://www.foxitsoftware.com/downloads/)

Then i unpacked the bzip 

Then opened the folder and double clicked on the exe and i had foxit runnig.  Open a couple of pdfs just to make sure.

Din not find any deb packages just a bz file and in the bz is an executable file which is foxit

---

### Post by KegHead on 2011-04-29
Hi!

It's much easier to download .deb files and open them w/gdebi.

KegHead

---

### Post by jmore9 on 2011-04-29
Well as i said i could not find foxit in the repos and the site that builds foxit gives that out for linux.

Thats one way of getting foxit.  Just create a luncher for it and your done

---

### Post by KegHead on 2011-04-29
[http://www.foxitsoftware.com/pdf/desklinux/download.html](http://www.foxitsoftware.com/pdf/desklinux/download.html)

---

