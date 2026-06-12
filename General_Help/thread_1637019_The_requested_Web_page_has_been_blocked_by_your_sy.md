---
title: "The requested Web page has been blocked by your system administrator"
date: 2010-12-03
forum: General Help
---

### Post by gyre007 on 2010-12-03
Hi,
I have a question. Today something really unexpected happened to me on my ubuntu laptop - not sure if it is the new update OR if it is something I have installed recently on it but suddenly I can't access any sites that have the words sex and porn in URL...which is pretty strange because from my other laptop on which I'm running fedora and which is attached to the same network everything works just fine. it looks like I must've installed some URL checker accidentally or it's been installed along with some other package without letting me know...not really sure. First I thought that the ISP has put some URL checker but after I tcpdump-ed the traffic on port 80 it's clear that the following response is coming from my own IP:

The requested Web page has been blocked by your system administrator.

Please contact your system administrator for further information.

So I tested couple of URLs on my Fedora box and found out everything is all right there....
Does anyone have a clue what could it be ?
The traffic must be being intercepted some proxy running on my laptop or something but I haven't found anything....maybe it's the browser settings which I didn't really change - at least I don't remember. Im getting the same result in both Chrome and Firefox ...
Anyone ideas ?
Cheers

---

### Post by gyre007 on 2010-12-03
I just found out that even the URLs that contain the word "game" are blocked....this sure is strange...I have no webcontrol package installed or anything...hmm

---

### Post by stinkeye on 2010-12-04
Have a look in the history section of software centre for clues.

---

### Post by gyre007 on 2010-12-04
nah I uninstalled all stuff from past month didn't help...
I must be missing out something...not sure what though...
OS reinstall is the clear choice unfortunately....

---

### Post by DeMus on 2010-12-04
> **gyre007 said:**
>  I can't access any sites that have the words sex and porn in URL

That'll teach you!!! :P

---

### Post by mmsmc on 2010-12-04
i dont think its anything you installed, from my professional stand point i believe your computer is telling you to get a girlfreind/boyfriend

---

### Post by gyre007 on 2010-12-04
Haha...both very helpful...
1st of all I have a girlfriend...
second of all...the problem doesn't appear only with the adult sites...also ANY site that has sex - and good to know funny guys that behind sex you actually seeing some pervy stuff - it could be just about anything  like sex clinic urology etc...
But the worst is I can't check any livescore results because when I want to display the result "game" word is in URL and it is blocked as well...
mystery

---

### Post by DeMus on 2010-12-04
> **gyre007 said:**
> Haha...both very helpful...
1st of all I have a girlfriend...
second of all...the problem doesn't appear only with the adult sites...also ANY site that has sex - and good to know funny guys that behind sex you actually seeing some pervy stuff - it could be just about anything  like sex clinic urology etc...
But the worst is I can't check any livescore results because when I want to display the result "game" word is in URL and it is blocked as well...
mystery

When you did not do it yourself, in the router or modem, or maybe in the used OS, then it could be your ISP who is blocking it. Is it your home connection or from where do you try to get to the internet?
Sorry for the first answer, could not resist it.

---

### Post by jplo on 2010-12-04
Have you checked the dialogue box at System > Preferences > Network Proxy?

---

### Post by gyre007 on 2010-12-04
> **DeMus said:**
> When you did not do it yourself, in the router or modem, or maybe in the used OS, then it could be your ISP who is blocking it. Is it your home connection or from where do you try to get to the internet?
Sorry for the first answer, could not resist it.

no worries...as I said in my original post - i'm running fedora on another box....it's connected to the exact same network, same DHCP server that is giving same DNS server IP as the one I'm getting on ubuntu box....I'll give it another day and then reinstall to Fedora and sticking to Fedora...this is just nonsense :)
I'm running few perl scripts using www-mechanize module that are gathering the goal scorers of soccer games....but with this problem Im only getting that stupid blocking statement which is pretty frustrating

---

### Post by DeMus on 2010-12-04
> **gyre007 said:**
> no worries...as I said in my original post - i'm running fedora on another box....it's connected to the exact same network, same DHCP server that is giving same DNS server IP as the one I'm getting on ubuntu box....I'll give it another day and then reinstall to Fedora and sticking to Fedora...this is just nonsense :)
I'm running few perl scripts using www-mechanize module that are gathering the goal scorers of soccer games....but with this problem Im only getting that stupid blocking statement which is pretty frustrating

You do realize it is not something which is in Ubuntu by default. Somewhere is a file which contains this information and it is put there either by you yourself, or you did run some kind of program which did it for you. 
As gerbilschool wrote did you check your proxy settings?
Don't give up on Ubuntu just yet, try to find the reason why you have this problem. Give it time.

---

### Post by gyre007 on 2010-12-04
> **DeMus said:**
> You do realize it is not something which is in Ubuntu by default. Somewhere is a file which contains this information and it is put there either by you yourself, or you did run some kind of program which did it for you. 
As gerbilschool wrote did you check your proxy settings?
Don't give up on Ubuntu just yet, try to find the reason why you have this problem. Give it time.

ok I GOT IT
I turned on MALWARE PROTECTION in Chrome couple of days ago and forgot to turn it off...now i turned it back off and my scripts started workng ! I checked the browser as well and everything ok there too!
BUT CAN THE GOOGLE ENGINEERS EXPLAIN ME WHY CHANGING THIS PARAMETER IN CHROME AFFECT THE BROWSING IN FIREFOX AS WELL ?????????????????????????????????????????
I'm so p***** off!!!!!!
Thanks everyone for help
cheers

---

### Post by jplo on 2010-12-04
If the problem has been solved, please mark the thread as closed/solved.

---

### Post by DeMus on 2010-12-04
> **gyre007 said:**
> ok I GOT IT
I turned on MALWARE PROTECTION in Chrome couple of days ago and forgot to turn it off...now i turned it back off and my scripts started workng ! I checked the browser as well and everything ok there too!
BUT CAN THE GOOGLE ENGINEERS EXPLAIN ME WHY CHANGING THIS PARAMETER IN CHROME AFFECT THE BROWSING IN FIREFOX AS WELL ?????????????????????????????????????????
I'm so p***** off!!!!!!
Thanks everyone for help
cheers

Can't answer that question but am happy it works now. Now it's working get away from the computer and join your girlfriend. :P

---

### Post by arvevans on 2010-12-04
In Firefox, look in Edit-->Preferences-->Advanced to see if you have been switched to a proxy that accesses the Internet via your Chromium Mal-ware blocker.  You may have got this from one of the .xxx sites that you visited.

---

