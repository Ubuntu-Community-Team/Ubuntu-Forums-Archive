---
title: "Hydra question"
date: 2010-08-18
forum: General Help
---

### Post by masamunedark on 2010-08-18
Hi, I am playing around with Hydra (on my own network ;)) and was wondering if it could be used without a passwords' wordlist, for example, could it maybe be used to brute force using every possible password combination ? ( It would take a huge time, i know) 
Thanks,

---

### Post by rollin on 2010-08-18
Hydra is a great tool but there are only a few machines in the world capable of testing every password combination. You'll need something like this [http://www.youtube.com/watch?v=4VTxyRVmL5c](http://www.youtube.com/watch?v=4VTxyRVmL5c) ;)

---

### Post by masamunedark on 2010-08-18
Thanks for the reply, but I am only talking here about humble unencrypted passwords consisting of a modest number of digits. :p
So by reading your answer I guess Hydra doesn't have that function ?

---

### Post by rollin on 2010-08-18
> **masamunedark said:**
> Thanks for the reply, but I am only talking here about humble unencrypted passwords consisting of a modest number of digits. :p
So by reading your answer I guess Hydra doesn't have that function ?

No problem! Good question but I don't think there is a function ( as in without a password list) to begin forcing combinations like  xxxxxyyy where x is a letter and y a numeric for example "alpha123" or just numbers and letters. If there is I don't know it, sorry! 

If your looking for scripts to generate password lists or completed password lists, try searching Backtrack and places like Packet Storm. Good luck with it either way! If you do find a way, (there are heaps of tools from THC) to define the character structure please post it ;)

---

### Post by masamunedark on 2010-08-19
Ok, I found one. This page contains a Perl script which can generate up to 8 digits possible combinations.

[http://linuxshellaccount.blogspot.com/2008/01/script-to-generate-all-possible.html](http://linuxshellaccount.blogspot.com/2008/01/script-to-generate-all-possible.html)

---

### Post by rollin on 2010-08-19
> **masamunedark said:**
> Ok, I found one. This page contains a Perl script which can generate up to 8 digits possible combinations.

[http://linuxshellaccount.blogspot.com/2008/01/script-to-generate-all-possible.html](http://linuxshellaccount.blogspot.com/2008/01/script-to-generate-all-possible.html)

That's pretty cool! Thanks for posting this, I'm going enjoy trying to create a few lists from it. Also take a look at CUPP v3 too [http://www.remote-exploit.org/?p=546](http://www.remote-exploit.org/?p=546) and [http://www.digininja.org/projects/cewl.php](http://www.digininja.org/projects/cewl.php) to test your webpages for vulnerabilties where your subject may be too closely linked to your passwords.

---

