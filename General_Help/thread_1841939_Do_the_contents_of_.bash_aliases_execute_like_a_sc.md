---
title: "Do the contents of .bash_aliases execute like a script?"
date: 2011-09-10
forum: General Help
---

### Post by ninjaaron on 2011-09-10
I have a folder for all of my personal scripts, and I want bash to automatically generate aliases for all of them.  This would be easy with... a script (what else?).

Anyway, I'm wondering if I can just call the script to do this from .bash_aliases or .bashrc

Thanks,
Aaron

---

### Post by sisco311 on 2011-09-10
I just keep my scripts in ~/bin. If the directory exist, by default, it's added to the PATH. In this way I can run them without having to specify the full or relative path to them.

---

### Post by llamabr on 2011-09-10
Both of those .bash_aliases and .bashrc run everything you run bash, like, for example when you reboot or log in.  Any aliases you put in either of those files will install every time you log in.

I keep all of mine in .bashrc

---

### Post by Absol on 2011-09-10
> **ninjaaron said:**
> I have a folder for all of my personal scripts, and I want bash to automatically generate aliases for all of them.  This would be easy with... a script (what else?).

Anyway, I'm wondering if I can just call the script to do this from .bash_aliases or .bashrc

Thanks,
Aaron

.bash_aliases is run by other script but as llamabr said it runs every time you login, you can place aliases there or in .bashrc or in other scripts in /etc folder

```
absol@Freiya:~$ cat .bash_aliases
alias hgrep="history | grep "
alias bell="ssh -X 10.8.16.1"
alias grep='grep -n --color=always '

```

i use it this way

---

### Post by sisco311 on 2011-09-10
In Ubuntu, by default, if ~/.bash_aliases exist it's sourced in ~/.bashrc.

So it runs every time you start an interactive shell.

---

### Post by ninjaaron on 2011-09-10
> **sisco311 said:**
> I just keep my scripts in ~/bin. If the directory exist, by default, it's added to the PATH. In this way I can run them without having to specify the full or relative path to them.

I'll just do that then.  Thanks!


And thanks to everyone for the answers.

Solved.

---

### Post by AlphaLexman on 2011-09-10
To answer the question in the title of the thread, YES and NO, ~/.bash_aliases is 'sourced' meaning the shell reads its contents, but it is not 'executed' in the way a script is executed with a 'shebang' on the first line.

However the ~/.bash_aliases file can utilize all shell commands such as the 'if' statement. For example...
```
if [[ `which htop 2>/dev/null` ]]; then 
	alias top='htop'
fi
```
Will use 'htop' instead of 'top' if it exists!

---

