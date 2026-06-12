---
title: "MCEdit?"
date: 2011-07-27
forum: General Help
---

### Post by lukebargh106 on 2011-07-27
Hello,
I am 'new' to Ubuntu and I have installed Minecraft, and have downloaded the MCEdit folder, I have read the Read-Me and done the 'apt-get install python-numpy python-opengl python-pygame', how-ever I don't know how to install/run the actual file... If you have any ideas, please post in this thread, Thank's in advance
-Luke.

Screen-Shot:
[[IMG]http://img3.imageshack.us/img3/4930/screenshotmcp.png[/IMG]]("http://imageshack.us/photo/my-images/3/screenshotmcp.png/")

---

### Post by turtle153 on 2011-07-27
Right click the file and go to Properties, then the Permissions tab and click "Allow executing file as program". You should then be able to double click the file and select Run.

---

### Post by lukebargh106 on 2011-07-27
It doesn't do anything, It says 'Run In Terminal', 'Display', 'Run', and 'Cancel'.
'Run', doesn't do anything.

---

### Post by turtle153 on 2011-07-27
Run it in the terminal and see if there are any errors. Where's this download anyway, I can take a look.

---

### Post by lukebargh106 on 2011-07-27
[[url="http://www.minecraftforum.net/topic/13807-mcedit-minecraft-world-editor-compatible-with-mc-beta-173/"]MCEdit]("http://http//www.minecraftforum.net/topic/13807-mcedit-minecraft-world-editor-compatible-with-mc-beta-173/")[/URL]

If you scroll down, it says 'Windows' (I have tried Windows - No luck), and a bit lower it says, 'Linux'.

Download that and it's a .tar.gz file.

---

### Post by turtle153 on 2011-07-27
Have you got the right version? If your on 11.04 you'll need MCEdit's Python 2.7 download.

---

### Post by lukebargh106 on 2011-07-27
Thanks,
Got it to work.
I downloaded the 2.7 file.
Thank's again.

---

### Post by turtle153 on 2011-07-27
No problem!

---

### Post by c0upedeville on 2011-08-28
Hello. I wanted to make a post because I'm having just a small problem  with MCedit that's not allowing it to open and run. I am using Ubuntu  11.04 Natty Narwhal and have downloaded the tar.gz of MCedit that's the  stable-21 for python 2.7 and I have already ran the apt-get for the  required prerequisites(the python --version says 2.7.1+), but when I run  the command [sh mcedit.sh] in terminal it kicks out this error code  regarding one of the .pyo files.

{{{{MCEdit-stable21-linux$ sh mcedit.sh
python: can't open file 'mcedit.sh/MCEditData/mcedit.pyo': [Errno 20] Not a directory}}}}

I am still a novice user of Ubuntu, as I have a much more powerful  Windows 7 rig that I use 80% of the time but won't be running until I  get a new hard drive for it, and I wanted to ask you guys about this, hoping  that I might be able to get some help to resolve this problem. Thanks!

---

### Post by BigRedButton on 2011-12-22
Not entirely sure why, but the mcedit.sh is no good. I'm assuming there is some syntax the author didn't understand or something, anyways if you just run mcedit directly using
```
python -O MCEditData/mcedit.pyo
```
it works just fine. I had to exit out and restart it the first time I ran it, fyi.

---

