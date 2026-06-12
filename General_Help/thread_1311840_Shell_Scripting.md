---
title: "Shell Scripting"
date: 2009-11-02
forum: General Help
---

### Post by mem0rex on 2009-11-02
I made a shell script and I changed the chmod, then I typed ./[x.sh] and I get permission denied. Can anyone help me with this error?

bash: ./test.sh: Permission denied

---

### Post by lavinog on 2009-11-02
what did you chmod it to and who is the owner?
```
ls -l x.sh
```

what does the script do?

does executing the script like this work?
```
bash x.sh
```
does it have a header to say it is a script?
```
#!/bin/bash
```

can you post the script?

---

### Post by t0p on 2009-11-02
If you did the chmod like this:

```
chmod +x script.sh
```

the script ought to run.  Is that what you did?

---

### Post by mem0rex on 2009-11-02
bash file.sh worked, 
why do i have to type bash first?

---

### Post by lavinog on 2009-11-02
> **mem0rex said:**
> bash file.sh worked, 
why do i have to type bash first?

you probably didn't have the magic header or "sha-bang"

the first line in your script should be:
```

#!/bin/bash

```

---

