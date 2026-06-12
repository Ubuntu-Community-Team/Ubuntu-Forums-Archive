---
title: "tar.gz help"
date: 2010-10-21
forum: General Help
---

### Post by 234jango on 2010-10-21
I am 100% new to Ubuntu and I am not really sure how things work. The main thing I am confused about is how to install files that are compressed as tar.gz. Remember, I am really new to Ubuntu so give me instructions that I would understand. 

Thanks. :)

---

### Post by TBABill on 2010-10-21
Before you install anything from tar.gz, have you confirmed the application or driver is not already in the repositories? You can search by name in either Synaptic package manager or the Ubuntu Software Center. I prefer Synaptic, but either works. You always want to choose from software in the repositories first because installing from outside sources can lead to update or upgrade breakage down the road, leaving you to learn quickly about your OS to get it going again.
 
Just food for thought. If you still need the tar.gz info, just post back. Also: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by WorMzy on 2010-10-21
The first thing you should do with a tar file is extract it's contents and read the README file if there is one. More often than not it'll give you clear instructions on how to install the software, telling you how to compile it if what you've downloaded is the source code. If there's no readme in the tar, then look on the website where you downloaded it from to see if there's any instructions on there.

Of course, checking the repositories first is the best way to install software. It's much easier, and you're less likely to run into problems regarding dependencies.

---

### Post by 234jango on 2010-10-21
I checked, and it wasn't in the repo's. I saw in the file there was a README it says "You'll need mono and log4net:

# sudo apt-get install mono liblog4net-cil-dev

Then, build it:

# mdtool build

And run it!

# bin/Debug/LOIC.exe"

How do I run/ build those things? :3

---

### Post by WorMzy on 2010-10-21
Open a terminal (Applications -> Accessories -> Terminal) and type/copy-paste the commands in. 

```
sudo apt-get install mono liblog4net-cil-dev
```

I dunno if that command will fully work, there's no such package as "mono" in the repositories for Lucid or Maverick, only Dapper. You may need to install mono-complete instead.

After that's finished installing, you'll need to change directory in the terminal to the directory where all the extracted files are. To do this, run

```
cd /path/to/the/directory
```

e.g. "cd /home/jango/Desktop/loic"

*Then* you can run the next command in the readme:

```
mdtool build
```

After the build has finished, you can presumably run the application by running

```
bin/Debug/LOIC.exe
```

Note that that will only work while your terminal is still inside the original code's directory. You'll need to declare the full path to the executable in the future. e.g. "/home/jango/Desktop/loic/bin/Debug/LOIC.exe".

Try all that and see how you fare.

---

### Post by mc4man on 2010-10-21
you'll probably need to install a few lib's to compile - I assume this is what you're up to ?
[http://encyclopediadramatica.com/LOIC](http://encyclopediadramatica.com/LOIC)

---

### Post by directhex on 2010-10-22
mdtool is part of apt:monodevelop

---

### Post by 234jango on 2010-10-22
Hmm... I'll try what WorMzy suggested.

---

### Post by ebasa on 2010-10-22
If you identified the mystery program you may get more specific help.

---

