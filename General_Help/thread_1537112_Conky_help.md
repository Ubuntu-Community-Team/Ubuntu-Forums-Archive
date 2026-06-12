---
title: "Conky help"
date: 2010-07-23
forum: General Help
---

### Post by famousforrest on 2010-07-23
I want to get a good looking conky set up on my comp. 
ran the 
sudo apt-get install conky
code but afterwards I input 

zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc

and I get

gzip: /usr/share/doc/conky/examples/conkyrc.sample.gz: No such file or directory

not sure what to do next.
thanks!

---

### Post by lion9 on 2010-07-23
Create ~/.conkyrc manually (leaving it empty) and then search in the Internet for the conky configs. Choose the one you like the most and paste it into your .conkyrc

---

### Post by tpjk on 2010-07-23
hey there,

you don't need to work with the examples that come with conky.
just create the .conkyrc file in your home folder, then head over to the following thread:

[Post your .conkyrc files with screenshots]("http://ubuntuforums.org/showthread.php?t=281865")         

... and just copy and paste the content of someone else's conkyrc into your own. you should pick something that's fairly simple, try and get an idea of how the code works and then proceed to the more advanced stuff.

---

### Post by famousforrest on 2010-07-23
Can you explain how to create the file in the /home folder?
What am I overlooking here?

Sorry for the extreme noobie ness
thanks

---

### Post by lion9 on 2010-07-23
Open terminal and enter:

gedit /home/%username%/.conkyrc

where %username% is your username.

---

### Post by famousforrest on 2010-07-23
okay so I've made the folder and pasted a simple example code in the .conkyrc folder. nothings showed up on my screen.
What next?

---

### Post by tpjk on 2010-07-23
.conkyrc needs to be a text file, not a folder :]

---

### Post by famousforrest on 2010-07-23
Clarafication: I pasted some basic code into the basic text document. ;)

---

### Post by famousforrest on 2010-07-23
Edit: just got it running. I probably had to close the window or something.
Thanks for all your help!

---

