---
title: "General Help with DOSbox... I need a C: drive..."
date: 2011-04-12
forum: General Help
---

### Post by Tiger's Eye on 2011-04-12
I am new to Ubuntu and need help with getting DOSbox to work. For the record, I found these three very helpful links:
[http://www.ubuntugeek.com/howto-auto-mount-a-drive-in-dosbox.html](http://www.ubuntugeek.com/howto-auto-mount-a-drive-in-dosbox.html)
[http://ubuntuforums.org/showthread.php?t=171970](http://ubuntuforums.org/showthread.php?t=171970)
[https://help.ubuntu.com/community/DOSBox](https://help.ubuntu.com/community/DOSBox)
The problem is that I cannot get any of it to work. I can't find a C: drive.

This is exactly what I did. I opened the terminal and typed "mkdir dosprog".
It didn't say anything. Then I open dosbox by typing "dosbox" into the terminal. Once there, I type "config -writeconf /home/user/dosbox.conf". It says:

Config tool:
Use -writeconf filename to write the current config.
Use -writeconf filename to write the current language strings.
Z:\>

Then I type "exit" and it closes and I'm back in the terminal.
In the terminal I type "sudo gedit dosbox.conf" and put in my password and it opens gedit, but this is where I have my first problem. It's empty. There is nothing there in the dosbox.conf file. WHY???

So I gave up on automounting the drive for the moment and decided I would try to simply mount it. Except the problem is I don't have a C: apparently and can't create one.
I tried typing "mkdir ~/dos/c" into the terminal, but it answers me with

mkdir: cannot create directory '~dos/c': No such file or directory

It lets me make the dosprog directory, but not the dos/c one. Why?? How do I get a C directory so I can mount it to my DOSbox and start playing?? For the record, the game I want to play is currently on my desktop. Not sure if I should put it somewhere else...

Thanks!

---

### Post by Nytram on 2011-04-12
I'm not sure how to go about automounting the C: drive as I've never tried that before.

For manual mounting you don't need to create a C directory, instead you tell DOSBOX to use one of your folders as the C: drive.

For example if your game was in the directory

**~/Desktop/game/**

Then you would start DOSBOX and type

**mount c ~/Desktop/game/**

Then while still in DOSBOX type

**c:**

This will change the directory to your game folder. From there you can use standard DOS commands sucn as **dir** to see a list of files, and you can run the game by typing its filename (it will have the extension **.com .exe or .bat**)

---

### Post by Tiger's Eye on 2011-04-12
Thank you sooo much! It worked! You are a life saver :D:D:D:D:D

---

### Post by LostFarmer on 2011-04-12
I do have dosbox but not to good at setting it up.  Look in /home/usename/.dosbox/ (hidden folder) does it have dosbox-0.74.conf  (--0.74=version #)?  If so you can edit it.

I would move you game to a folder on /home.

here is my {autoexec} last part of file.
```
[autoexec]
# Lines in this section will be run at startup.
mount D: /mnt/DadStorage/
 mount c: /mnt/DadStorage/base
C:
cd dbase
dbase z
exit
```
I'm runing a old dos progarm 'dbase' it is in /mnt/DadStorage/base/dbase

hope this helps some.

---

### Post by Yellow Pasque on 2011-04-12
Manual mounting gets annoying. Open your dosbox.conf with gedit (don't use sudo).

This is my autoexec section at the end:
```
[autoexec]
# Lines in this section will be run at startup.
mount c *DIRECTORY_GOES_HERE*
mount d /media/cdrom -t cdrom -ioctl -usecd 0
```

---

### Post by Nytram on 2011-04-13
> **Tiger's Eye said:**
> Thank you sooo much! It worked! You are a life saver :D:D:D:D:D

You're welcome good to hear it worked for you.

---

