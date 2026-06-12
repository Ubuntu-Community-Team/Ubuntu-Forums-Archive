---
title: "a question on bash script"
date: 2011-03-24
forum: General Help
---

### Post by volvolinux on 2011-03-24
Hello
 
I am a bash beginner. Can I know what is the meaning of the following meaning:?
 
export EASY_RSA="${EASY_RSA:-.}"

i know it  exports EASY_RSA to my environment variables, however, why it need to be "${EASY_RSA:-.}"? the result is the same.
 
I try to goole some, but the most clue i can got is that to avoid some misunderstanding for the system, like - can mean redirection.... but I can't get more detailed part....
 
pelase help.

---

### Post by sisco311 on 2011-03-24
```
man bash | less +/"^ +Parameter Expansion"
```

;)

"${EASY_RSA:-.}" = if EASY_RSA is unset or null, . (a period) is substituted.

---

### Post by nothingspecial on 2011-03-24
This explains the same thing but with examples and in a style that presumes a human being is reading it.

[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)

---

### Post by volvolinux on 2011-03-25
> **sisco311 said:**
> ```
man bash | less +/"^ +Parameter Expansion"
```
 
;)
 
"${EASY_RSA:-.}" = if EASY_RSA is unset or null, . (a period) is substituted.
 
thanks man. withou you i can't understantd it so fast

---

