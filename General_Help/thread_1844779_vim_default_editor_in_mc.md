---
title: "vim default editor in mc"
date: 2011-09-15
forum: General Help
---

### Post by chris1497 on 2011-09-15
I want to use vim when I hit f4 (view) in midnight commander but I can't seem to get it to work.  It keeps using nano

I have export EDITOR="vim" in my bashrc file
vim is in my PATH
if I use 
```
edit some.txt
```this does open it in vim

I have also changed the alternatives to vim using 

```
sudo update-alternatives --config editor
```and I have disabled the "edit in internal editor" and "view in internal editor" under Options>Configuration inside of mc and saved my configuration.

I've also started new terminals.

the only flaw I can see is that when I 
```
echo $EDITOR 
```I get a blank line

---

