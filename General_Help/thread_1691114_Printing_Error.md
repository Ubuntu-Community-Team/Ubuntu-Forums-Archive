---
title: "Printing Error"
date: 2011-02-19
forum: General Help
---

### Post by ashton3553 on 2011-02-19
Hello,

I am trying to get a printing script to work to eventually automatically print documents remotely via dropbox.  I have my printer installed on the computer(its actually a network printer) but anything I print manually works fine, test page, open office doc etc.  But anything my script tries to print gets added to the printing spool process and says completed but never actually prints.  I have no idea whats up any help would be apperciated

print script that seems to works
```

#!/bin/bash
export PrintQueue="/home/bobby/Dropbox/Print";
IFS=$'
'
for PrintFile in $(/bin/ls -1 ${PrintQueue}) 
do
 lpr -r ${PrintQueue}/${PrintFile};
done

```

Printer is a Canon MX870

---

