---
title: "Terminal Name Replaced Due to Bashrc"
date: 2011-09-20
forum: General Help
---

### Post by kpryde on 2011-09-20
Hi all,

I was at a hackathon this weekend, and now whenever I open up my terminal I get this message:

bash: /home/jennifer/.bashrc: line 87: syntax error near unexpected token `;&'
bash: /home/jennifer/.bashrc: line 87: `alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '''s/^s*[0-9]+s*//;s/[;&|]s*alert$//''')"''
[e]0;u@h: wa]u@h:w$ 


The only issue I see is that it replaced my username. Any help?

---

### Post by AlphaLexman on 2011-09-20
You could just comment out line #87 as it's only an alias. Is your prompt different after also?

---

### Post by kpryde on 2011-09-21
It changes my name on the terminal to [e]0;u@h: wa]u@h:w$ 
 and doesn't let me see what directory I am in. I commented out the line and now i get the following:


The program 'ali' can be found in the following packages:
 * mailutils-mh
 * nmh
Try: sudo apt-get install <selected package>
bash: /.npm/nvm/0.0.6/package/nvm.sh: No such file or directory
[e]0;u@h: wa]u@h:w$

---

### Post by philinux on 2011-09-21
> **kpryde said:**
> It changes my name on the terminal to [e]0;u@h: wa]u@h:w$ 
 and doesn't let me see what directory I am in. I commented out the line and now i get the following:


The program 'ali' can be found in the following packages:
 * mailutils-mh
 * nmh
Try: sudo apt-get install <selected package>
bash: /.npm/nvm/0.0.6/package/nvm.sh: No such file or directory
[e]0;u@h: wa]u@h:w$

Here's a copy of a default bashrc file to compare. Or substitute.

---

### Post by kpryde on 2011-09-21
I replaced my file with the one philinux posted and the problem was fixed. Thanks guys.

---

