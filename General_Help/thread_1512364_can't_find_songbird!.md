---
title: "can't find songbird!?"
date: 2010-06-18
forum: General Help
---

### Post by mina299 on 2010-06-18
Hey, I deleted the songbird icon from my start menu bar, I don't know, ASSUMING it would just be under Applications/Sound & Video on the start menu bar... menu?  Where the hell is it?

What I did: right click: delete.  Come home from shopping, want some music, not in the menu anywhere!  Songbird files are still where they always were.  Cannot find the icon that launches the damn thing.  Help?!

Ubuntu 9.04

:confused:

---

### Post by ajgreeny on 2010-06-18
There are several ways to go:-

1.  use command ```
locate -i songbird
``` which will show all files with "songbird" in the name, and will include the executable, for which you can then make a launcher.

2.  Even better, use command ```
whereis songbird
```will do more or less the same, but only find binaries or executables.  This only works for executables in your $PATH, as far as I'm aware, so if you installed songbird manually, the executable could be elsewhere, even in your /home, and not found with this command.

3.  What happens if you use the command ```
songbird
``` in terminal?

---

### Post by ronnielsen1 on 2010-06-18
> whereis songbird

I used whereis and which in another distro but for some reason it doesn't work for me in Ubuntu 10.04. Is there a package I need to install?

---

### Post by ajgreeny on 2010-06-18
Not that I'm aware of.  I certainly didn't knowingly install whereis, but it works on my system.

What do you get as output when you use "whereis songbird" in terminal.  If there is no songbird to find it should just say **songbird:**  If whereis is not a known command you would get an error message of some sort.

My suspicion is that songbird was installed somewhere out of your $PATH so the command can not find it, or it is not installed at all.

---

### Post by mina299 on 2010-06-18
Fantastic!!  How do I do that?

If you haven't figured this out already, I'm new to this.

---

### Post by mina299 on 2010-06-18
Alright, I'm not completely helpless; I went into the "ubuntu help" section and did some reading.  Did the search in the terminal.

whereis songbird did not do anything, I hit enter and it just said "songbird," however, upon entering "locate -i songbird" I got all the files I previously found the hard way (the Windows way, at any rate).  I obviously, as I was born and raised with Windows (well, DOS, too), *naturally*, I assume .exe is the file extention used for an executable file, but am I wrong? Should I be looking for something else? I scanned over it twice and did not see one.

If it is NOT there, does that mean it's gone for good?  Should I just re-download the program?

All I did was right-click and delete the icon from the top panel!  Why would that even begin to permanently delete my executable file?  It doesn't add up that the only place such a file would be stored is in the top freaking panel.  What the hell?  It must be somewhere.  I refuse to believe that it had indirectly deleted my actual program off the face of my hard drive.  It must be somewhere.  Is there another way to find it?

---

### Post by mina299 on 2010-06-18
Sorry, didn't see your question.  You asked what happened if I just used "songbird" as a command.  This is what happened:

mina@mina-laptop:~$ songbird
bash: songbird: command not found
mina@mina-laptop:~$

I'm screwed, aren't I?

---

### Post by oldos2er on 2010-06-18
> **mina299 said:**
>  *naturally*, I assume .exe is the file extention used for an executable file, but am I wrong? 

*.exe doesn't really apply to Linux. Executables are determined by one set of file permissions (see [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)).

How did you install Songbird?

---

### Post by ajgreeny on 2010-06-19
In your output from ```
locate -i songbird
``` look for a file simply called **songbird** either in your home, or in /usr or /usr/bin, or perhaps in /opt.

When you find it, try and double clicking on the file, which may be a shell script or the executable itself.  If that starts songbird, just make a launcher for that file and add it to the panel or desktop, as you prefer.

---

### Post by mina299 on 2010-06-19
Well, I searched those folders and I could not find a file just called "Songbird."  Before that, I repeated my "locate -i songbird" in the terminal and filtered through the results, and none of the file names were just "songbird," so I felt that my manual search wouldn't pan out.  I did it anyway, because, you know, what the hell.

So I actually don't know how this was installed.  Someone else installed this for me.  Does the system have a history that shows that sort of thing?  That might prove useful!  Otherwise, I've exhausted all suggestions and I'm hungry for more.  How would I re-download the thing so that I don't overwrite the files I have for songbird already?  I'm tempted to just re-download it, isolate the executable file (whatever the hell that is) and paste over the remaining files.  However, as this is not Windows, I am unclear on how such a thing is done.

---

### Post by ajgreeny on 2010-06-20
Here you go to reinstall songbird, but be advised that there is no longer a mozilla linux version and this has been added from a ppa repository, so be prepared for problems, though they are no at all likely.

**Install Songbird in Ubuntu Jaunty and Intrepid**

Add the GPG Key first. Copy-paste the following line to  Terminal.```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5719E347
```
[LIST]
[*]Now, You  will have to add the following songbird-daily repo to your third-party  repository list.
[/LIST]


[LIST]
[*]For that, goto ***System - Administration -  Software Sources***, select the ***Other Software*** tab  and Click ***ADD***.
[/LIST]

[LIST]
[*]Now,  copy-paste the following line.
[/LIST]

**For Ubuntu Jaunty 9.04**
```
deb [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu) jaunty main
```

Now click on the reload button, if it does not do that automatically.

Songbird should now be available with sudo apt-get or synaptic.

---

