---
title: "pgp --clearsign"
date: 2010-08-07
forum: General Help
---

### Post by S.R on 2010-08-07
I was trying to sign my Ubuntu Conduct Agreement with the key I created for luanchpad.  I have one other key that is used for my private folder.

While using pgp --clearsign to sign my agreement it kept using the first key I created for my private folder. My work around was to create an email and then copy/paste using the correct key.

My question is how can I select between multiple keys from the terminal with pgp --clearsign?

Thanks

---

### Post by chopinhauer on 2010-08-07
> **S.R said:**
> 
My question is how can I select between multiple keys from the terminal with pgp --clearsign?


The **-u** switch to the gpg command, cf. the [gpg manpage]("http://manpages.ubuntu.com/manpages/lucid/en/man1/gpg.1.html#toptoc7") (also available by typing 'man gpg').

PS: If you are wondering how to remember all the options, the shell auto-completes the options when you type '--<tab>' (the <tab> key).

---

### Post by S.R on 2010-08-07
Nice! Thanks for the help.

---

