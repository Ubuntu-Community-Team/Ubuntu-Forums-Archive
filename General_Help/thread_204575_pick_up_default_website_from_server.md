---
title: "pick up default website from server"
date: 2006-06-27
forum: General Help
---

### Post by oly on 2006-06-27
is it possible to make ubuntu pick up a default website from a central server currently our windows machines do this so was curious if you could make ubuntu do the same. ??

---

### Post by Maggot on 2006-06-27
What exactly do you mean by "pick up a default website" ? What are you looking to do?

---

### Post by oly on 2006-06-28
basically when we connect a computer to the windows 2000 network it also picks up a website which has been specified on the server, i would like to know if similar behaviour is possible with linux.

so that as we add computers they pick up the schools website automatically instead of have to set it on each computer

---

### Post by mozetti on 2006-06-28
I'll take a stab at what might be going on in the Windows world, and give a little insight on how to do it in Linux/Ubuntu.

1) The browser homepage may be set using a logon script, so every time someone logs in it sets the homepage to the school's website. 

~or~

2)Win2000 is installed as an image on each computer -- Install and set it up on one computer, then make an image of it installation and copy it to all other computers.

Either way, the way you could do it in Linux/Ubuntu is to make a script to set the broswer homepage during boot/logon. Unfortunately, that's as far as I can get you, since I'm a new Linux user. But, someone should be able to expand on this and get you going in the right direction.

---

### Post by lamego on 2006-06-28
Yes it could be easily done using a script and it wouldn't need to be based on the login, it could apply the home page change as an event from a new network connection, based on the IP address you could select the page to setup.
To implement this you will need some shell scripting skills and find how to call a script during a network up event. I believe there are some ifup/down scripts somewhere at /etc .

---

### Post by oly on 2006-06-29
okay this would require installing a script on each computer and in the windows world u change the address on server and it copies it to the clients  :p

but thanlks for suggestions

---

