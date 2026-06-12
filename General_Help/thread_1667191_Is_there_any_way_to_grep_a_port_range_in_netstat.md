---
title: "Is there any way to grep a port range in netstat"
date: 2011-01-14
forum: General Help
---

### Post by dodo3773 on 2011-01-14
Right now I have 
```
netstat --tcp --numeric |  cut -c 45-65 | sort -u | sed '/Foreign/d' | sed '/^$/d' | grep -e ':80' -e ':443'
```Which will show me all of my http stuff. I would like to continue to do this for Other protocols (email, ftp, etc..) The problem I have is that I cannot figure out how to grep something like :48620-:49150  I am not even sure that this is possible. If it is not then is there any way to create a list of those numbers in this format 

 -e ':48620'
 -e ':48621'
etc...

So that I can just dump that into my script? Also, will that seriously affect the performance of the script if I have to do it that way because of the length? I read somewhere that this sort of thing can be done with sed but I am not really sure. Thanks in advance.

---

