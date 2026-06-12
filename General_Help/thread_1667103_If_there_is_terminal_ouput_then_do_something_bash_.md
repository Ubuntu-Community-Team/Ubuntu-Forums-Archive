---
title: "If there is terminal ouput then do something bash question"
date: 2011-01-14
forum: General Help
---

### Post by dodo3773 on 2011-01-14
Is there any way to run a command only if another command produces terminal output? I want to run 

```
netstat --tcp --numeric |  cut -c 45-65 | sort -u | sed '/Foreign/d' | sed '/^$/d' | grep -e ':80' -e ':443'
```and if that produces output in the shell then run 

```
echo 'http / https' && netstat --tcp --numeric |  cut -c 45-65 | sort -u | sed '/Foreign/d' | sed '/^$/d' | grep -e ':80' -e ':443'
```but also suppress the output from the original check. 

The script that I have so far is 

```
#! /bin/bash
if netstat --tcp --numeric |  cut -c 45-65 | sort -u | sed '/Foreign/d' | sed '/^$/d' | grep -e ':80' -e ':443' ; then
echo 'http / https' && netstat --tcp --numeric |  cut -c 45-65 | sort -u | sed '/Foreign/d' | sed '/^$/d' | grep -e ':80' -e ':443'
fi


exit
```which produces

```
24.143.207.65:80     
http / https
24.143.207.65:80
```I am still new at this and know that there is something I am missing but I cannot seem to figure it out. I read a bash syntax guide that I found online but I still just don't get it. Any help would be greatly appreciated.

---

