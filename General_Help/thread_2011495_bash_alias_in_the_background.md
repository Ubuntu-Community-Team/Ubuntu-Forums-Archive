---
title: "bash alias in the background"
date: 2012-06-27
forum: General Help
---

### Post by vinay_wagh on 2012-06-27
Apologies if the following question is already answered here. With several combinations of google search I couldnt find any answer.

How does one define an alias so as to run the command in background. 
e.g. I would like to define an alias 
$ > alias e='emacs'

But would like to put it in the background, which is similar to
$ > e a.txt &

But rather than giving the ampersand `&` every time, is it possible to incorporate it in alias command?

Thanks in advance

VInay
P.S.
I am using Ubuntu 12.04 with bash (4.2.24(1)-release).

---

### Post by The Cog on 2012-06-27
I don't have emacs so I experimented with xeyes.
> alias e='xeyes &'
seems to do the trick for me.

---

### Post by steeldriver on 2012-06-27
I think the issue is the passing of the filename argument, not the backgrounding per se - you could do it with a simple bash function rather than an alias I think, 

```
function e() { emacs $1 & }
```I don't know if this is good practice though... ymmv

---

### Post by drmrgd on 2012-06-27
I had that same thought - the issue was passing an argument - and you're right, I think you need a function to do it.  I scribbled up the same thing, but with an error check (not that it matters...just out of boredom!):

```

function e() {
    if [ ! -n "$1" ]; then
        echo "USAGE: e <filename>";
    else
        ( emacs "$1" & );
    fi
}

```

---

### Post by vinay_wagh on 2012-06-27
Thanks steeldriver,
The trick seem to work, irrespective of it is a common practice or not! 

@Experts: is there any drawback of this trick? 

Thanks once again

VInay

---

### Post by steeldriver on 2012-06-27
you should definitely use drmrgd's version not mine - as well as error checking he remembered to quote the argument! (in case the filename has spaces etc.)

---

### Post by Vaphell on 2012-06-27
+1 to drmrgd's example


aliases work like simple text substitution and they act as a single block, it's not possible to split them into functional parts. Your arguments are always at the end.
alias a='cmd -a b -c d e ...' when used 
$ a p1 p2
becomes 
$ [COLOR="Navy"]cmd -a b -c d e ...[/COLOR] p1 p2


in cases where you need something fancier (like here, with something specific at the very end), you want functions or scripts. With them you have the total freedom how you want to construct the actual command to be executed.

---

### Post by vinay_wagh on 2012-06-28
Thanks all of you for the quick support. drmgd's reply is really fantastic. I also tried it with the filename with spaces.

Thanks once again.

-- VInay

---

