---
title: "java not working in firefox"
date: 2009-09-30
forum: General Help
---

### Post by rhythmiccycle on 2009-09-30
i can't view certain java applets on my laptop, running ubuntu 9. I'm running the same os on my other computer and it works find.

specifically i want to be able to view the applets on this page:
[http://maliszesky.dyndns.org/Classes/Geo/javaExample.php](http://maliszesky.dyndns.org/Classes/Geo/javaExample.php)

i have java installed (see screen shot)

maybe the problem with the plug-in that Firefox is using.

how do i fix this?
OR how do i change the java plugin that firefox uses?

---

### Post by hwttdz on 2009-09-30
First the link you posted doesn't work.  

Second, I might go for removing your java's then deleting the ~/.icedteaplugin dir. Then reinstalling and trying again.  I personally have the sun java installed, critically the sun-java6-plugin.

---

### Post by rhythmiccycle on 2009-09-30
i fixed the link

---

### Post by hwttdz on 2009-09-30
So it loaded for me, but caused some crazy errors along the way.  I thought my entire computer had hung.  Like I said I'm using the sun java 6 and I removed .icedtea* from ~

---

### Post by rhythmiccycle on 2009-09-30
its working now, thanks alot.

the page is from my own website.

what kind of errors are you getting??

after i redid the java like you said, i don't see any errors

---

### Post by hwttdz on 2009-09-30
It wrecked the X-server somehow, or so it seems.  Here's a screen capture, wasn't able to get terminal output.  I'm using some unusual software, so it could be that, but the errors on that website were reproducible.  So they may only occur in some hardware/software/combinations but it's certainly bizzarre for me.  Of course last time I waited a few minutes and things seemed to settle, this time I just rebooted (restarting x was not sufficient).  

[IMG]http://phoenix2.ath.cx/img/Screenshot.png[/IMG]

---

### Post by rhythmiccycle on 2009-09-30
sorry for crashing your computer. 

the page just has a hand full of java applets, that create images.
php makes random numbers that go into the applet, that adds variations to the images.

they are posted with <applet> tags,

and I made the applets in processing 1.0

I don't want my site to mess up people's computers.

Do you think I should change any thing????

I can show you the code if you want.

---

### Post by hwttdz on 2009-09-30
On the one hand it's the responsibility of firefox to not allow an applet to mess up anything outside of the applet itself.  So it's a bit of a failure there.  And in fact in order to get the behavior I see it seems that a few things need to go wrong, the worst you should be able to do by writing bad code is nothing (unless you're maliciously exploiting security flaws like buffer overflows).  

On the other hand it's always good practice to test your code on multiple different setups.  So here's one where it's not much of a success.  I would recommend trying a few different browsers, possibly a virtual machine or even a few different os's.

---

