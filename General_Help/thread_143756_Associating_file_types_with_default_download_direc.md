---
title: "Associating file types with default download directories (did that make sense?)"
date: 2006-03-13
forum: General Help
---

### Post by TeeAhr1 on 2006-03-13
Basically, what I mean is: When I download a file, the default save directory is whatever directory I last downloaded a file to, which often isn't where I want to be.  I realize I'm three clicks away, but I am profoundly lazy.  Is there a way to tell the save dialogue to come up with, for instance:

**/home/me/** when I download a .deb
**/media/datadrive/comics/** if it's a .cbx
**/media/datadrive/images/** if it's a .jpg or .png

et cetera?  I apologize if this question seems nonsensical, I don't really understand how this works at all.  I don't even know if it's Nautilus or Firefox that 'decides' that.  Thx in advance for anyone who can give me a little insight on this...

-p.

---

### Post by meborc on 2006-03-13
i guess it is decided by firefox... it sends all the files to some default folder... i don't know if it is _safe_ to go messing around firefox, but i think you could make a workaround by making a small nautilus script...

the script should check your /home/download folder and then move all *jpg files to /home/me/pictures and *cbx to /home/me/comics etc... i guess i'm way too lazy for knowing anything about scripting for nautilus, but i have seen some of the similar things done... and i would be very interested in this specfic script :D 

i guess if you are up to it, you can check this: [https://wiki.ubuntu.com/NautilusScriptsHowto](https://wiki.ubuntu.com/NautilusScriptsHowto)

ps - it would be so nice if it turned out that firefox can be modified though :rolleyes:

---

