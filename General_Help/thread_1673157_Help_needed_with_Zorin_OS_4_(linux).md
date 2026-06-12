---
title: "Help needed with Zorin OS 4 (linux)"
date: 2011-01-22
forum: General Help
---

### Post by the wolfe on 2011-01-22
I have recently installed Zorin OS 4 64 bit, which reads as Ubuntu 10.10 in the system monitor. I guess it is just 10.10 with a visual pack installed. 

Anyway, How would I go about getting the movie player to actually read a Movie DVD? Is it a plugin thats needed? Or another program?

thanks ahead of time for any help that you can provide.

---

### Post by Timmer1240 on 2011-01-22
sudo apt-get install libdvdread4 {in the terminal} Then
sudo /usr/share/doc/libdvdread4/install-css.sh {in the terminal}
rebooting may be nessesary

---

### Post by the wolfe on 2011-01-22
that worked wonders. Thanks man. 

Now next question, still having to do with this OS. 
How would I go about Enabling the HD Audio through HDMI? I know it can be done, as I used to use it in win 7.

---

### Post by Timmer1240 on 2011-01-22
you got me on that one?

---

### Post by the wolfe on 2011-01-22
I actually just figured that out after I posted that. 
Clicked on Audio, then preferences,then output. Clicked on HD4200 Digital. Worked. Its actually a very similar process to Widows 7. 

Happen to have any clue on how to use terminal to PING a website? or to trace the signal to see if there is a server down?

---

### Post by the wolfe on 2011-06-03
> **Timmer1240 said:**
> sudo apt-get install libdvdread4 {in the terminal} Then
sudo /usr/share/doc/libdvdread4/install-css.sh {in the terminal}
rebooting may be nessesary
I know this thread is dead, but this isnt working now. Is there another way to get the DVD plugins?

---

