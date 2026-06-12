---
title: "Important question about synaptic. Please enter"
date: 2006-05-25
forum: General Help
---

### Post by Isoss on 2006-05-25
I have just installed a bunch of packages with synaptic. most of them where dictionaries ...  after downloading the packages, and during the installation stage, I opened the terminal of the "installation" window, I noticed that something that used to happen to me before when installing directly with apt-get which is : connect set locale modifiers! ... this happened with me before I reinstall ubuntu cuz my locale was set to English (zimbabwe). Then I fixed this by changing it to English US and it never prompted me again. Today after I reinstalled ubuntu I forgot to set the locale. 

So I am just concerned! will this corrupt something? it looks to me that all the packages were installed and everything is fine but I would that affect the packages in any how? will fixing the locale fix the problem that might have happened? and if no, do I have to uncheck all of them and reinstall them again? ... I can't really check them all to see if they work properly. I tried one of them though and it didn't really work but not sure if this is the problem.

So, I hope I can get a help ASAP ... this is a lotta time installing and still need to download a lotta stuff. so thanks in advance.

---

### Post by kingmonkey on 2006-05-25
nothing will get corrupt

To reset your local or add locals or whatever type:

sudo dpkg-reconfigure locales

---

### Post by Isoss on 2006-05-25
Thanks a lot. especially for the code it helps be more specific I guess.

---

