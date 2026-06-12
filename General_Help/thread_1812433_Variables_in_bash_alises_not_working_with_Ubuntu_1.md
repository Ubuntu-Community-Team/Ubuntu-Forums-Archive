---
title: "Variables in bash alises not working with Ubuntu 11.04"
date: 2011-07-26
forum: General Help
---

### Post by rhugga on 2011-07-26
I am trying to use the following bash alias:

alias rd="host=\$1;rdesktop -u myuser -d mydomain -p mypassword -a 16 -g 1280x960 -k en-us -T \$host -x l -5 -0 \$host &"

I've been able to get this working under mac and solaris. 

I've also tried not escaping the vars.

Anyone know if this is doable with ubuntu's bash shell? (or any meaningful workaround other than writing a script for this?)

Thx

---

### Post by AlphaLexman on 2011-07-26
> **rhugga said:**
> alias rd="host=\[COLOR="Red"]$1[/COLOR];rdesktop -u myuser -d mydomain -p mypassword -a 16 -g 1280x960 -k en-us -T \$host -x l -5 -0 \$host &"
In bash, there is no mechanism for using arguments in the replacement text.

Use a function instead.

Regards.

---

### Post by seawolf167 on 2011-07-26
> **AlphaLexman said:**
> In bash, there is no mechanism for using arguments in the replacement text.

Yup, OP I suggest you read through [this BashGuide ]("http://mywiki.wooledge.org/BashGuide")if you want to learn Bash Scripting

---

