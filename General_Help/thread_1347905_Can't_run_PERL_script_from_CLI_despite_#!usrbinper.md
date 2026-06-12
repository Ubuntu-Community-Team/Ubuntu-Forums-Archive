---
title: "Can't run PERL script from CLI despite #!/usr/bin/perl"
date: 2009-12-06
forum: General Help
---

### Post by texpat on 2009-12-06
I have a weird problem with running perl scripts:

[FONT="Courier New"]**% perl myscript.pl**[/FONT] runs without a problem. 

I do use [FONT="Courier New"]**#!/usr/bin/perl**[/FONT] at the top of the script, so normally it should run if I simply type 

```
% myscript.pl
```

but what I get is

```
% myscript.pl: command not found
```

Obviously, perl is installed (otherwise '[FONT="Courier New"]perl myscript.pl[/FONT]' wouldn't run). It is also located in [FONT="Courier New"]/usr/bin/[/FONT]. Oh, of course I made the script executable. I've played around with permissions on the odd chance that had anything to do with it.

So I'm rather confused and would appreciate any ideas.

---

### Post by DaithiF on 2009-12-06
```
./myscript.pl
```

unless myscript.pl happens to be in a directory on your path you have to tell the shell where to find it.

---

### Post by VCoolio on 2009-12-06
Is the script executable? Run 
chmod +x myscript.pl
and try again

---

### Post by texpat on 2009-12-06
@DaithiF
Yep, that did it! Thanks. I thought that if I was in the script's directory it'd be found automatically (I think DOS does that).

Cheers to VCoolio, too, even though that wasn't the problem.;)

---

