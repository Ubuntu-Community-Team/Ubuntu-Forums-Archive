---
title: "Child Lock?"
date: 2010-09-02
forum: General Help
---

### Post by phantom27 on 2010-09-02
I want to be able to start a movie on my ubuntu 10.4 machine and then hand it to my daughter (it's a netbook).  Is there a program (or setting) to lockdown the keyboard and mouse so she can't change the movie?

Obviously there would have to be a hidden password or something.

Any suggestions?

---

### Post by rbc on 2010-09-02
Just saw this mentioned on the forums last night. Only partially what you are asking for, as it does not lock the mouse. Interesting nonetheless. If you get no other answers, maybe you could just unhook the mouse while she's watching
[http://csincock.customer.netspace.net.au/lock-keyboard-for-baby.htm](http://csincock.customer.netspace.net.au/lock-keyboard-for-baby.htm)

---

### Post by phantom27 on 2010-09-02
> **rbc said:**
> If you get no other answers, maybe you could just unhook the mouse while she's watching


Except it's actually a touch pad... There is a function key combo to disable the touchpad so I guess all I need is a program to disable the keyboard.

---

### Post by phantom27 on 2010-09-02
I just found this [http://linux.softpedia.com/progDownload/Lock-keyboard-for-Baby-Download-23745.html]("http://linux.softpedia.com/progDownload/Lock-keyboard-for-Baby-Download-23745.html")

Will this work?

I downloaded it but I can't figure out how to install it.  When I click open it just loads up in a text editor.  I'm sure it has something to do with how ubuntu installs programs but I'm a total newb.  I'm sure it's an easy fix but...  

Please help.

---

### Post by CharlesA on 2010-09-02
It's a perl script.

You'd have to make it executible and then run it with perl /path/to/script.pl

---

### Post by phantom27 on 2010-09-02
> **CharlesA said:**
> It's a perl script.

You'd have to make it executible and then run it with perl /path/to/script.pl

Ok?

How do I do that? (remember I'm a newb)

---

### Post by CharlesA on 2010-09-02
Should be able to just right click on it and go into the properties and make it executable from there. Then double click to run it.

Also note: normally it's better to only install stuff from the repos, as the packages there have been checked and found to not be malicious.

A script on some random site isn't guaranteed to be safe.

I've looked over the source, and it looks ok, but I'm not perl expert.

---

### Post by phantom27 on 2010-09-03
Ok.  I figured out how to check "allow executing file as a program".  That was easy.  

When I run the program nothing happens.  At least I can't tell that anything happened.

---

### Post by phantom27 on 2010-09-03
Ok.  I figured out how to run the program.  It seems to work good.

Here is another question:  How do I put it in my list of Applications?

---

### Post by CharlesA on 2010-09-03
You can add it under System > Preferences > Main Menu.

Either that or just create a launcher on the desktop: Right click on desktop > Create Launcher.

---

### Post by phantom27 on 2010-09-03
Thank You.  

Works great.

---

