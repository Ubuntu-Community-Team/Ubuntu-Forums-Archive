---
title: "Error in terminal"
date: 2010-12-22
forum: General Help
---

### Post by karthick87 on 2010-12-22
When i open terminal,i can find these two lines there..
```

bash: /etc/bash_completion.d/lvm.backup: line 172: syntax error near unexpected token `newline' 
bash: /etc/bash_completion.d/lvm.backup: line 172: `        --metadatacopie' 
karthick@LinuxBox:~$  
 
```How to get rid of those errors???

---

### Post by karmila on 2010-12-22
Hmm why i don't have that file at my /etc/bash_completion.d. I only have lvm no lvm.backup. did you make it yourself?

Try to move that file to somewhere else (e.g. desktop).

---

### Post by MooPi on 2010-12-22
Here is my /etc/bash_completion.d/lvm 
Hope a clean copy helps.

---

### Post by karthick87 on 2010-12-22
That helped me..Thanks a lot MooPi :)

---

