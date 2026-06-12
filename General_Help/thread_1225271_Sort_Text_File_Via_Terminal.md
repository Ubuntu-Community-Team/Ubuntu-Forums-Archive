---
title: "Sort Text File Via Terminal"
date: 2009-07-28
forum: General Help
---

### Post by Chamillionaire2 on 2009-07-28
What's Up?

OK, So with My new project, I need to be able to sort thourgh a text file for links, the only probley is the links are going to be diffrent each time, is their a way i could sort just the links to a new file or delete everything in the file that isent a link?

Thanks Bye.

---

### Post by DaithiF on 2009-07-28
Hi,
almost certainly, yes.  can you post a sample of the file?

---

### Post by Idefix82 on 2009-07-28
> **Chamillionaire2 said:**
> What's Up?

OK, So with My new project, I need to be able to sort thourgh a text file for links, the only probley is the links are going to be diffrent each time, is their a way i could sort just the links to a new file or delete everything in the file that isent a link?

Thanks Bye.

How are you going to recognise the links? What format is the text file? Do you just want to look for everything that starts with www or is there any html markup in the file?

---

### Post by Chamillionaire2 on 2009-07-28
Heres a example
```
http://cira.login.cqr.ssl.seasons/.ssl 	tperreault
763430 	http://www.heathdesktop.iceryder.net/
763429 	http://122.19.73.24/paypal/
763428 	http://www.jogando.net/mu/season4/
763427 	http://www.buyrealestateat.com/js/index.php
```

It would have to find the links, which start with [http://www](http://www). and either copy them to a new file or delete everything other then a link im not too fussed so long as the end result is everything has been sorted.

the real text files it would have to sort mite be alot bigger though.

Thanks for your replys.

---

### Post by kotnik on 2009-07-28
You can extract all URLs using Perl and a bit of regexp:

[http://codesnippets.joyent.com/posts/show/523](http://codesnippets.joyent.com/posts/show/523)

---

### Post by Chamillionaire2 on 2009-07-28
> **kotnik said:**
> You can extract all URLs using Perl and a bit of regexp:

[http://codesnippets.joyent.com/posts/show/523](http://codesnippets.joyent.com/posts/show/523)

Perl? Ive heard about that language but never learnt it, how would i go about running that script?

---

### Post by Slim Odds on 2009-07-28
grep and sort would work just fine also. no need for perl

---

### Post by DaithiF on 2009-07-28
something like
```
grep "http://" <filename> | sed 's/^.*http:/http:/' | sed 's/\s.*$//' | sort 
```
for a quick and dirty solution

add > somefilename at the end to save results to a new file

---

### Post by Chamillionaire2 on 2009-07-28
> **DaithiF said:**
> something like
```
grep "http://" <filename> | sed 's/^.*http:/http:/' | sed 's/\s.*$//' | sort 
```
for a quick and dirty solution

add > somefilename at the end to save results to a new file

Brilliant! Just what I was looking for, Works perfectly.

You must be some sort of terminal Wizard!

---

### Post by Slim Odds on 2009-07-28
> **Chamillionaire2 said:**
> Brilliant! Just what I was looking for, Works perfectly.

You must be some sort of terminal Wizard!

You just need to learn some of the simple *nix command line tools (grep, sed, sort, cut and of course bash).

Once you learn to put them together you'd be amazed at what you can do.

---

