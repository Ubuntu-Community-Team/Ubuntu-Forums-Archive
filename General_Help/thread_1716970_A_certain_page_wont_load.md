---
title: "A certain page wont load"
date: 2011-03-29
forum: General Help
---

### Post by blabla1 on 2011-03-29
It's very weird because i just tried opening facebook in firefox on windows and it works fine. On Firefox in ubuntu on the other hand the connection resets while the page is loading every time. 
I think my laptop/browser is blocking the connection to facebook but since I'm new to ubuntu i don't really know how to solve this.

edit: I tried opening it through [http://www.adminsucks.com/](http://www.adminsucks.com/) and it works...



Any help would be appreciated.

Thanks in advance

---

### Post by blabla1 on 2011-03-29
bump?

---

### Post by An Sanct on 2011-03-29
Have you tried the [prism plugin for facebook]("http://ubuntu.igameilive.com/2009/03/facebook-and-ubuntu.html")?

PS. I know, this doesn't solve the original problem...

---

### Post by blabla1 on 2011-03-29
Thank you. Finally a reply :P
But like you said this doesn't solve the original problem...

---

### Post by mendhak on 2011-03-29
Are you at home, work, uni, library...?
Do you know if you're behind a proxy? 

Are other sites working?
What about other sites over HTTPS (try logging in to Live Mail or GMail)?

---

### Post by blabla1 on 2011-03-29
> **mendhak said:**
> Are you at home, work, uni, library...?
Do you know if you're behind a proxy? 

Are other sites working?
What about other sites over HTTPS (try logging in to Live Mail or GMail)?


I'm at home, no proxy and HTTPS sites and other sites work fine.

---

### Post by blabla1 on 2011-03-29
Bump again : /

---

### Post by prat22 on 2011-03-29
Hi! 
I have also experienced the same many years ago! I figured out that certain hardware with certain connections and OS blocks certain sites. And then I tried by changing the MTU in your connection settings, to anything. It worked for me, and worth a try!

---

### Post by blabla1 on 2011-03-29
> **prat22 said:**
> Hi! 
I have also experienced the same many years ago! I figured out that certain hardware with certain connections and OS blocks certain sites. And then I tried by changing the MTU in your connection settings, to anything. It worked for me, and worth a try!


I tried that as well, still nothing. The thing is, everything was fine yesterday. This suddenly happened.

---

### Post by PoHandle on 2011-03-29
I had trouble accessing Facebook using Firefox in the past.  The solution for me was to type the full address in the title bar.```
http[COLOR="Red"]s[/COLOR]://[COLOR="red"]www[/COLOR].facebook.com
```
I don't have this problem anymore, but then again, I'm using Firefox4 and Chromium.

If that solution doesn't work for you, you may want to reset (power off for 30 seconds) your router, or even clear your browsing cache and cookies.

---

### Post by blabla1 on 2011-03-29
> **PoHandle said:**
> I had trouble accessing Facebook using Firefox in the past.  The solution for me was to type the full address in the title bar.```
http[COLOR=Red]s[/COLOR]://[COLOR=red]www[/COLOR].facebook.com
```I don't have this problem anymore, but then again, I'm using Firefox4 and Chromium.

If that solution doesn't work for you, you may want to reset (power off for 30 seconds) your router, or even clear your browsing cache and cookies.


:o Finally! This works! 
Thank you very much :) 

Any idea why this didn't happen before ? I mean i didn't have to make it https to make it run before.

---

### Post by PoHandle on 2011-03-29
I'm not sure what brought about this change, but I would guess that an update may have caused this.  The problem seems to be an issue with the domain name not being able to be resolved for some reason or another.  You may want to clear your DNS cache, or use another DNS altogether.  I use the Google Public DNS (8.8.8.8 or 8.8.4.4)

---

