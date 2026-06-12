---
title: "acidently made something a repository ...how do I undo it?"
date: 2010-11-29
forum: General Help
---

### Post by Adrienk on 2010-11-29
I accidently made the "home" folder a repository thinking that it would make me a folder for my repository, now everything has a "+" sign on it, how do I unmake something a repository?

this was using the tortioushg tool for ubuntu.

---

### Post by Adrienk on 2010-11-29
bump

---

### Post by Adrienk on 2010-11-29
bump

---

### Post by Adrienk on 2010-11-29
Some one has to know the answer....I mean if you make a repository can you not just go backwards? I tried uninstalling and re-installing but it remebered the repository i had

---

### Post by WorMzy on 2010-11-29
Never heard of the "tortioushg" package, and I can't find it mentioned as a application in any of the packages listed in the default repositories. All I can suggest is checking the map page/help files that the application came with (if any), and checking the website you downloaded it from for a tutorial or something.

---

### Post by Adrienk on 2010-11-29
also why is it taking for ever to push a single file to the online repository?

plus if i take the link I gave it to push it to the repository its all like hi I see this link, but using the tortuous tool to push its like


```
http authorization required
realm: Bitbucket.org HTTP
user: Adrienk
pushing to https://Adrienk@bitbucket.org/Adrienk/java-source-code
searching for changes
HTTP Error 504: Gateway Time-out

[command interrupted]
```


> **WorMzy said:**
> Never heard of the "tortioushg" package, and I  can't find it mentioned as a application in any of the packages listed  in the default repositories. All I can suggest is checking the map  page/help files that the application came with (if any), and checking  the website you downloaded it from for a tutorial or something.

Its because its a PPA and you can find the site [http://tortoisehg.bitbucket.org/](http://tortoisehg.bitbucket.org/), its basically SVN with a gui.

my issue is I accidentally made the home folder a repository...meaning that everything "is ready to be pushed or commited" and I need to know in the world of SVN how to go backwards from that.

---

### Post by nolag on 2010-11-29
> **Adrienk said:**
> I accidently made the "home" folder a repository thinking that it would make me a folder for my repository, now everything has a "+" sign on it, how do I unmake something a repository?
 
this was using the tortioushg tool for ubuntu.
 
View hidden files.  There is a .svn or svn (can't remember what exactly it was named) you need to delete that.  You willl likely need to sudo or be root.

---

