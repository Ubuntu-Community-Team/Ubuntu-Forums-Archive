---
title: "Lan web based search engine for ubuntu server."
date: 2010-10-20
forum: General Help
---

### Post by Coder68 on 2010-10-20
I am looking for a good search engine that I can install on my Ubuntu Server 10.04 .  I want it to search my LAN (NAS mostly), and for us to be able to go to a web page to search for various types of files. jpg, mp3, .doc, etc. I do want it to search my PC's as well.

I found Solr and a few others, but I cant seem to find what exactly they search or what file types they find and  how to install them.

I have a mix of Windows, and Linux + a Western Digital NAS.  I plan to add a NAS with a Linux OS later.  Ubuntu or one of the NAS distros. I want to be able to search them as well. 

Any ideas?

---

### Post by Coder68 on 2010-11-02
Bump.

I want to index my mp3's video files, text files, .odt files etc. I want to be able to search via a lan based website.

Can anyone give me some ideas?

Thanks,

C68

---

### Post by Crazedpsyc on 2010-12-09
[www.**htdig](www.**htdig)**.org/
HTDig indexes everything that is linked to, so If there is a "Downloads" page or a "Pictures" page it will take every link from there. It seems to get both the name of the picture and the "alt" flag in the html if you have it.
It is meant to index all files (including html php etc) but in its configuration file (explained thoroughly in the running instructions on thier site) you can put "jpg png gif bmp mp2 mp3 odt ods odb odc..." to have it only index those files.
Then as it says, run "sudo rundig -v" to start the indexer. Just watch out, if you link to any external sites it can start indexing half the internet ;) (you can safely stop it from doing this by pressing Ctrl+C in the terminal right when it starts listing external sites)

Good Luck!

---

### Post by Coder68 on 2010-12-17
Yes, I have looked at that.

I need a web page that users can go to and type in what they want to look for. (Think average users.) I need to to act like Google, but on the LAN only.

Thanks,

Coder68

---

### Post by Crazedpsyc on 2010-12-29
Well there is google custom search... But I think it is commercial.
If you have any experience programming (ie. in python and cgi or django) You could fairly easily create your own. as simply as listing the directories you want to index on each computer and adding the lists to a database, but that might take a while depending on the size of your network. If I get some extra time I will try making a very simple one for you, but I do not guarantee it will be as easy and powerful as google.

What do you think is difficult about running htdig anyway? You could just set it up quickly and shedule rundig to run on the main server every so often. If the config is what's driving you away from it, I can just upload my conf file with plenty of comments

---

