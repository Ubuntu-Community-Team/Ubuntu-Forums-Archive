---
title: "can't kill firefox-bin"
date: 2011-05-13
forum: General Help
---

### Post by someitalian123 on 2011-05-13
I have this problem where I keep losing internet and the only way to fix is to restart the computer, I think it's because my wifi card isn't completely compatible with ndiswrapper. Anyways when ever this happens I am unable to shutdown properly because ubuntu says firefox-bin is still running, when I try to shutdown it just hangs. I tried killing firefox-bin with the system monitor but that didn't work, then I tried killing it the terminal by using killall -9 firefox-bin. This too doesn't work. How can I kill firefox-bin?

---

### Post by bchurchill on 2011-05-13
If an application received a signal 9 with sufficient privileges it should terminate no matter what, so the question is "why didn't firefox-bin receive a signal 9?".

It seems there are three possibilities:
1) killall never sent the signal.  I typically use pkill or kill, so I don't really know killall that well, but the manpage seems to suggest that to send a signal you should use the "-9" command.
2) killall was underprivileged.  I hope that you're not running firefox as root... typically this shouldn't be an issue if both processes are running at the same level.  You could run 'sudo killall' and that would guarantee that this is not an issue.
3) something is wrong deep down inside, and the signal didn't kill the process.  This seems unlikely.

I don't know what more you've tried since your last post.  Any further thoughts?  Is this problem reproducible?

---

### Post by someitalian123 on 2011-05-13
It happens kind of randomly I been trying to reproduce it but it isn't happening. It usally happens at the most inconvenient time. I'm pretty sure I have tried using sudo in the past.

---

### Post by someitalian123 on 2011-05-14
OK I was able to reproduce the problem. When I used sudo it didn't ask for my password and I wouldn't allow to type in more commands so I had to close out the terminal and open another one. So apparently when this happens sudo is unusable.  kill -9 firefox-bin gave me this error

bash: kill: firefox-bin: arguments must be process or job IDs

And pkill  -9 firefox-bin did absolutely nothing. same as killall -9 firefox-bin

> 3) something is wrong deep down inside, and the signal didn't kill the process.  This seems unlikely.I'm pretty sure something is wrong deep inside. What should I do. This problem with losing internet is driving me crazy, and I would like to fix it but every time I search for an answer I can't find anything, all I can find is a guide to setting up my card with ndiswrapper and that is absolutely no help because I've tried it. I feel like I'm the only person having this problem and it's driving me crazy.

---

### Post by Flugz on 2011-05-14
Aye, using kill you should use the PID of the process you would like to end, so no wonder you will get an error from bash.
```

ps aux | grep firefox-bin

```Should give you the info about the process you would like to kill, in your case I presume that would be firefox-bin
```

kill -9 [PID]

```Where PID is the job number, inserted without the brackets.

---

### Post by someitalian123 on 2011-05-14
Well I'll try to reproduce the problem again, but why isn't sudo working. Why I'm I losing internet in the first place. Apparently my hardware is suppose to be compatible with ndiswrapper since no one else is having this problem.

---

### Post by someitalian123 on 2011-05-14
Ok I've tried it again this time using kill properly and it still doesn't work. As I said sudo is unusable because it hangs at the terminal when I try to use it, will someone please tell me what I should do now.

---

### Post by someitalian123 on 2011-05-14
It just happened again, can someone please tell why this is happening and how can I kill firefox-bin.

---

