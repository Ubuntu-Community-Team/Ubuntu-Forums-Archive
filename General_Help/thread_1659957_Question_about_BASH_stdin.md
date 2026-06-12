---
title: "Question about BASH stdin"
date: 2011-01-04
forum: General Help
---

### Post by wpcarro on 2011-01-04
Does anyone know how many bytes the Standard Input buffer on the BASH can hold at one time? I'm not sure whether or not this question is shell-specific, but I thought I'd specify anyway. I've tried searching elsewhere but cannot seem to find the answer or anything close to it for that matter. If anyone knows the answer or can point me in the right direction I'd appreciate it greatly.

Thanks

---

### Post by hawkmage on 2011-01-04
What are you trying to do?  I have piped very large amounts (10s of gigs) of info from one command into another via stdout/stdin without any issue.

---

### Post by wpcarro on 2011-01-04
Oh, I guess I just wanted to know for the sake of knowing. I'm experimenting with different implementations of a getline function that reads from  stdin and stores the contents into an array, so I was just playing around with various sizes for that array.

---

