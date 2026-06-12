---
title: "How can I back up my 9.04 system?"
date: 2010-05-26
forum: General Help
---

### Post by Seepgood on 2010-05-26
I have been using 9.04 since it came out and recently I have decided to move on to 9.10 and after some testing, to 10.4 since it is an LTS version. But since I have spent so much time configuring and finetuning my system, I want to be able to transfer all that work to 9.10 and 10.4 as well. What backup choices do I have? I would like to backup not only ~/ but also configuration files, installed programs, extra fonts I have installed, ssh keys etc.

---

### Post by sdennie on 2010-05-26
In general, the important things to backup are /etc and /home.  Sometimes important things live in /var as well but, unless you have specifically put important things there, you can probably ignore it.

I recommend using one of the myriad of backup tutorials using rsync on the internet to backup /etc and /home.  After that, restore /etc and /home after you've re-installed and just re-install what you previously had installed (maybe do a dpkg -l before re-installing to see all the packages you installed).

I'm sure that there is a more automated way but, if you have an intact /etc, you've not lost information about how your system should run.  In fact, as long as you keep /etc around, a re-install is sort of a Daemon House Cleaning as you'll only re-install exactly what you need.

---

### Post by offshoredevelopment on 2010-05-26
If you are going to be getting your back up your 9.04 system, I would suggest making a custom live CD using a tool like remastersys. It's very easy to use and completely portable then after you will install it.

---

### Post by dino99 on 2010-05-26
look at clonezilla

---

### Post by lovinglinux on 2010-05-26
To restore you programs see [Umarks](http://umarks-extension.blogspot.com/).

---

### Post by Seepgood on 2010-05-27
Thanks for the quick answers everybody.

I will probably use rsync to copy /home, /etc and /var to an external drive and use dpkg -i to get a list of installed programs. I looked into clonezilla but I haven't made a linux backup before and I dont think I'm capable of doing a really targeted backup with those tools. I also looked into umarks but it wasn't available for my version of firefox.

Two new questions: 

[LIST]
[*]don't I have to copy /usr and /root for the rest of the conf files and the conf files for programs installed as root?
[*]after I backup my data, how am I going to incorporate them into the new version of ubuntu? just copy my old /home over the new black /home in 9.10 for example? And how am I going to reinstall my installed programs all together? Is there a command where I can give apt-get a list-file I created with dpkg and let it do all the installing unattended?
[/LIST]

I'm a complete newbie at linux backups and data transition and I need to get it right the first time.

---

