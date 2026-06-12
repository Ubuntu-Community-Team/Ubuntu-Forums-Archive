---
title: "Help with two aliases in bashrc?"
date: 2011-01-01
forum: General Help
---

### Post by kgarbutt on 2011-01-01
Can I combine these two aliases into one alias?

alias vdir='cd /home/smooth/Documents/vuze'
alias vuze='./azureus'

Thank you for your help?

---

### Post by sisco311 on 2011-01-01
```
alias whatever='cd /home/smooth/Documents/vuze && ./azureus'
```

---

### Post by kgarbutt on 2011-01-01
Bingo! Thanks sisco. I appreciate your help.

---

### Post by sisco311 on 2011-01-01
You are welcome!

You can't combine two or more aliases in a new one, but you can write a function:
```
function_name () {
  vdir
  vuze
}

```

If you want to learn more about aliases and functions, check out [http://mywiki.wooledge.org/BashGuide/CompoundCommands](http://mywiki.wooledge.org/BashGuide/CompoundCommands)

Oh, and don't forget to mark your threads as [SOLVED].

---

