---
title: "Where is Perl?"
date: 2006-06-09
forum: General Help
---

### Post by Vyizis on 2006-06-09
I have installed a LAMP install from the ubuntu cd and i am trying to install webmin. The only problem is that it is asking me for the location of the full path to perl on my system and i cant find it for the life of me. Any body got any clues?

---

### Post by taurus on 2006-06-09
Run this command to search for perl on your machine.
```

sudo find / -name perl -print

```
If it returns nothing, then you need to install it with apt-get!!!
```

sudo apt-get install perl

```

---

### Post by Vyizis on 2006-06-09
Thanks, that sorted me out.

---

### Post by taurus on 2006-06-09
[QUOTE=Vyizis]Thanks, that sorted me out.[/QUOTE]
You're welcome.  :cool:

---

### Post by scxtt on 2006-06-10
i know it's a little late, but you were SO close - just cause of your subject line!```
$hostname [~]
:> [color=red]whereis perl[/color]
[color=green]perl: /usr/bin/perl[/color] [...]
```unless a LAMP install doesn't include perl - which would kinda shock me, figured that'd be a staple of any web-based suite ...

---

### Post by anthro398 on 2006-06-10
[QUOTE=taurus]Run this command to search for perl on your machine.
```

sudo find / -name perl -print

```
If it returns nothing, then you need to install it with apt-get!!!
```

sudo apt-get install perl

```[/QUOTE]

I would think 'which' would be much simpler than the complex syntax of find.
```
me@kailua:~/live$ which perl
/usr/bin/perl
```

---

