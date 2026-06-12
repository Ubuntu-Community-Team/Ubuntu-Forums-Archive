---
title: "piping command output into grep as search term."
date: 2010-11-11
forum: General Help
---

### Post by voltaic on 2010-11-11
I feel a bit silly asking this, and I have spent the last hour trying to figure it out, and I just can't figure out a way to do this;

I want to pipe the output of a command into grep as the search TERM, rather than the text to be searched, like this for example

```

cat /var/log/auth.log | grep date "&b &d"

```

so that I only see the lines in auth.log for the current day...

but obviously that line doesn't work.... is there a way to do this with grep, or even another command? 

Thanks,
Daniel

---

### Post by squaregoldfish on 2010-11-11
You need to enclose your date command in backquote characters. This will force the command to be run and then passed into grep:

```
cat /var/log/auth.log | grep `date "&b &d"`
```

Steve.

---

### Post by sisco311 on 2010-11-11
Yep, you have to use command substitution, see:
```
man bash | less +/"Command Substitution"
```

and you don't need the pipe:
```
grep "$(date +"%b %d")" /var/log/auth.log
```

---

### Post by voltaic on 2010-11-11
thanks a million to both of you, i knew it was something simple that I was overlooking...

---

### Post by sisco311 on 2010-11-11
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" menu, then "Mark this thread as Solved".

Thanks.

---

