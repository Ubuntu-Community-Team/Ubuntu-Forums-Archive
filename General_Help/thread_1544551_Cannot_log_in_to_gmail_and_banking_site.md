---
title: "Cannot log in to gmail and banking site"
date: 2010-08-02
forum: General Help
---

### Post by tas.b on 2010-08-02
Hello,
I have trouble logging in to some pages: gmail and [www.alpha.gr]("http://www.alpha.gr"). After entering username & password the browser is continuously loading but there is no network activity and the page won't load.
I am running 64bit Lucid and have this problem with the latest versions Firefox, Chromium and Opera.
There is no problem with Windows XP installed on the same machine. This is not the solution I want to follow however.
Everything was fine about a month ago...
Any ideas what I could try?

---

### Post by dv3500ea on 2010-08-02
It looks like you are having problems connecting to https websites.
I assume most websites work fine.
I'm not sure how to solve this issue but https appears to be the problem.

---

### Post by dv3500ea on 2010-08-03
There is a thread here with similar issues:
[http://ubuntuforums.org/showthread.php?t=1543458]("http://ubuntuforums.org/showthread.php?t=1543458")

---

### Post by tas.b on 2010-08-03
Thanks, it looks like similar problems although i can log into ebay but not into gmail or launchpad.

---

### Post by Krabby.Linux on 2010-08-03
Same for you :


>  Thats hard to say, could be your hardware, you will have to test the  connection with a new network card i think. I know some people who had  this Problem or still having this under Windows AND Ubuntu, thats the  strange thing.

Are you able to test the connection with a new card?

What about Firefox settings ? Is SSL 3.0 checked? What about TSL? If TSL is checked try to turn it off and restart your browser.


Another Idea: Do you use a proxy? First check Firefox Proxy and mark use  system proxy. Than go to System --> preferances --> network proxy  and disable eveything (mark direct connection) than push the button  apply system wide and type in your su password twice. What about now? 

---

### Post by tas.b on 2010-08-04
I have checked with a different card: 
(a) my normal connection (is with a wireless Belkin card ) 
(b) wired connection with the onboard LAN
both (a) and (b) had the same issue.
in Firefox SSL 3.0 is checked and I tested with and without TSL, still nothing.
I don't use any proxy, I checked firefox and system settings just in case.
I started the recent Puppy linux 5.0.1 from a USB drive and the same problem both with wired and wireless.
I started Ubuntu from the Live CD with a wired connection and still had the problem.
I also checked the same Ubuntu Live CD on different computer (laptop - wireless) and had the same problem. 
I suppose it must be a setting on the router Linksys WAG200G ?

---

### Post by tas.b on 2010-09-15
Finally this was fixed after resetting the router. Rebooting the router was not correcting the problem.

---

