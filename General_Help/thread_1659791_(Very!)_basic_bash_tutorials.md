---
title: "(Very!) basic bash tutorials"
date: 2011-01-04
forum: General Help
---

### Post by nahallac on 2011-01-04
Hello,
 
I have decided that I can no longer be ignorant of scripting and its fundamentals, and I'm going to start with learning Bash. I have found what looks (at first glance) to be a decent tutorial for a beginner: [http://www.ibm.com/developerworks/library/l-bash.html](http://www.ibm.com/developerworks/library/l-bash.html).
 
Does anyone have any other online resources - or even books - that will be of use to me? Bear in mind that I really am terribly ignorant of all things scripting...

---

### Post by luvshines on 2011-01-04
This one is what I refer to time and again.
Simple, perfect and exhaustive

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

Covers advanced topics as well:
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by KJ KJ KJ on 2011-01-04
Are you aware that Ubuntu uses 'dash' rather than 'bash' by default?

So you'll be puzzled when valid bash scripts don't work with Ubuntu. I'm un-learning bash to suit Ubuntu. 


[http://en.wikipedia.org/wiki/Debian_Almquist_shell](http://en.wikipedia.org/wiki/Debian_Almquist_shell)

*Dash has been the default /bin/sh in [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29") since the 6.10 release in October 2006.[]("http://en.wikipedia.org/wiki/Debian_Almquist_shell#cite_note-4") During the transition by Ubuntu, numerous scripts making use of [Bash]("http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29")-specific functionality (but not declaring it) were discovered.[]("http://en.wikipedia.org/wiki/Debian_Almquist_shell#cite_note-5")[]("http://en.wikipedia.org/wiki/Debian_Almquist_shell#cite_note-6")To avoid errors, Bash-specific scripts can be modified to be compatible  with the appropriate standard, or explicitly declare their use of [bashisms]("http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29") by explicitly setting the interpreter to bash via the [shebang]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29") line: #!/usr/bin/env bash.*

[http://mywiki.wooledge.org/Bashism](http://mywiki.wooledge.org/Bashism)

---

### Post by sisco311 on 2011-01-04
> **nahallac said:**
> Hello,
 
I have decided that I can no longer be ignorant of scripting and its fundamentals, and I'm going to start with learning Bash. I have found what looks (at first glance) to be a decent tutorial for a beginner: [http://www.ibm.com/developerworks/library/l-bash.html](http://www.ibm.com/developerworks/library/l-bash.html).
 
Does anyone have any other online resources - or even books - that will be of use to me? Bear in mind that I really am terribly ignorant of all things scripting...

That looks like a quiet good guide for beginners. Also check out [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

> **luvshines said:**
> This one is what I refer to time and again.
Simple, perfect and exhaustive

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

Covers advanced topics as well:
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

I don't recommend the *Advanced Bash-Scripting Guide*. Some sections are outdated and the examples are full of bugs.

> **KJ KJ KJ said:**
> Are you aware that Ubuntu uses 'dash' rather than 'bash' by default?

So you'll be puzzled when valid bash scripts don't work with Ubuntu. I'm un-learning bash to suit Ubuntu. 


[http://en.wikipedia.org/wiki/Debian_Almquist_shell](http://en.wikipedia.org/wiki/Debian_Almquist_shell)

*Dash has been the default /bin/sh in [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29") since the 6.10 release in October 2006.[]("http://en.wikipedia.org/wiki/Debian_Almquist_shell#cite_note-4") During the transition by Ubuntu, numerous scripts making use of [Bash]("http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29")-specific functionality (but not declaring it) were discovered.[]("http://en.wikipedia.org/wiki/Debian_Almquist_shell#cite_note-5")[]("http://en.wikipedia.org/wiki/Debian_Almquist_shell#cite_note-6")To avoid errors, Bash-specific scripts can be modified to be compatible  with the appropriate standard, or explicitly declare their use of [bashisms]("http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29") by explicitly setting the interpreter to bash via the [shebang]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29") line: #!/usr/bin/env bash.*

[http://mywiki.wooledge.org/Bashism](http://mywiki.wooledge.org/Bashism)

While it's true that the system shell in Ubuntu is dash, the default interactive shell for users is bash.

---

### Post by nahallac on 2011-01-04
> **KJ KJ KJ said:**
> Are you aware that Ubuntu uses 'dash' rather than 'bash' by default?
 
So you'll be puzzled when valid bash scripts don't work with Ubuntu. I'm un-learning bash to suit Ubuntu. 
 
 
 
No, I must admit I didn't! However Bash seems to be ubiquitous enough that I should be learning it first. And changing the shell used in the script will make it work anyway, yes?

---

### Post by nahallac on 2011-01-04
> **sisco311 said:**
> That looks like a quiet good guide for beginners. Also check out [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) [QUOTE]
 
Thank you, I will have a browse shortly.
 
[QUOTE=luvshines;10316492]This one is what I refer to time and again.
Simple, perfect and exhaustive
 
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

 
I must admit I had a brief look at this but it appeared to be missing the basic explanations I need. I will re-read though as I admit I disregarded it quickly.

---

### Post by KJ KJ KJ on 2011-01-04
> **nahallac said:**
> No, I must admit I didn't! However Bash seems to be ubiquitous enough that I should be learning it first. And changing the shell used in the script will make it work anyway, yes?

Indeed if you change the first line of your scripts to use bash, then you're all set.

It would be confusing to have things work at the interactive prompt but not inside your scripts, which is an easy mistake to make because 'sh' is synonymous with 'bash' for many people.

In a few months' time, when you've become proficient at bash, this will come back to bite you ...

---

