---
title: "compiz setting problem - reflection"
date: 2009-12-12
forum: General Help
---

### Post by bryncoles on 2009-12-12
Greetings, the Internet.

Today, in my infinite wisdom, I decided to mess with *Things Man Was Not Meant To Know* (compiz settings). I turned on the 'reflection' setting, and now my laptop wont respond to anything but the power key!

So, what I'd like to know is 

a) how do I change the setting back (turn off reflection) from the live cd

or b) how do i boot into the command line and change the setting?

I'd appreciate the idiots version of how to fix my computer, if that's ok with you guys, but what ever helps me resolve the problem is fine!

Cheers guys, awaiting your feedback!

---

### Post by bryncoles on 2009-12-12
I have a habit of doing this.... I post for help and then solve my own problem! 

Thanks to everyone - especially me! :)

I found the solution [here]("http://www.linuxforums.org/forum/ubuntu-help/116239-how-earth-do-you-reset-compiz-defaults-command-line.html"). I logged into recovery mode, and selected boot as normal. This took me to the command prompt. then, I typed 

```
gconftool-2 --recursive-unset /apps/compiz
```rebooted and it was fine! though I have to set my compiz settings again now... Lets hope I don't play with *Things Man Was Not Meant To Know* again!

---

### Post by stinkeye on 2009-12-13
> **bryncoles said:**
> I have a habit of doing this.... I post for help and then solve my own problem! 

Thanks to everyone - especially me! :)

I found the solution [here]("http://www.linuxforums.org/forum/ubuntu-help/116239-how-earth-do-you-reset-compiz-defaults-command-line.html"). I logged into recovery mode, and selected boot as normal. This took me to the command prompt. then, I typed 

```
gconftool-2 --recursive-unset /apps/compiz
```rebooted and it was fine! though I have to set my compiz settings again now... Lets hope I don't play with *Things Man Was Not Meant To Know* again!
Does that command disable compiz or just disable the plugins.
Thanks.

---

### Post by amadeus266 on 2010-05-18
Did the same thing this morning. Thanks for the post. I would have pulled my hair out trying to fix it otherwise.

---

