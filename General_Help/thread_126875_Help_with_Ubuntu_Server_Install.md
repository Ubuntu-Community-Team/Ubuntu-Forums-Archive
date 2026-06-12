---
title: "Help with Ubuntu Server Install"
date: 2006-02-07
forum: General Help
---

### Post by barqster on 2006-02-07
OK, I installed ubuntu server....first of all was I supposed to partition it in any speccfic way? Second of all, all I want on it is samba; all I want to use it for is a file server. Lastly, how do I edit files with the server installation?

---

### Post by barqster on 2006-02-07
Oh by the way, just to clarify, ubuntu is on another computer.

---

### Post by soulestream on 2006-02-07
[www.tldp.org](www.tldp.org)

partitioning is really up to you, the size of your drives, and what you are doing with it. By default i believe ubuntu formats a / and a /swap only. Which for basic stuff is probably fine. I would have probably done a /, /swap and a /data partitiion. Just makes restoring/changing distros easier. 

sudo apt-get install samba

will get you samba. then you need to edit your smb.conf file.

You can either use vi, vim, emacs, or nano to edit your files

sudo vim /etc/samba/smb.conf

or use samba-swat

search the forum for "swat" it should tell you how to enable it on ubuntu if its not. I dont use ubuntu for a file server, so im not sure if it is or not. With swat after you have it setup, you can edit samba from another PC, via a webbrowser. Can be handy when you are first learning.

soule

---

### Post by barqster on 2006-02-07
Ok, so I edited my my smb.conf, my /etc/network/interfaces, and /etc/hosts, andy /etc/apt/sources.list....It's still not working....do you know any other place I could see an example of these files using VIM?

---

### Post by barqster on 2006-02-08
I can't get my internet connection to work....on my windows computer it says they're connected, but I'm pretty sure I messed up the conf. file....can somebody help?

---

### Post by dcstar on 2006-02-08
[QUOTE=barqster]I can't get my internet connection to work....on my windows computer it says they're connected, but I'm pretty sure I messed up the conf. file....can somebody help?[/QUOTE]
It would probably be more helpful to you to do forum searches for each specific problem you encounter, the answers to your individual problems are probably just waiting for you to find 'em.

Post back here if you don't quite understand the solutions you find.

---

### Post by barqster on 2006-02-08
I know, I've looked and I've seen the same redundant information. I know it might seem like I just jumped to the boards for help without looking for myself. I'm sure the answer is out there, but I believe it's hiding from me....Oh well, the search continues. If anyone knows any easier way to configure my files while I'm in server installation mode. Oh, and if anyone can help me out with the debfoster aproach, that'd be great too.

---

### Post by richw on 2006-02-08
There appears to be no easy way to edit config files in server mode, unless you install a GUI.  I prefer to use nano when editing files - its very simple to use!

If you don't mind loosing about 9Mb of RAM, it may be worth looking at Webmin - it offers a web browser based GUI and can be rather helpful!

Internet access can you ping machines on the internet? Can you ping IP addresses? This would give us some more info. Some websites do block pings.

---

### Post by barqster on 2006-02-09
I like to use VIM in server mode, took me a while but I figured it out. I would like to use Webmin, but how do install it if I can't access the internet? Do I burn the tar (or whatever they're using) and pop it in on my ubuntu computer?

---

### Post by richw on 2006-02-09
Yes you could, but it would be better to get the net connection working.

See if you can ping a). via hostname and b). via ip address. You MUST ping to a  machine on the internet (that does respond to a ping).

---

