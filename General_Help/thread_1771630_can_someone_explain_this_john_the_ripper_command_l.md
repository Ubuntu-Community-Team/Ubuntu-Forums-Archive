---
title: "can someone explain this john the ripper command line to me?"
date: 2011-05-30
forum: General Help
---

### Post by nethero on 2011-05-30
[FONT=Verdana][FONT=Verdana]Hi there,

I have a rar that I forgot the password on.  I was using rarcrack but it was very slow.  Some comments in some blog posts recommended that I use john the ripper and they used this command line as an example...

[/FONT][/FONT]```
sudo john --wordlist=/usr/share/john/password.lst --rules --stdout | xargs -I jtr unrar e -pjtr rarfile.rar
```[FONT=Verdana][FONT=Verdana]

I understand some of this.  --wordlist is the dictionary,  --rules allows mangleing of the words (not sure what they mean by this exactly, still reading).  The thing is that I don't understand anything after.  I know that xargs allows me to pass additional arguments but most of the rest of that looks like gibberish to me.  Any help would be appreciated.  Thank you.[/FONT]
[/FONT]

---

### Post by gmargo on 2011-05-30
It's explained in the **xargs(1)** and **unrar(1)** man pages.

"xargs -I jtr" means: take each input line (individual test passwords in this case) and perform a substitution on the command of "unrar e -pjtr rarfile.rar", and then run it.  The substitution replaces the string "jtr" with the test password.  The "-p" option of unrar is used to specify the password.

So if your first three test passwords were "alpha", "beta", "gamma", this would be the same as running "unrar" three times with these arguments:
```

unrar e -palpha rarfile.rar
unrar e -pbeta rarfile.rar
unrar e -pgamma rarfile.rar

```

---

### Post by nethero on 2011-05-31
I did some reading on xargs so I have a better understanding now.  Between that and your explanation, I understand perfectly now.  Thanks so much!

---

