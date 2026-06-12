---
title: "Security Issues!"
date: 2010-03-24
forum: General Help
---

### Post by cityydude on 2010-03-24
**[COLOR=black][FONT=Verdana]Hello All,[/FONT][/COLOR]**
**[COLOR=black][FONT=Verdana] [/FONT][/COLOR]**
**[COLOR=black][FONT=Verdana]I ran into a few problems after the installation was completed. I installed Apache, Mysql and Php5 just fine. But in order to make the system more secure I needed to change a few settings in each of these systems. I was able to change the php5 :[/FONT][/COLOR]**[COLOR=black][FONT=Verdana]

**expose_php = on to off just fine.**

**But I was not able to locate the two settings I needed to change in apache. I need to change these two settings:**

**ServerTokensFull to ServerTokensProd **
**ServerSigatureOn to ServerSignatureOff**

**I tried searching for these strings but nothing came up. Any idea where to find these settings and how to change them?**

**I then tried to install the firewall as per these instructions:**

**Sudo aptitude install shorewall**

**But it comes back saying it cannot find this file to install it. Any idea where it’s supposed to be or has it been replaced by some other firewall program?**

**Any help with these problems would be appreciated.**

**Thanks**[/FONT][/COLOR]

---

### Post by ankspo71 on 2010-03-24
Hi, 
Here is a link to the firewall that Ubuntu uses as default.
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
A good GUI for it is gufw. (I think you are running the ubuntu server edition though).

Also, I'm using an Ubuntu test release 10.04, and I can find shorewall in the repositories. So it should be there in Ubuntu 9.10 too. Maybe you need to enable more repository sources in /etc/apt/sources.list ?

I don't know the answer to your server security questions, but I'm sure other people do.
Hope this helps.

Edit: Yes, Shorewall is available in 9.10 as seen here [http://packages.ubuntu.com/search?keywords=shorewall&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=shorewall&searchon=names&suite=karmic&section=all)

---

### Post by Aped on 2010-03-24
here's what I did to find what you were looking for:

#$ cd /etc/apache2
#$ grep -inH 'Token' `find . -type f`


^ The above spits out the file and line numbers of all instances of 'Token' including what you want. Change 'Token' to 'ServerSignature' for your other variable to change. 

Spoilers: both look like they're in ./conf.d/security around lines 27 and 38. 

Be sure you put in a space when actually entering the variables, the way you have them written there won't do anything. 

Enjoy your server.


Edit/PS: Just as more of a breakdown on the commands used, since this is something I've found to be superhelpful, and is something I wish someone had told me about when I started... grep is a search-in-file tool and find is a search-for-files tool. Syntax for grep is: grep -[options] 'string-to-find' [filename (optional, you can pipe something into grep, for instance, though it wouldn't work here because it would break -H)]

The switches I used were -inH. -i just means ignore case-sensitivity, -n means give me line numbers (madly useful) and -H means show me the source name of this found line. Here, it shows us what file it found it in, but if you used cat bla/* | grep it would all just say 'Standard Input' instead. less useful. 

Find is super useful but mad tricky; `` <- tildes mean 'evaluate/execute this command and then use THAT info to execute the command around it. Also useful as hell. Find syntax is thus: find [directory] [options] --- find will just recursively check everything till it gets your hits, then spew those out. This time what I used was find . (to mean currentdir since I cd'd there) -type f (type file, don't need the directories or whatever) and that caused the grep to look in every file within /etc/apache2. 

So grep/find can get a specific string out of anywhere on your hdd! Hope I'm not being condescending here, just something that I discovered and wished I'd known for a lot longer.

PPS: Use sudo apt-get install shorewall-common, it's the new version or something I guess.

---

### Post by rnerwein on 2010-03-24
hi aped
+1 
i know all the options you used for grep and find - but never thougt about to combine them.
very helpfull. 
unix/linux is a never ending story.

ciao   :-)

---

