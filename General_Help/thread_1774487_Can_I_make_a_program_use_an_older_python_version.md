---
title: "Can I make a program use an older python version?"
date: 2011-06-03
forum: General Help
---

### Post by theophiles on 2011-06-03
I need to know how to make a program use a version of python older than the newest one. I am trying to run the Traipse fork of OpenRPG. Through their forums, I have learned that one of my problems is that I am running too new a version of python. I have python 2.7.1 installed.

I also have python2.6.6 installed, so I should be able to use that. My first thought was to uninstall 2.7.1 and just use the older version. The problem is that if i uninstall 2.7.1, it wants to also uninstall all the packages dependent on that program. Let's face it, in Natty Narwhal, that is pretty much everything. 

Do you know how to force Traipse make it use the 2.6 version?

---

### Post by oldfred on 2011-06-03
I think you just tell it to use 2.6. If you look in /usr/bin you find the pythons. python will just be a link to the current installed version 2.7, you can in your programs then use either python or python2.7. There then is also a link from python3 to the current version of python3 which in my Maverick is python3.1. I run python3 programs with this 

#!/usr/bin/python3.1
# -*- coding: utf-8 -*-

But now I realize I could have just used python3 and it will use current version 3.

You should just be able to say python2.6. Check /usr/bin.

And it is a good thing you did not uninstall 2.7. Users who have done that with older versions had to reinstall as network was also lost. Current versions seem to be repairable with chroot to reinstall just about everything.

---

### Post by theophiles on 2011-06-03
Found out [here]("http://www.rpgobjects.com/forum/viewtopic.php?f=4&t=2795&p=13182#p13182")

you simply type python2.6 in the terminal and then the filepath.

---

