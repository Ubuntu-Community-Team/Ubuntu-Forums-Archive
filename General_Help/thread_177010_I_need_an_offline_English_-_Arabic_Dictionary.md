---
title: "I need an offline English - Arabic Dictionary"
date: 2006-05-15
forum: General Help
---

### Post by Isoss on 2006-05-15
I've installed dictd ... but it's not working! niether using terminal nor can I find an application icon for it!

Can you please help! I need this program so badly ... I need something offline like Sakher or GoldenWafi which only work under windows. I tried to install those with wine but unfortunately they didn't work.

Any help will be so much appriciated.

Thank you
Isos

---

### Post by matthew on 2006-05-15
I would be very interested in this as well. I'll do some looking around and see if I find anything. If I do, I'll post info or a link in a followup. 

In the meanwhile, you do have Hans Wehr's dictionary and perhaps Al Mawrid on your shelf, right? :)

---

### Post by matthew on 2006-05-15
Some things I've found.

There's a downloadable [english-arabic dictionary as an xml file here]("http://crl.nmsu.edu/Resources/lang_res/arabic.html"). I'm not sure how to use it yet and you have to register to get it, but it was easy and free to acquire.

[This is an interesting conversation]("http://lists.arabeyes.org/archives/doc/2005/December/msg00024.html")...you might have some luck. I took a quick look and didn't find all the files mentioned in the Ubuntu repos, though.

I've run across a lot for windows, lots for online use, and very little other than statements of "we're working on..." for linux. Let's look more and also see if someone else jumps in with something.

---

### Post by Isoss on 2006-05-15
Ok I need some help here ... I downloaded ktranslator. it's tar.dz
I extracted it, and 'cd' to it's directory and 'sh' ./configure to create a Makefile and then I typed make to compile the package but it gave me this:
```
make: *** No targets specified and no makefile found.  Stop.

```
So I need some help here, I am not so aquainted with installing tars and stuff like this ... hope I can get a help here and also maybe more suggestions for more offline Eng-Ara dictionary softwares.

Thanks in advance.

---

### Post by Isoss on 2006-05-16
Hellooooooooooooo ... any body there!?

---

### Post by Sef on 2006-05-16
Here's two sites that will help you to install.

[http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal]("http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal")

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

---

### Post by Isoss on 2006-05-16
No luck ... still getting the same error!

---

### Post by matthew on 2006-05-16
[quote=Isoss]No luck ... still getting the same error![/quote]Have you installed the build-essential package, etc?```
sudo apt-get update
sudo apt-get install build-essential
```All I can think of is it is either this or there is a problem with the file you downloaded--either the copy you got was corrupted or was made incorrectly.

---

### Post by Googler on 2006-05-16
did you read the INSTALL/README stuff to know the exact procedures ?

---

### Post by sondad on 2008-01-17
you can download the dict files needed for ktranslate from this form
[http://www.linuxac.org/forum/showthread.php?t=3190]("http://www.linuxac.org/forum/showthread.php?t=3190")

---

