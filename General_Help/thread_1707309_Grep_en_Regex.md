---
title: "Grep en Regex"
date: 2011-03-15
forum: General Help
---

### Post by Guerreiro on 2011-03-15
Esteemed Ubuntu'ers,

Maybe this is not the correct place to post and ask this question but this community can do anything, so I would appreciate it if you could help me out with a little, simple, regex and grep.

So far I got :


```
cat onlinecasinogokkencasinoonlinebonussen.wordpress.2011-03-15.xml | grep -e  "<title>" -e "<content:encoded>" > Test.txt
```


And I want it to read:


```
cat onlinecasinogokkencasinoonlinebonussen.wordpress.2011-03-15.xml | grep -e  "<title>" -e "<content:encoded>infinite random chars a-z,A-Z,.,,,0-9,$,€ so on </content:encoded>" > Test.txt
```

Pseudocode of course. :D 
Because it needs to pick out the whole part between <content:encoded> and </content:encoded> if you follow me. :) 

Thanks a lot if you can help me out and if you need more info let me know.

---

### Post by Another Monkey on 2011-03-15
Have you tried searching for Regular expressions?  There's loads of guides and on-line tools available.

At a guess, something like this might work
```
grep -e  "<title>" -e "<content:encoded>.*</content:encoded>"
```

Not sure if you'll need to worry about end-of-line etc, but that's easy enough to sort out.  Plenty of examples.

---

### Post by Guerreiro on 2011-03-15
Sadly that one did not work :S , but can you give me a good keyword to search for. I am drawing blank today. :(


======================================================

Something that I tried.

```
cat onlinecasinogokkencasinoonlinebonussen.wordpress.2011-03-15.xml | grep -e  "<title>" -e "<content:encoded>.*" -e "</content:encoded>" > Test.txt
```

Then I get the line with <content:encoded> and the last line.. but not the stuff in between :S would [:alnum:] and [:space:] contribute much?

---

