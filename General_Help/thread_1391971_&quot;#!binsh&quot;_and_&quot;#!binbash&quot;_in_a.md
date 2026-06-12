---
title: "&quot;#!/bin/sh&quot; and &quot;#!/bin/bash&quot; in a script, what is the difference between them?"
date: 2010-01-27
forum: General Help
---

### Post by rhythmiccycle on 2010-01-27
I just started learning how to make scripts

I noticed some start with
```

#!/bin/sh

```

and others start with

```

#!/bin/bash

```


what is the difference?
how do you know what one to use?
what the worst that can happen if you use the wrong one?
are there any other ways to start a script?

---

### Post by t4thfavor on 2010-01-27
That's the "hashbang" it tells the OS which shell to execute the script in. One is for sh, the other bash.



You can use whatever shell you like the best, currently the default shell in ubuntu is bash. That works with any scripting language though, as PHP would be !#/usr/bin/php or wherever your PHP is installed.

It's not absolutely nessecary as you can call your scripts like

bash /home/user/script.sh

It's just easier to say

./script.sh

---

### Post by stim on 2010-01-27
I believe its called a "shebang" pronounced "sha-bang" not "she-bang".  There is no difference between using sh and bash, bash is a branch of sh. You will not cause problems going from sh->bash but potentially from bash->sh if the script is using bash specific functions.

---

### Post by ean5533 on 2010-01-27
> **rhythmiccycle said:**
> what is the difference?
/bin/sh is the Bourne shell, while /bin/bash is the Bourne-again shell. For any simple script, there isn't much difference in the way they handle things.

> **rhythmiccycle said:**
> how do you know what one to use?
It doesn't matter, as long as you're happy with the features provided by the given shell. /bin/bash is the default shell for Ubuntu and is probably the most commonly used shell, so it's probably best to use that one if you're learning.

> **rhythmiccycle said:**
> what the worst that can happen if you use the wrong one?
Your script won't work. :)

> **rhythmiccycle said:**
> are there any other ways to start a script?
There are tons. See: [Wikipedia article on the Shebang.]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29#Examples")

---

### Post by rhythmiccycle on 2010-01-27
thanks for the reply,

so, it sounds like I should just use bash all the time?

---

### Post by mcduck on 2010-01-27
> **rhythmiccycle said:**
> I just started learning how to make scripts

I noticed some start with
```

#!/bin/sh

```

and others start with

```

#!/bin/bash

```


what is the difference?
how do you know what one to use?
what the worst that can happen if you use the wrong one?
are there any other ways to start a script?

/bin/sh is the default system shell, whatever that happens to be on the distribution you are using (in Ubuntu /bin/sh is linked to Dash).

/bin/bash is, well, Bash.

Different shells are different. For example Bash has some features that Dash (or the original Sh) doesn't have. If you use such features, you need to make sure your script is ran with Bash. If you only use standard sh-compatible stuff in your scripts then using /bin/sh is just fine (and will make your script perform slightly better in Ubuntu, since Dash is lighter than Dash).

(Unlike what's claimed in above posts, it's not exactly correct to say that Bash would be the default shell in Ubuntu. Ubuntu uses two shells by default, Dash is the system shell, used for all system scripts since it's lighter and executes commands quicker. Bash is the default interactive shell for users, so every time you open a terminal you are using Bash)


...and no, you shouldn't be using Bash all the time. It's usually considered a good practise to avoid using Bash-specific features in scripts, and instead stick to standard Sh-compatible commands. That way any shell scripts you write will remain easily portable to other shells (as most of them are compatible with the original Sh). Only use Bash stuff if you really, really need them.

---

### Post by rnerwein on 2010-01-27
hi
sorry i ain't want a bean but was MCDUCK wrote is absolute

---------> +1

ciao

---

### Post by rhythmiccycle on 2010-01-29
in reply to what mcduck said...

my intention is to really understand linux and ubuntu. the more I learn the more questions I have (and the more I dislike windows)

let me be sure I understand thing correctly:

mentioned in this post there are 3 shell scripts types
bash, sh and dash. there are more shells not listed in this post.

each shell has its own set of commands?

and there are commands that work on multiple shells?

Dash is quicker, but Bash is more user friendly????

if i have a code that works in the (ubuntu) terminal, and I want to script it, then bash will always work, on ubuntu????


and the part I don't understand at all is this
> 
stick to standard Sh-compatible commands. That way any shell scripts you write will remain easily portable

portable to other distributions of linux? or portable within ubuntu? will sh scripts work on a Mac??

---

### Post by t4thfavor on 2010-01-29
The last part means don't use any commands that are unique to BASH, because other people on your same system may be using other shells. 

you can do whatever you want though, as it was just a suggestion.

The scripts will work wherever you have an sh compatible shell, so mac, yes.

---

### Post by tgalati4 on 2010-01-29
If you work in  a data center, you can use the same /bin/sh script on supercomputers, unix servers, Red Hat machines, even macs.

---

### Post by raktarok on 2010-01-29
What I have posted may not be that relevant to the ongoing discussion, but this was something that was not obvious to me when I started learning these sort of things. I don't see any use of this particular script, but what the heck, its fun!

```
#!/bin/rm

echo "you won't see this, ever.."
```

and you can do this with all sort of other commands....

---

