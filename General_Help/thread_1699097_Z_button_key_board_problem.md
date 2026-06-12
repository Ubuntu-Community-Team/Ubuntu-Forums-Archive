---
title: "Z button key board problem"
date: 2011-03-03
forum: General Help
---

### Post by jolian ramos on 2011-03-03
suddenly i notice that when i press Z button on keyboard i find that it doesn't write anything i thought that maybe the problem is with keyboard itself but when i logged off and log in to ROOT account i find that when i press Z button it writes  so only when i use the normal account not the Root it doesn't write or function or gives any thing 

this is sooooooooooo weird so please any idea about this or how to fix it  [SIZE=2]****[/SIZE]

---

### Post by ThaDoctor99 on 2011-03-03
What is the situation is it generally in all applications or only in a certain application ?
If it is in one application you might have a bad config for that user.

---

### Post by jolian ramos on 2011-03-03
> **ThaDoctor99 said:**
> What is the situation is it generally in all applications or only in a certain application ?
If it is in one application you might have a bad config for that user.
it is for all application in firefox and open office and as i said when i login to ROOT the Z button works and write very normal and well even in those application firefox and openoffice 
really hope to help me it seems to me that there is something different from my account and the ROOT account

---

### Post by ThaDoctor99 on 2011-03-03
Have you done anything to keyboard like mods or anything ??
Perhaps you have "killed" the z key for the user but not root.

---

### Post by jolian ramos on 2011-03-03
> **ThaDoctor99 said:**
> Have you done anything to keyboard like mods or anything ??
Perhaps you have "killed" the z key for the user but not root.
actually i don't know to kill z all what i did recently that i add more languages from system --> administration---> language supported then i added more languages and that is all 
so please tell me how to check if z button function is killed in my account or no and i will check it and tell you

---

### Post by ThaDoctor99 on 2011-03-03
System -> Administrative -> keyboard 
And there you should be able to see, however I am not on any ubuntu on my local machine and I do not run gnome. I did, but not any more, but I think it is there. then there should be a keyboard and some options like keymap (have you chosen one with dead keys ?)
That is the best I can do.

---

### Post by jolian ramos on 2011-03-03
> **ThaDoctor99 said:**
> System -> Administrative -> keyboard 
And there you should be able to see, however I am not on any ubuntu on my local machine and I do not run gnome. I did, but not any more, but I think it is there. then there should be a keyboard and some options like keymap (have you chosen one with dead keys ?)
That is the best I can do.
thank you very much for your concern sir 

any other one can help me please i am using ubuntu 10.04i have never faced something weird like this problem

---

### Post by oliwek on 2011-03-03
> **jolian ramos said:**
> thank you very much for your concern sir 

any other one can help me please i am using ubuntu 10.04i have never faced something weird like this problem

for sure, your root account has another language/keyboard layout, as compared to your user account ; check both and select what you need.

for each user layout : [http://www.wikihow.com/Change-Keyboard-Layout-in-Ubuntu](http://www.wikihow.com/Change-Keyboard-Layout-in-Ubuntu)

for the terminal (language/keyboard used in command line interface), try : 
> sudo dpkg-reconfigure console-data

---

### Post by jolian ramos on 2011-03-03
i discovered the problem it was with compiz configuration when i select to use to activate the accessibility -->opacify i used the z button it self to activate this option in compiz seeting manager and i never imagine that this will kill the function of z button in writing  when i change this matter i get the z button in writing again thank you very much for your concern again

---

