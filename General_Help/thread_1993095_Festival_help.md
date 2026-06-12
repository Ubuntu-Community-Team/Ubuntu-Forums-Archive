---
title: "Festival help"
date: 2012-06-01
forum: General Help
---

### Post by gardengxc on 2012-06-01
Trying to use text2wav on an E book I downloaded, however I get an error every time I try. 
```
*****@*****scomp:~$ cd Desktop
*****@*****scomp:~/Desktop$ cd MAOCT
*****@*****scomp:~/Desktop/MAOCT$ cat 01|sed 's/[^a-zA-Z 0-9 .,!?]//g'|text2wave -o 01.wav
CLUNITS: no predicted class for ngonset
*****@*****scomp:~/Desktop/MAOCT$ cat 02|sed 's/[^a-zA-Z 0-9 .,!?]//g'|text2wave -o 02.wav
CLUNITS: no predicted class for ngonset
*****@*****scomp:~/Desktop/MAOCT$ cat 03|sed 's/[^a-zA-Z 0-9 .,!?]//g'|text2wave -o 03.wav
CLUNITS: no predicted class for ngonset
*****@*****scomp:~/Desktop/MAOCT$ cat 04|sed 's/[^a-zA-Z 0-9 .,!?]//g'|text2wave -o 04.wav
CLUNITS: no predicted class for ngonset
```

Other documents work fine. So could someone tell me what's going wrong when it says ```
CLUNITS: no predicted class for ngonset
```

---

### Post by gardengxc on 2012-06-13
bump

---

### Post by neu2buntu on 2012-06-13
perhaps install the application ```
espeak
``` . it is capable of doing what you require ;)

---

### Post by gardengxc on 2012-06-25
OK I removed every character that wasn't a number letter of punctuation. That has fixed it.

---

