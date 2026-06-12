---
title: "open file apps"
date: 2009-11-15
forum: General Help
---

### Post by theblade180 on 2009-11-15
whenever i try to download a file in ubuntu, i can never open/install the file because when i click or right click, and click open with... the open with... window has no applications to open the file with!!! how the hell am i supposed to use the f***ing retarded computer if i cant install sh*t!!!

---

### Post by arnab_das on 2009-11-15
type the following from the terminal:

sudo apt-get install ubuntu-restricted-extras

or if u dont want to use the command line interface, use the pictorial guide here to install ubuntu restricted extras.

[http://thoughtsndreams.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/](http://thoughtsndreams.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/)

see if it changes anything.

---

### Post by theblade180 on 2009-11-15
where&#347; the terminal?

---

### Post by arnab_das on 2009-11-15
> **theblade180 said:**
> where&#347; the terminal?

follow the link.

[http://thoughtsndreams.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/](http://thoughtsndreams.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/)

use the second method

---

### Post by sisco311 on 2009-11-15
Edit: 

You can use Add/Remove... or in 9.10 Ubuntu Software Center and Synaptic Package Manager to install applications:

[http://psychocats.net/ubuntu/installingsoftware]("http://psychocats.net/ubuntu/installingsoftware")

What exactly are you trying to install?

---

### Post by tsymnz on 2009-11-15
I'm trying to install 'transmageddon' video converter and I see a few normal files but nothing I've tried works.

/home/tony/Desktop/transmageddon-0.15/Makefile.am
/home/tony/Desktop/transmageddon-0.15/Makefile.in
/home/tony/Desktop/transmageddon-0.15/install-sh

---

### Post by delgan999 on 2009-11-27
I managed to get this install but with an error that it cant find glib module on running.

heres what I did

in a terminal, cd to the directory you extracted it to

type all that is bold

**./configure**

(stuff whizzes by)

**./make**

(more stuff)

**sudo make install**

It was the configure first that I was getting caught up on for ages

hope this helps

---

