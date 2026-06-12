---
title: "How to install Postfix on Ununtu 10.10"
date: 2011-03-12
forum: General Help
---

### Post by AdRock952 on 2011-03-12
I am trying to install Postfix on Ubuntu 10.10 but the configuration screen I am getting is not the same as others i've seen online in instructions

I've done 

> sudo apt-get install postfix

which downloads and starts to install it, but instead of the configuration screen similar to Ubuntu install, it opens in a terminal window and it shows the different configurations such as Internet etc.

The problem is that becuase it opens in a terminal window i can't select any option.  It just looks like a text file that i can't do anything with.

How do i install postfix with options i can choose.  Is it worth using Synaptics and if so what packages do i download?

---

### Post by jerome1232 on 2011-03-12
Actually you can, you use tab to move around choices and enter or space to select options, the very fist screen you just hit enter at the next screen allows choices. 

See Screenshot for example.

edit2: use dpkg-reconfigure postfix to get back into it's configuration

---

### Post by AdRock952 on 2011-03-12
Many thanks Jerome

It's not obvious that you would need to use tab but seeing as it looks like the installer in the beginning it looks more obvious.  Maybe people writing these instructions shouldn't take it for granted that everyone would think of these things.

I have postfix installed now but now i've come across a new problem which i'll start in a new thread

---

