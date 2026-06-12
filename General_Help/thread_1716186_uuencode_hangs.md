---
title: "uuencode hangs"
date: 2011-03-28
forum: General Help
---

### Post by olivo on 2011-03-28
Dear All, 
I installed uuencode and uudecode (sudo apt-get install mpack) 

I cannot understand why uuencode hangs after printing the first line:
begin 644 filename


Any help?
thanks 
Olivo

---

### Post by andrew.46 on 2011-03-28
Can you give the full commandline you have used?

Andrew

---

### Post by olivo on 2011-03-28
I simply used 
uuencode file.txt

---

### Post by andrew.46 on 2011-03-28
Try:

```

uuencode file.txt file.txt > test.uue

```

Andrew

---

### Post by olivo on 2011-03-28
works fine. thanks.

---

### Post by andrew.46 on 2011-03-28
Good news :)

---

