---
title: "I colourized my HISTTIMEFORMAT EnviroVar, But...."
date: 2009-10-17
forum: General Help
---

### Post by rob86 on 2009-10-17
I was reading about colourizing my bash a bit, and put this in my .bashrc..

```
HISTTIMEFORMAT=`echo -e "\033[1;34m%F \033[1;31m%T \033[0m"`

```This works, it colourizes and is pretty cool actually, but I noticed two strange things. 

One, why does it have those "stylized" single quotation marks? The ` instead of the normal ' used in programming. I thought it was a bug on the website replacing the programming style quotes with the stylish ones, but as it turns out, those slanted, stylized quotation marks are NECESSARY and when I replaced them, the var didn't work. 

Why? I thought all computer related languages used ' and ", not `

My second question is, this works fine in a terminal like GnomeTerminal, but if I hop into a virtual terminal like tty1 and type $ history , it isn't colourized, yet retains the %F %T format without the colour. They are perfectly capable of using colour since my grep results have colour, so why didn't the colour go with the %F %T?

---

