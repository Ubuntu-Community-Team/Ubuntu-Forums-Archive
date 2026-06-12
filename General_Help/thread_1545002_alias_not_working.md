---
title: "alias not working"
date: 2010-08-03
forum: General Help
---

### Post by cmcanulty on 2010-08-03
I tried to set up an alias for update, upgrade and clean by putting this line into my .bach.rc file

```
#alias  ud= 'aptitude update && sudo aptitude upgrade && sudo aptitude dist-upgrade && sudo aptitude autoclean'

```

but when I type ud I get this error message, by the way I tried the bash.rc entry both commented and uncommented with the same result.

```
bash: alias: sudo apt-get update && sudo apt-get upgarde && sudo apt-get clean: not found
```

 I am not sure what I am doing wrong. I got the command from a help forum, don't remember the exact place, thank you

```
#alias  ud= 'aptitude update && sudo aptitude upgrade && sudo aptitude dist-upgrade && sudo aptitude autoclean'

```

I also tried this one
```
alias ud= 'sudo apt-get update && sudo apt-get upgarde && sudo apt-get clean'
```

---

### Post by Elfy on 2010-08-03
Remove the space - and check the spelling 

alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'

---

### Post by cmcanulty on 2010-08-03
Thanks, sorry that makes me feel really dumb. I have to wait to try it as I just manually updated. Is it correct to put # before it or not, that # really confuses me.

---

### Post by Elfy on 2010-08-03
You musn't use the # 

A # will stop the alias working - no idea of the technical jargon, but basically a # causes a line to be ignored.

---

### Post by cmcanulty on 2010-08-03
OK thanks I3 had tried it first without the # but I guess the spaces was the problem, solved!

---

