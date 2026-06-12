---
title: "Filter specific text from source code with grep"
date: 2011-02-27
forum: General Help
---

### Post by whiterabbit7500 on 2011-02-27
I'm working on a new conky script, and I had the idea to use text from a [http://www.thefuckingweather.com](http://www.thefuckingweather.com). The command I'm using to pull the file is:
```
curl -s http://www.thefuckingweather.com/?zipcode=33186 | grep 'ITS FKING *'
```

However, this gives me the entire line of code this line appears in.

```
<br />ITS FKCING NICE</div><div  id="remark"><br />
```

How can I limit this to simply the text?

Sorry about the foul language btw...the words obviously aren't misspelled when I enter them in the terminal

---

### Post by rolandrock on 2011-02-27
grep is not very good at editing.  You could try awk or sed. It's not pretty but this might work:

> curl -s [http://www.thefuckingweather.com/?zipcode=33186](http://www.thefuckingweather.com/?zipcode=33186) | sed -n 's/<br \/>\(ITS F.*\)<\/div.*/\1/p'

---

### Post by whiterabbit7500 on 2011-02-27
seems to work perfectly. I'll test it out in the next few days. I knew sed or awk would be the solution, I just don't have the time to sit and learn either :-/

Thank you however, I appreciate it.

---

### Post by rolandrock on 2011-02-28
Best way to learn sed and awk is probably doing what you are doing.  Get an example with a solution and try to figure out what the gobbledygook means.

Good luck anyway.

---

### Post by DaithiF on 2011-02-28
The -o flag tells grep to output only the pattern that matches, not the entire line where the pattern matches. 

so something like this:
```
curl etc... | grep -o "ITS FKCING [^<]*"

```

---

### Post by rolandrock on 2011-02-28
Cool.  Didn't know that.  Thanks.

---

