---
title: "Scripting Prob :-("
date: 2009-08-12
forum: General Help
---

### Post by Chamillionaire2 on 2009-08-12
What's Up?

OK, Getting straight down to brass tacks here. Is their a way via terminal you could search the given file for links, and delete everything that was returned as a link?

Thanks Bye.

---

### Post by Chamillionaire2 on 2009-08-12
[img]http://tbn0.google.com/images?q=tbn:56Pc7HNg54-uoM:http://www.lhcrt.org.uk/fabrics/plain_white.jpg[/img]

---

### Post by Chamillionaire2 on 2009-08-12
[img]http://tbn0.google.com/images?q=tbn:56Pc7HNg54-uoM:http://www.lhcrt.org.uk/fabrics/plain_white.jpg[/img]

---

### Post by P4man on 2009-08-12
You can bump it till kingdom comes, but perhaps you can instead try and rephrase the question, because I have no idea what you're asking ?

The link you gave doesnt work (even if I copy/paste it entirely) but I got no idea if that was part of your point, or a mistake :confused:

---

### Post by Chamillionaire2 on 2009-08-12
> **P4man said:**
> You can bump it till kingdom comes, but perhaps you can instead try and rephrase the question, because I have no idea what you're asking ?

The link you gave doesnt work (even if I copy/paste it entirely) but I got no idea if that was part of your point, or a mistake :confused:

The link isent a real one, i used it as an _Example_ Ill try rephrase it the best i can.

---

### Post by Slim Odds on 2009-08-12
Hourly bumping is extremely rude.

And the answer is yes, there is a way to do it.

---

### Post by Chamillionaire2 on 2009-08-12
> **Slim Odds said:**
> Hourly bumping is extremely rude.

And the answer is yes, there is a way to do it.

I thought so, using awk or grep i should imagine.

---

### Post by arsenic23 on 2009-08-12
Well assuming all of the links start with 'http://' :

```
sed -e 's|http://[^ ][^ ]*||g' filename > newfilewithnolinks
```

[COLOR="Gray"]Also it is better to have a post with no replys then when filled with bumps.  Some people actually go through and try and look at posts with zero replies.[/COLOR]

---

