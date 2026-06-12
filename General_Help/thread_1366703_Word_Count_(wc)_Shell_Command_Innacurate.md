---
title: "Word Count (wc) Shell Command Innacurate"
date: 2009-12-28
forum: General Help
---

### Post by bradley002 on 2009-12-28
Hello, I need to submit a writing sample at least 500 words in length, so I am trying to use the shell command wc to conveniently count different documents. The problem is that the word counts using shell are inflated about 20% beyond the actual number of words. I tested this in open office and verified it with an online word counter. What is happening here?

Thanks.

---

### Post by synapsys on 2009-12-28
It's probably counting the carriage return at the end of the line as a character.

Why don't you use the word counter in open office? I believe it's under 'properties' or something.

---

### Post by bradley002 on 2009-12-28
I did use it, but I want to quickly perform word counts for a large folder full of documents so I can select only those that are greater than 500 words. 

Words, not characters. Even if it included the carriage return as a character, that would not produce a 20% increase in character count. I am seeing like 660 words when it should be 550.

---

### Post by bradley002 on 2009-12-28
No other theories?

---

### Post by dcstar on 2009-12-28
> **bradley002 said:**
> Hello, I need to submit a writing sample at least 500 words in length, so I am trying to use the shell command wc to conveniently count different documents. The problem is that the word counts using shell are inflated about 20% beyond the actual number of words. I tested this in open office and verified it with an online word counter. What is happening here?

Thanks.

"Documents" created by word processing programs contain far more than just the words you type. Tools like wc assume pure text files which these are not.

---

### Post by KiLaHuRtZ on 2009-12-28
Try the 'w' flag?

```
 cat FILE | wc -w
```

---

### Post by bradley002 on 2009-12-28
> **dcstar said:**
> "Documents" created by word processing programs contain far more than just the words you type. Tools like wc assume pure text files which these are not.

Hm, okay - so there is no way to use shell commands for my goal? The "w" flag gives the same number, just isolated.

---

### Post by dcstar on 2009-12-28
> **bradley002 said:**
> Hm, okay - so there is no way to use shell commands for my goal? The "w" flag gives the same number, just isolated.

There is no way tools designed for text files will work correctly with non-text files.

You would have to convert your word processing files to plain text files and then it would work.

---

### Post by bradley002 on 2009-12-28
thanks - as a rough method I will just apply a fixed ratio to all of the results of the word counts and then double check my potential candidates

---

