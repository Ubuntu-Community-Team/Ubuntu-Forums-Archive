---
title: "bash history: have up arrow filter only matching entries"
date: 2011-12-04
forum: General Help
---

### Post by matteosistisette on 2011-12-04
Hi,

I remember using linux (don't know which distros but I'm almost sure it was more than one) ages ago, and when I started typing a command in a terminal and I hit the up arrow key, it would show me only commands that started with those characters I had typed.

For example, suppose the most recent commands in my bash history were (latest first) were: "ls -la", "grep foo /", "clear", "groupadd bar". If I typed "gr" and then hit the up arrow key, the command "grep foo" would appear, because it was the most recent that matched "gr".

Now this does not happen in Ubuntu, nor has it for ages. When I hit the up arrow key, the last item (and then the last but one, and so on) in the bash history shows up, no matter whether it matches or not what I have typed so far.

Is there some configuration file somewhere that I can edit to have this feature back? And by the way, is there a reason why it was "removed"? It seems to me extremely useful and I can't see any drawbacks in it...

---

### Post by Lars Noodén on 2011-12-04
What if you type ctrl-r first before entering your letters and pressing the up arrow?

---

### Post by m_duck on 2011-12-04
You could add the following to ~/.inputrc```
"\e[A":history-search-backward
"\e[B":history-search-forward
```Source: [Arch Wiki - Readline]("https://wiki.archlinux.org/index.php/Readline#History")

---

### Post by matteosistisette on 2011-12-04
> **Lars Noodén said:**
> What if you type ctrl-r first before entering your letters and pressing the up arrow?

Interesting, thanks. Is there a way to see more matches? I mean, if there are two or more matches, it will only show one (I guess the latest), is there a key that will show me the next match?

EDIT: found it, just press Ctrl+R again :)

---

### Post by matteosistisette on 2011-12-04
> **m_duck said:**
> You could add the following to ~/.inputrc```
"\e[A":history-search-backward
"\e[B":history-search-forward
```Source: [Arch Wiki - Readline]("https://wiki.archlinux.org/index.php/Readline#History")

Thanks a lot, this is EXACTLY what I was looking for :)

---

