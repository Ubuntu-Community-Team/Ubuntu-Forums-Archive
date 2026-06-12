---
title: "Can't login in kubuntu"
date: 2006-06-25
forum: General Help
---

### Post by saax on 2006-06-25
I was in kubuntu browsing over net then sudenly crashed then i restart computer.Kubuntu start ok to the session type where is need password to log in ,but when i hit enter it send me back to session menu.I try to log in failsafe ,openbox no sucess.I can only log in console mode.

WHats wrong and how can i fix this ,please help me

---

### Post by gingermark on 2006-06-25
do
```
rm /home/user/.{ICE,X}authority
``` where "user" is your username

Assuming this is the problem I think it is, then it can be avoided in the future by using "kdesu" to lauch graphical applications and sudo only for terminal commands.

eg. To edit your sources.list file the command would be ```
kdesu kate /etc/apt/sources.list
``` **NOT** ```
sudo kate /etc/apt/sources.list
```
Of course, that assumes the problem is what I think it is....

---

### Post by saax on 2006-06-25
I try your way ,but its  still not working i can only type my pass ,blink black screen and im back to session type menu  ](*,)

---

### Post by gingermark on 2006-06-25
Do you get an error message?
Did you try what I told you to in the failsafe console?

---

### Post by saax on 2006-06-25
I cant login in Failsafe only console type i try with your code no errors ,but it send me back to kubuntu session menu then i type password and old story...

---

### Post by gingermark on 2006-06-25
Ok, I just got that command off the wiki.

I'm still assuming that this is a .ICEauthority problem, but I would have thought you would have gotten an error message when you tried to login.

Try ```
sudo chown -R username : username /home/username
``` followed by ```
sudo chmod -R u+w /home/username
``` again substituting your username for every instance of 'username'.

And you can remember any error messages or have any other info then that would help :)

---

### Post by saax on 2006-06-25
I get error invalid user

---

### Post by gingermark on 2006-06-25
That is odd. Did you substitute YOUR username for every instance of "username" in the code I gave you?

I'm trying to find out if there could be another reason for your problem. Hopefully someone else will help too :)

---

### Post by saax on 2006-06-25
I give up ,I ill make reinstall i will only loose some movies and not important data.

Thx for helping me gingermark.

---

### Post by FredB on 2006-06-25
you can save a reinstall. Try booting is the restricted (or something like this) mode, by pressing ESC key on the booting shutdown. After, you can enter a text mode, and try what saax is proposing.

---

