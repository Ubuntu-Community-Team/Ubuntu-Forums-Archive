---
title: "Ubuntu 10.04 - Compiz won't change window border"
date: 2010-07-03
forum: General Help
---

### Post by Cant on 2010-07-03
(This started after I upgraded from Ubuntu 8 ) Everytime I enable desktop effects (system -> preferences -> appearance) compiz replaces the pretty New Wave window border with the ugly Emerald glass window border (custom border) that I used on Ubuntu 8.

---

### Post by anand_30 on 2010-07-03
> **Cant said:**
> (This started after I upgraded from Ubuntu 8 ) Everytime I enable desktop effects (system -> preferences -> appearance) compiz replaces the pretty New Wave window border with the ugly Emerald glass window border (custom border) that I used on Ubuntu 8.

Dont know much about compiz coz its not working on my system showing me that there is a bug.
So may be this solution will not work but you can try....
have you tried this..?
```
metacity --replace
```

---

### Post by Cant on 2010-07-03
> **anand_30 said:**
> Dont know much about compiz coz its not working on my system showing me that there is a bug.
So may be this solution will not work but you can try....
have you tried this..?
```
metacity --replace
```

That's not really a solution. I want compiz to work with the system borders, not just use metacity instead.

---

### Post by yossell on 2010-07-03
does running

compiz-decorator --replace

help?

---

### Post by Cant on 2010-07-03
> **yossell said:**
> does running

compiz-decorator --replace

help?

Nope. Terminal just says "starting gtk-window-decorator" and then hangs.

Nothing happens when I try Alt-f2, either.

---

### Post by yossell on 2010-07-03
hmm - when I run that command in a terminal I get the same message, but the windows borders change from the emerald theme back to the theme set by the standard appearance tabs. 

When you run compizconfig settings manager and go to effects and click window decoration, what is specified in the command line there? in my case, it's /usr/bin/compiz-decorator. I'm wondering if your has somehow been changed to emerald.

but it may just be a shot in the dark.

---

### Post by Cant on 2010-07-03
> **yossell said:**
> hmm - when I run that command in a terminal I get the same message, but the windows borders change from the emerald theme back to the theme set by the standard appearance tabs. 

When you run compizconfig settings manager and go to effects and click window decoration, what is specified in the command line there? in my case, it's /usr/bin/compiz-decorator. I'm wondering if your has somehow been changed to emerald.

but it may just be a shot in the dark.

Yeah, it worked. Thanks :popcorn:

---

### Post by DJYoshaBYD on 2010-07-03
just throwing this out there.. i do this everytime, and it works great

get compiz installed

get emerald installed

add the following to the window decorator command box in the compiz settings

```
emerald --replace
```

then, start compiz.. it will start emerald with it

```
compiz --replace
```

booya.. 

then i just save my session, and tell my system to use that session on startup..

maybe a lil harder or whatever, but its quick and easy for me.. plus, emerald is a sweet window decorator..

---

