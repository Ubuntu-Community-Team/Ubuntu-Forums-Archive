---
title: "Unable to complete update - repo down?"
date: 2010-08-09
forum: General Help
---

### Post by bobnutfield on 2010-08-09
Hello Everyone,

Normal updates working OK, but have been unable to complete the process with a failed update to Software Center:

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_2.0.6_all.deb
  404  Not Found
```

Anyone else experience this?  Is there another repo available to complete this?  I am using GB servers.

Thanks for any replies.

---

### Post by drs305 on 2010-08-09
The repository above works for me. I also tried changing "gb" to "us" in your error message and it also worked. Otherwise, you could try changing servers in Synaptic or Software Sources via Settings > Repository.

---

### Post by inameiname on 2010-08-09
Sometimes that just happens, for instance if there is a slight pause in the system or something, or the servers froze for half a second or something. Try it again and see if it works. Or, if it still won't, just do what drs305 mentioned.

---

### Post by bobnutfield on 2010-08-09
Thank you for the replies.  Solved it by updating via apt on the command line.  Just never experienced that before.  All OK now.

---

