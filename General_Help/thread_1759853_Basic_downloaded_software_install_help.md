---
title: "Basic downloaded software install help"
date: 2011-05-16
forum: General Help
---

### Post by deadpool47 on 2011-05-16
Hey, I am currently trying to install PersonalBrain on my Ubuntu 11.04 and I came to realise I am Linux retarded. I got used to it for about a year, but for the most part I used the Ubuntu Software Center and Synaptic Package Manager to install software and learned to manage okay.

Thing is, I have used the terminal, but I don't know any of the coding or commands to generally install software being straight up downloaded form the net. Can you guys give me some help in just generally installing software?

---

### Post by sanderd17 on 2011-05-16
There are many ways to install software in Linux. Most software should be installed via the repositories (Software center, aptitude, apt-get, synaptic ...) but your software can't. The other ways to install software go from running a script in a package you downloaded to compiling the code.

But looking at the site of personalBrain, I think it is the following case:

I guess you have an archive file (zip or tar.gz or something else). So you should first unpack it. You can do it by right clicking on it in Nautilus. If you're lucky, there is a README file in it. Check it to see what file you need to run. If there is no such README file, try running a file with a relevant name. 

How do you run a file?

go into terminal and cd to the directory where your extracted files are
```

cd /path/to/extracted/files

```

make the file you want to run executable
```

chmod u+x fileIWantToRun

```
and run it
```

./fileIWantToRun

```

Then you should see what happens. If the file asks to be installed as root, put "sudo" in front of the last command.

---

### Post by aeiah on 2011-05-16
the file is PersonalBrain_unix_6_0_7_0.sh, which we can see from the .sh file extension, can be treated as a shell script. its massive for a shell script of course (about 11mb) so its probably got an archive packaged in there too. anyway:

you should be able to mark it as executable and double click it. it will pop up with a setup dialog. i recommend you launch it from a terminal though, so you can see what's going on if there's an error or something.

in a terminal, navigate to where you've downloaded it```
cd ~/Desktop
```
and run it```
./PersonalBrain_unix_6_0_7_0.sh
```

---

