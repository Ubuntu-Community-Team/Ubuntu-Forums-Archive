---
title: "hi am trying to down load cario dock from there web site"
date: 2009-11-17
forum: General Help
---

### Post by blake7 on 2009-11-17
but im having no luck

can you give me a step by step on how to do it

thank you

---

### Post by fluffman86 on 2009-11-17
You don't need to get it from their web site.  Instead, use the Ubuntu repositories, which will keep it up to date with the latest bug fixes.  Also, it's *much* easier to install.  Go to Applications > Accessories > Terminal, and type:

sudo apt-get install cairo-dock

You can also search for it in System > Administration > Synaptic, which is the same thing...the command line is just easier. :)

If the command above doesn't work, go to System > Administration > Software Sources, and make sure the top four checkboxes are checked.  Then close software sources, click "Reload" and run the command above again.

Edit: and if you really just want to compile it and get the latest goodies from berlios, then check out [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by Giblet5 on 2009-11-17
Open a terminal window. Enter ```
sudo apt-get install cairodock
```

---

### Post by blake7 on 2009-11-17
i thiought that if i did from the site then it would give me the lastest version the last on  i did keeped freezing so i was hopeing to get other that problem 


cheers

---

### Post by Giblet5 on 2009-11-17
Yes, but you will probably have to build it yourself. Are you proficient in C++?

If not, stick to the repos.

The latest IS the bleeding edge. Do you know why that term is common? Do you remember the last time you were bleeding? ;)

If you were proficient in C and C++, you wouldn't have posted this question. That's why I recommended the repo version.

---

### Post by blake7 on 2009-11-17
yea your not really bleeding edge if you where you would not be so bleeding annoying
its to easy just to be good at one thing like your self thoe congrats for the one thing you are good at


later

 Re: hi am trying to down load cario dock from there web site
Yes, but you will probably have to build it yourself. Are you proficient in C++?

If not, stick to the repos.

The latest IS the bleeding edge. Do you know why that term is common? Do you remember the last time you were bleeding?

If you were proficient in C and C++, you wouldn't have posted this question. That's why I recommended the repo version.
__________________
s&#305; &#623;&#477;1qo&#633;d &#633;no&#654; &#647;&#592;&#613;&#653; &#477;&#477;s &#305; &#670;u&#305;&#613;&#647; &#305;

---

### Post by Giblet5 on 2009-11-17
> **blake7 said:**
> yea your not really bleeding edge if you where you would not be so bleeding annoying
its to easy just to be good at one thing like your self thoe congrats for the one thing you are good at

Uh huh. Whaaaargarbl! to you, too. :)

---

