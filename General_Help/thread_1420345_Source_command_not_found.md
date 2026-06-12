---
title: "Source command not found"
date: 2010-03-03
forum: General Help
---

### Post by jus71n742 on 2010-03-03
9.10 Bash shell.
```

Linux $ sudo source ./vars 
sudo: source: command not found

Linux $ sudo . ./vars
sudo: .: command not found

Linux $ sudo /bin/bash -c source ./vars
./vars: line 0: source: filename argument required
source: usage: source filename [arguments]

Linux $ which source
Linux $

Linux $ type source
source is a shell builtin
Linux $ type .
. is a shell builtin

```

I think this is all the ways I tried it.  any ideas?

---

### Post by lyall on 2010-03-03
see Bash Reference Manual 
[http://www.gnu.org/software/bash/manual/bashref.html#Shell-Functions]("http://www.gnu.org/software/bash/manual/bashref.html#Shell-Functions")

for linux commands see
[http://www.oreillynet.com/linux/cmd/#s]("http://www.oreillynet.com/linux/cmd/#s")

I did not see Source in the Linux cammands

the two links might help, I do not know

good luck and have fun learning

---

### Post by asmoore82 on 2010-03-03
As you have discovered, source only exists as a shell builtin and
as such cannot be sudo'd ...

What's the bigger picture for you though?

---

### Post by jus71n742 on 2010-03-03
reading an article on Open VPN, and the above is one of the steps creating PKI environment

---

### Post by asmoore82 on 2010-03-03
can you post a link to the article ~ it doesn't sound like a very well done one so far.

---

### Post by jus71n742 on 2010-03-03
Maybe, I will look, its in the march 2010 issue of Linux Journal issue 191

if I su into it it works just fine...I forgot to set that up.

---

### Post by asmoore82 on 2010-03-03
> **asmoore82 said:**
> can you post a link to the article ~ it doesn't sound like a very well done one so far.

I may take that back, it's possible that it just wasn't intended for the sudo-sytle systems.

---

### Post by flippo on 2010-03-03
<I think> Since when you run sudo it keeps your bash shell's environment variables, just ```
source <file>
``` should be equivalent to```
sudo source <file>
``` for your needs, if your running everything through sudo.  <I think>

---

### Post by jus71n742 on 2010-03-04
> **flippo said:**
> <I think> Since when you run sudo it keeps your bash shell's environment variables, just ```
source <file>
``` should be equivalent to```
sudo source <file>
``` for your needs, if your running everything through sudo.  <I think>

Well this isn't supposed to be done though a ```
sudo
``` enviroment. 
it needs to be done through a ```
su
``` into Root

---

