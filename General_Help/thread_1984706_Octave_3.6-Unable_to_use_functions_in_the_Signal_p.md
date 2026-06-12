---
title: "Octave 3.6-Unable to use functions in the Signal package even after installing it"
date: 2012-05-22
forum: General Help
---

### Post by danwill on 2012-05-22
I have installed all the dependencies for the Signal package as listed in the link below :

[http://octave.sourceforge.net/signal/index.html]("http://octave.sourceforge.net/signal/index.html")

But if I use any of the functions like 'fir1' there is an error message saying that the function is undefined.What could be the possible problem?

---

### Post by Redblade20XX on 2012-05-22
Hopefully this doesn't sound bad but did you install the package? You mentioned that you've check the dependencies but you didn't say that you installed the package. Also did the dependencies install correctly?

-Red

---

### Post by danwill on 2012-05-22
I did install it and I have checked it once again too.

---

### Post by namruf15 on 2013-01-02
After installation of any packages (for example signals) you must use command [I]load.
[/I]Type *pkg load all* and you should have you problem solved.

---

