---
title: "Bug in Uniq?"
date: 2010-01-21
forum: General Help
---

### Post by Alaric on 2010-01-21
Hello,

I recently found myself in possession of a large file (a few million lines in length) of short strings and would like to count the number of lines that are unique to the file.  I thought this would be an easy process, but while working on the problem, I encountered the following.  Can anyone explain this weird result to me?  

```
alaric@alaric-laptop:~/Documents/Programming$ grep '^string$' file.txt | uniq | wc -l
1
alaric@alaric-laptop:~/Documents/Programming$ uniq file.txt | grep '^string$' | wc -l
59182
```

Why in the world would the order of the commands matter to uniq?

---

### Post by Alaric on 2010-01-21
<Sigh> As usual, problem solved 10 seconds after posting.  

[http://www.opensubscriber.com/message/bug-coreutils@gnu.org/5103253.html](http://www.opensubscriber.com/message/bug-coreutils@gnu.org/5103253.html)

---

