---
title: "alternative for xterm"
date: 2010-11-10
forum: General Help
---

### Post by thol4u on 2010-11-10
Hi All,

I'm using Lucid 10.04 and usually ssh to many unix server. I have created aliases with server name, that executes xterm command as below.

I'm getting frustrated by inability to copy and paste using keyboard shortcuts, always have to use middle button. Is there any alternative out there?

Appreciate any help or pointers

Thanks

----------
alias "acme=xterm -font 10x20 -bg     pink    -title    acme    -sb -sl 250 -e ssh chidamba@acme &"
alias "apex=xterm -font 10x20 -bg     skyblue    -title    apex    -sb -sl 250 -e ssh chidamba@apex &"
alias "bach=xterm -font 10x20 -bg     skyblue    -title    bach    -sb -sl 250 -e ssh chidamba@bach &"
alias "centipede=xterm -font 10x20 -bg     skyblue    -title    centipede -sb -sl 250 -e ssh chidamba@centipede &"
alias "escher=xterm -font 10x20 -bg     skyblue    -title    escher    -sb -sl 250 -e ssh chidamba@escher &"

---

### Post by TeoBigusGeekus on 2010-11-10
ctrl-insert : copy

shift-insert : paste

---

### Post by thol4u on 2010-11-10
> **TeoBigusGeekus said:**
> ctrl-insert : copy

shift-insert : paste

Thanks for the reply, but it doesn't work, does it require any setting or keybinding?

---

### Post by TeoBigusGeekus on 2010-11-10
> **thol4u said:**
> Thanks for the reply, but it doesn't work, does it require any setting or keybinding?
No, it doesn't.
Funny, it works for me.

---

### Post by I'mGeorge on 2010-11-10
I'll say go for aterm, a very nice terminal emulator with transparency support as well.

In linux the copy paste keyboard terminal shortcuts are not ctrl+c, ctrl+v but ctrl+shif+c, ctrl+shift+v if you don't like the middle mouse button

---

### Post by mcduck on 2010-11-10
> **I'mGeorge said:**
> 
In linux the copy paste keyboard terminal shortcuts are not ctrl+c, ctrl+v but ctrl+shif+c, ctrl+shift+v if you don't like the middle mouse button

+1 to this.

You are not going to find a terminal emulator that would use ctrl-c & ctrl-v for copy/paste, as those keyboard shortcuts already have a completely different purpose in the shell.

---

