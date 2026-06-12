---
title: "ZSH Alias use"
date: 2010-01-24
forum: General Help
---

### Post by oneindelijk on 2010-01-24
Hi, 

I've recently started fiddling around with zsh and I'm trying to create an alias where I want to insert the text from the commandline in between.
For example:
I use this command to add new aliases:
```
echo alias 'pc0=ssh -X user@machine' >> /etc/zsh/zaliases
```
What I looking for is an alias so I can type for example
```
add 'pc0=ssh -X user@machine' 
```
So I would need to define an alias 'add' that contains ```
echo alias <*> >> /etc/zsh/zaliases
``` whereby the text after 'add' is inserted at <*>

Is there a way do do this ?

thx a lot for all help

---

### Post by dcstar on 2010-01-24
> **oneindelijk said:**
> Hi, 

I've recently started fiddling around with zsh and I'm trying to create an alias where I want to insert the text from the commandline in between.
For example:
I use this command to add new aliases:
```
echo alias 'pc0=ssh -X user@machine' >> /etc/zsh/zaliases
```
What I looking for is an alias so I can type for example
```
add 'pc0=ssh -X user@machine' 
```
So I would need to define an alias 'add' that contains ```
echo alias <*> >> /etc/zsh/zaliases
``` whereby the text after 'add' is inserted at <*>

Is there a way do do this ?

thx a lot for all help

Try $1 for the typed text.

---

