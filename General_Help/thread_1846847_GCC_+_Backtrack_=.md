---
title: "GCC + Backtrack ="
date: 2011-09-19
forum: General Help
---

### Post by k_0z on 2011-09-19
Ok, so I'm running Ubuntu 10.04 and I'm trying to compile C. 

Each time I compile I get:  

[COLOR=Green]GCC[/COLOR]: [COLOR=Blue]filename.c[/COLOR] > [COLOR=Red]a.out  [/COLOR]

What I want to do is:  

[COLOR=DeepSkyBlue][COLOR=Green]GCC[COLOR=Black]:[/COLOR][/COLOR] [COLOR=YellowGreen][COLOR=Blue]filename.c[/COLOR] [/COLOR][COLOR=Black]>[/COLOR] [COLOR=Blue]filename.out  [/COLOR][/COLOR]

Is this possible to do?  

I thought I'd get a bunch of a.out files in the same directory, but a.out gets overwritten.  I better keep all of my programs in one directory, if I want to keep a good organized environment. Thanks for your help!

---

### Post by Slim Odds on 2011-09-19
> **k_0z said:**
> Ok, so I'm running Ubuntu 10.04 and I'm trying to compile C. 

Each time I compile I get:  

[COLOR=Green]GCC[/COLOR]: [COLOR=Blue]filename.c[/COLOR] > [COLOR=Red]a.out  [/COLOR]

What I want to do is:  

[COLOR=DeepSkyBlue][COLOR=Green]GCC[COLOR=Black]:[/COLOR][/COLOR] [COLOR=YellowGreen][COLOR=Blue]filename.c[/COLOR] [/COLOR][COLOR=Black]>[/COLOR] [COLOR=Blue]filename.out  [/COLOR][/COLOR]

Is this possible to do?  

I thought I'd get a bunch of a.out files in the same directory, but a.out gets overwritten.  I better keep all of my programs in one directory, if I want to keep a good organized environment. Thanks for your help!

See the -o option to specify an output filename

```
gcc -o filename.out filename.c
```

---

### Post by Alucinari on 2011-09-19
If you put -o after gcc you can specify your file name.

```
gcc -o DESIREDNAME filetocompile.c
```



Oh, yea, as the guy above me said..

---

### Post by k_0z on 2011-09-19
> **Slim Odds said:**
> See the -o option to specify an output filename

```
gcc -o filename.out filename.c
```

Beautiful!

It worked and thanks guys! I'm going to keep learning and dreaming of the day I become as 1337 as all of you.

Someone told me about a wrapper script that could add flags automatically. Any suggestions on how to get that up and running?

---

### Post by Alucinari on 2011-09-19
You might be interested in the "man" command to bring up a manual about what certain commands do and how they can be modified.

```
man gcc
``` 

for example, give you a list of other things you can do with gcc.  It works for learning what other commands do as well.

---

