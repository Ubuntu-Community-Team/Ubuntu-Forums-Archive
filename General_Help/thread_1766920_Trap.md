---
title: "Trap"
date: 2011-05-25
forum: General Help
---

### Post by COKEDUDE on 2011-05-25
Could anyone tell me what package trap is in? I see we have a man page on trap here. So I would think we would have it. I tried to search the repository but didn't see it. 

[http://manpages.ubuntu.com/manpages/natty/en/man1/trap.1posix.html](http://manpages.ubuntu.com/manpages/natty/en/man1/trap.1posix.html)

Normally when you type a command wrong or you try to use a command that is in a package you don't have you will get a message like this. 

```
~ $ 7zip
No command '7zip' found, did you mean:
 Command 'lzip' from package 'lzip' (universe)
 Command 'jzip' from package 'jzip' (universe)
 Command 'zip' from package 'zip' (main)
 Command 'p7zip' from package 'p7zip' (universe)
 Command 'wzip' from package 'wzip' (universe)
 Command 'xzip' from package 'xzip' (universe)
 Command 'mzip' from package 'mtools' (main)
 Command 'gzip' from package 'gzip' (main)
 Command 'rzip' from package 'rzip' (universe)
7zip: command not found

```

I didn't get any of this. 

```
~ $ trap

```

---

### Post by papibe on 2011-05-25
trap is built-in statement of bash. It is already installed (because is part of bash). Try:
```
$ trap --help
```
Check this couple of tutorials to learn how of use it: [Bash Traps]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_12_02.html"), and [Use the Bash trap Statement.]("http://www.linuxjournal.com/content/use-bash-trap-statement-cleanup-temporary-files")

I hope it helps.

---

### Post by COKEDUDE on 2011-05-30
> **papibe said:**
> trap is built-in statement of bash. It is already installed (because is part of bash). Try:
```
$ trap --help
```
Check this couple of tutorials to learn how of use it: [Bash Traps]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_12_02.html"), and [Use the Bash trap Statement.]("http://www.linuxjournal.com/content/use-bash-trap-statement-cleanup-temporary-files")

I hope it helps.

Thank you for this.

---

