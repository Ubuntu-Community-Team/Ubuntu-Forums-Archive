---
title: "Some minor, but annoying glitches"
date: 2009-11-05
forum: General Help
---

### Post by Soundler on 2009-11-05
Hi everyone,

So I got more glitches. 
1. Facebook page won't load at all
2. I can't sign in on Youtube
3. Gmail page won't load at all as well

Any suggestions ? :popcorn:

And yes - I have Flash and Java installed.

Running Ubuntu 9.04

---

### Post by x C0MMAND0 x on 2009-11-05
What browser are you using?  Do other pages load?  Can you ping those websites from terminal? 
Example:
```
ping facebook.com
```

---

### Post by wojox on 2009-11-05
[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by abcuser on 2009-11-05
You maybe installed some extensions or changed some settings.

I suggest to create new profile, execute:
firefox -P
from terminal and check if web pages are working with new profile. If they do, then there is some problem with Firefox settings/plugins.

You can then delete created profile, to take you to the old, no profile starting Firefox.

---

### Post by undecim on 2009-11-05
Can you try this on another browser? (such as epiphany)

And also from a different internet connection if possible.

---

### Post by Soundler on 2009-11-05
> **x C0MMAND0 x said:**
> What browser are you using?  Do other pages load?  Can you ping those websites from terminal? 
Example:
```
ping facebook.com
```

I'm using Firefox. There's some ping from Facebook. Still.. can't sign in

---

### Post by Soundler on 2009-11-05
> **abcuser said:**
> You maybe installed some extensions or changed some settings.

I suggest to create new profile, execute:
firefox -P
from terminal and check if web pages are working with new profile. If they do, then there is some problem with Firefox settings/plugins.

You can then delete created profile, to take you to the old, no profile starting Firefox.

Created a new one. That didn't help :(
What do you mean by 'to take you to the old' ?

---

### Post by Soundler on 2009-11-05
> **wojox said:**
> [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

Tried some of the suggested solutions. Didn't help either :(

---

### Post by Soundler on 2009-11-05
Problem solved ! Had to configure my proxy settings. It's pretty weird though because I was able to access other pages. Thanks for the help! :lolflag:

---

