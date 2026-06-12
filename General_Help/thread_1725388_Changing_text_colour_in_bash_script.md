---
title: "Changing text colour in bash script"
date: 2011-04-09
forum: General Help
---

### Post by Spyderkid on 2011-04-09
How can I go about making an echo with specific text in colour in bash?......

this is the result I want:
```

I like [COLOR="Red"]**Red!**[/COLOR]

```

---

### Post by TeoBigusGeekus on 2011-04-09
Download [this]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") book and look at Chapter 14: Customizing the prompt.

---

### Post by CharlesA on 2011-04-09
See here:
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html)

---

### Post by Spyderkid on 2011-04-10
I don't want to change the prompt I wan't to change specific text in an echo

thanks

---

### Post by AlphaLexman on 2011-04-10
Color in a prompt works the same way in an echo statement.
```
echo -e "The quick\e[1;31m red\e[0m fox jumps over the lazy dog."
```
The escape codes can change the foreground and/or background of the text.

---

