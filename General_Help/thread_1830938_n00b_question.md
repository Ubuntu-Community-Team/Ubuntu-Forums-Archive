---
title: "n00b question"
date: 2011-08-22
forum: General Help
---

### Post by reco1l on 2011-08-22
Hi there, I have been using Ubuntu without a problem for a while now I run it on my TV/Film server around the house.
 
Now my question is I have a folder that was shared on the server that I cant delete I try from the main share using a windows box it says I need permission from the server, I try to delete it from the server it says I need permission from the folder owner.
 
But when I right click goto permission it tells me that "nobody" onws the folder, so how do I delete the folder??

---

### Post by Script Warlock on 2011-08-22
thats impossible folders with no owners? who created that in the first place?, just kidding.. you can try it using gksudo nautilus and search for that particular folder and delete...

---

### Post by allwimb on 2011-08-22
did you tried to use the command line with sudo to get the admin previleges ?

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by asomad on 2011-08-22
I wish I knew more about file ownership and permissions in Ubuntu, it's one of the primary things to learn on my list...

But I would think, you could (in a terminal, of course)

1. add your log in account as an owner to the folder
2. then you should be free to delete it on your server

or
1. add ownership and permissions to the folder for anyone and everyone
2. then you could delete it from your windows box...

Now, I just need someone to translate the above steps into some simple code. LOL
Sorry I cant be of more help

---

### Post by reco1l on 2011-08-28
gksudo nautilus

that worked thanks

---

