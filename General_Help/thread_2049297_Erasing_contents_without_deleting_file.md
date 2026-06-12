---
title: "Erasing contents without deleting file"
date: 2012-08-28
forum: General Help
---

### Post by RockinsonM on 2012-08-28
I am running Xubuntu on a VM, although I assume this question would relate to all variants, but basically I am having OpenNMS send email locally to my user mailbox, a simple setup where I just check /var/mail/username for the text based messages. The problem is that it becomes a hassle to scroll through all the old messages I don't need anymore and I am looking for a solution. Is there a command I can run from the terminal in order to erase the current contents of my username mailbox without actually erasing the mailbox file itself?

---

### Post by codemaniac on 2012-08-28
the below commandline would erase the contents of a text file .

```
cat /dev/null >  /var/mail/username
```

In combination with the redirection operator (>) colon(":"), also truncates a file to zero length, without changing its permissions. If the file did not previously exist, creates it.

```
: > /var/mail/username
```

---

### Post by zombifier25 on 2012-08-28
EDIT: Ninja'd.

---

### Post by RockinsonM on 2012-08-28
Great thank you for the response. I knew there had to be a simple way to get it done.

---

### Post by Lars Noodén on 2012-08-28
There's also [shred](http://manpages.ubuntu.com/manpages/precise/en/man1/shred.1.html) which will overwrite the contents instead of just erasing them.  Though the above examples are probably what you want.

---

### Post by RockinsonM on 2012-08-28
I just saw a mention of shred when looking up options for the rm command. How would shred be shown to do the same thing? 

I don't think it's necessary in this instance but perhaps for future reference it may be good to know.

---

### Post by Lars Noodén on 2012-08-28
shred fills the space on the disk that the file occupies with binary junk.  It's meant to prevent recovery via forensic tools.  codemaniac's solution gives you an empty file of zero length which is probably what will be useful in your case.

---

