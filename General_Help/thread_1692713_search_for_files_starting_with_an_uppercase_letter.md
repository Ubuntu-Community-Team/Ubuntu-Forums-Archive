---
title: "search for files starting with an uppercase letter"
date: 2011-02-21
forum: General Help
---

### Post by d!srupt!on on 2011-02-21
I am trying to sort some files in the terminal and I cannot figure out how to do a search for files starting with an uppercase letter. Been reading documentation and searching the web for a hours now. Maybe I missed something...

---

### Post by Habitual on 2011-02-21
```
find -name '[A-Z]*'
```

---

### Post by sisco311 on 2011-02-21
Is this your homework?

---

### Post by d!srupt!on on 2011-02-21
and if i want to then move those files to a certain directory I tried adding on -exec mv /home.../destination but it said missing argument

this isn't homework for a class, I'm trying to teach myself to use Linux and programming. Pretty much just started >.<

---

### Post by Habitual on 2011-02-21
some useful links/whatnot:
[http://www.unix.com/shell-programming-scripting/](http://www.unix.com/shell-programming-scripting/)
and
[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)

---

### Post by sisco311 on 2011-02-21
> **d!srupt!on said:**
> and if i want to then move those files to a certain directory I tried adding on -exec mv /home.../destination but it said missing argument

this isn't homework for a class, I'm trying to teach myself to use Linux and programming. Pretty much just started >.<

If you want to learn bash scripting, then start here:

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
[http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)


> **Habitual said:**
> 
[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)


[s]Oh, boy![/s] The bash guides at tldp.org are terrible guides for learning scripting. They teach you to write bugs, not scripts.

---

### Post by d!srupt!on on 2011-02-22
Alright, I'll check those sites out too. I'm goin through Garrels: Introduction to Linux right now.

if any one could just tell me the right syntax to finish off the command that would be stellar. I'll check back in the morning and switch this thread to [solved]

---

### Post by aeiah on 2011-02-22
```
find -name '[A-Z]*' -exec mv {} ~/path/to/destination/{} \;
```

this'll move things from your current directory to the new one if they start with an upper case letter.

---

### Post by d!srupt!on on 2011-02-22
Thank you all for your help :)

this thread is solved.

---

