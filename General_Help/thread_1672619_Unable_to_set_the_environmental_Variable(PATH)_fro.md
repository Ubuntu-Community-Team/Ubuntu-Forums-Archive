---
title: "Unable to set the environmental Variable(PATH) from the SCRIPT"
date: 2011-01-21
forum: General Help
---

### Post by vicky6528 on 2011-01-21
HI Everyone, 

I am Just trying to set the Environmental variable using a script file and my code is as follows:

#!/bin/bash

echo $PATH
PATH=${PATH}:/opt/bin
export PATH
echo Environmental Variable path is Set
echo $PATH

When I am running the above script, from the last line "echo $PATH" I am getting that /opt/bin has been appended to the PATH but again when I am typing echo $PATH in the terminal I am not getting the newly appended path. Can some one help me to get the solution for the same. It is very Urgent fro me


Regards,
Zafar

---

### Post by RegUB on 2011-01-21
Zafar,

Instead of running the script, type a dot and a space before the script name, and it should do what you want.

e.g. if your script is called "setv", type as below -

. setv

---

### Post by vicky6528 on 2011-01-21
Thanks for the Reply Buddy.

It is working fine when I am running directly the shell script, but I need to provide the shell inside a .deb file so that when one will install the ,deb package automatically the Environmental variable(PATH) will be set. Is there any way to do the same.

Thanks in advance.


Regards,
Zafar

---

### Post by RegUB on 2011-01-21
I'm not sure I understand what you're doing - is your script installing the .deb file? If so, then the environment variables you have set in the script will remain in force for the duration of the script, but will be lost when the script exits. This is because the script runs in its own shell.

---

