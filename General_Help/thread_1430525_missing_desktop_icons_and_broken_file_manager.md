---
title: "missing desktop icons and broken file manager"
date: 2010-03-15
forum: General Help
---

### Post by greggy.gregory on 2010-03-15
i am reposting this in this section of the forum as my problem was not solved when i posted it elsewhere, if you want to see the original post to see what suggestion were made it can be found here [http://ubuntuforums.org/showthread.php?t=1406005](http://ubuntuforums.org/showthread.php?t=1406005)

i am pretty new  to linux and have only been using it for a couple weeks now. i  installed Picasa from google just now and since then my desktop icons  have disapeared and if i open the file manager it closes within 5  seconds. i have tried rebooting the computer and have now completly  removed picasa and the problem is still there.
any ideas what the problem might be and how i can fix it?

---

### Post by nitstorm on 2010-03-15
> **Re: compiz water effect making system unable to use** 			 			 			 		   		 		 		 	Code:
 	sudo aptitude search compiz | grep "i " 
Uninstall all the programs you see there with 
 	Code:
 	sudo aptitude remove compiz compiz-core [...rest of programs...] 
You can also use synaptic, which is a graphical program and easier to use but I figured that you wouldn't be able to use it if it turns your screen black.


This is what I had for a reply wen compiz water effect made my system crazy

why not try the same thing with picasa?
Ex:

```
 
sudo aptitude search picasa | grep "i"

```
and then remove the files that get listed using
```

sudo aptitude remove picasa-whatever-whatever-that-comes-up

```

Not sure if it might solve ur problem, kinda a newbie myself :) 
But if it was Picasa that messed ur sys, then this shall remove every trail of picasa off ur sys and theoretically will make it work :)

---

### Post by greggy.gregory on 2010-03-15
> **nitstorm said:**
> This is what I had for a reply wen compiz water effect made my system crazy

why not try the same thing with picasa?
Ex:

```
 
sudo aptitude search picasa | grep "i"

```and then remove the files that get listed using
```

sudo aptitude remove picasa-whatever-whatever-that-comes-up

```Not sure if it might solve ur problem, kinda a newbie myself :) 
But if it was Picasa that messed ur sys, then this shall remove every trail of picasa off ur sys and theoretically will make it work :)

ok thnx, will try this when i get back from my dinner

---

### Post by nitstorm on 2010-03-15
keep us updated buddy :)

---

### Post by greggy.gregory on 2010-03-16
> **nitstorm said:**
> keep us updated buddy :)

well im not entirely sure how but me not using my linux system for weeks because of this problem seems to have fixed it. i just logged in and the file manager seems to work fine as does the desktop. 

i did as you suggested anyway, and it looked like it was already completly gone.

one problem i still have that i forgot to mention in my first post is that i enabled the "automaticly remember running applications when logging out" option and even tho i then disabled the option, it always starts up firefox and skype now, even if i close them before logging out. i dont know if this is related or not, but hopefully someone will know the reason.

---

