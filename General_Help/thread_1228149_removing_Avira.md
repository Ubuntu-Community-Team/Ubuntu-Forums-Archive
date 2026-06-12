---
title: "removing Avira"
date: 2009-07-31
forum: General Help
---

### Post by Deathvalley122 on 2009-07-31
hi,

I have install avira on my ubuntu but now I can't remove it's bogging my pc down how do I remove it can I use rm to remove it? and I can't find in the package manager I installed it today to test it out now I can't remove it at all I need help on this issue on what to do ... idk what to do and I don't feel like formating my pc ...

Thanks,
Patrick Voege

---

### Post by guillaume_u on 2009-07-31
Hi,

Avira is not in the package manager, unless you added it to the list of depositories to download from, but I don't believe it's the way it works.

So, first you could try to prevent it from starting up :

From the command line
```
$ cd /etc/init.d (this is the directory for things that are launched at startup for every user)
$ ls | grep -i avira
```If the last command returns a result, I suggest you move the file
```
$ sudo mv TYPETHEFILENAMEHERE /home/YOURUSERNAME
```You can also check whether there is a startup entry for your user account :

```
$ cd
$ cd .config/autostart
$ ls
```If there is an entry for Avira, move it

```
$ mv TYPETHEFILENAMEHERE ../
```Anyway, I suggest you go to Avira's forum, they know better than me how to remove their own software I guess.

---

### Post by oldos2er on 2009-07-31
How did you install it?

---

### Post by kidoruigenso on 2010-09-12
Take a moment to be sure it is Avira that slows you down.  Perhaps you installed other antivirus packages at the same time, and one of these is the problem.  For example, I had AVG 8.5.810 for a while.  Basically, once logged in, AVG would create multiple instances of avgscand, the number growing with normal use of the system, that eventually consumed all of the available memory and swap file space, at which point the system was fully unresponsive.  From reading on the forum, it sounds like a kind of "memory leak".  Since these start with "avg" and Avira runs avguard that starts with "avg" you might have then confused.  For information, I was using Ubuntu 9.04, with 1Gb RAM and a 3Gb swap partition. 

When I installed Avira, I had unpacked the tar archive package as a folder in my home directory, in my case with name "antivir-workstation-pers-3.1.3.4-1".  In here I found a text file called "README.uninstall".  This was my guide.  

First, from a terminal, I stopped avguard using "sudo avguard stop"

From the terminal, I changed directory to where the Avira uninstall script was located, using "cd ~/antivir-workstation-pers-3.1.3.4-1".

From the terminal I then issued the command "sudo ./uninstall --product=all"

Hope this helps.

---

### Post by steez2002 on 2010-09-16
open terminal>navigate to the directory where your avira install files are. As for me I kept avira install folder after installing in "Downloads".

once in your install directory type

sudo ./uninstall --product=all

answer some questions all defaults were no 

and there you go.

FYI this is somewhat listed in the README.uninstall file that accompanied the install. 

If you added the Avira status icon to your panel, just remove it by right clicking it and remove

If you were to look you can no longer add that icon to panel as Avira is gone.

Steez2002
No Problems Only Solutions

---

### Post by steez2002 on 2010-09-16
sorry [kidoruigenso]("http://wwww.ubuntuforums.org/member.php?u=1147554") for reposting what you posted... lol I didn't see yours.

---

