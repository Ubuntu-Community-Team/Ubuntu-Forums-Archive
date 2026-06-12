---
title: "Using a keyboard shortcut to run a shell script"
date: 2010-07-28
forum: General Help
---

### Post by NeoDevin on 2010-07-28
Ubuntu 9.04

I have a bash shell script located at "/home/devin/.Scripts/script"

I want to attach it to a hot key, I go to "System > Preferences > Keyboard Shortcuts", click "Add", Type in a name, and under "Command" I put in "/home/devin/.Scripts/script", and then assign a key to it.

When I press that key, nothing happens...

Any ideas?

Thanks in advance
Devin

---

### Post by blur xc on 2010-07-28
Does your script have executable premissions? Other than that, might be a key bindign conflict, or something...

BM

---

### Post by NeoDevin on 2010-07-28
> **blur xc said:**
> Does your script have executable premissions? Other than that, might be a key bindign conflict, or something...

BM

Thanks for the reply.

I believe it has executable permissions: I can run it from within the terminal with the command "/home/devin/.Scripts/script" and it works as expected.

It doesn't matter what key I bind it to, it still doesn't work.  I tested the each of the keys that I tried by assigning it to "Open Terminal", to make sure that they were being received/processed correctly, and they work there, but when I assign them to run the script, they don't do anything.

---

### Post by prodigy_ on 2010-07-28
What is it supposed to do? If you want a terminal window to appear, your command should be: ```
gnome-terminal -e "bash /home/devin/.Scripts/script"
``` Otherwise it'll be executed silently.

---

### Post by NeoDevin on 2010-07-28
> **prodigy_ said:**
> What is it supposed to do? If you want a terminal window to appear, your command should be: ```
gnome-terminal -e "bash /home/devin/.Scripts/script"
``` Otherwise it'll be executed silently.

I don't need the terminal to (stay) open (the script is to toggle from internal to external display on my laptop).  But apparently using 

```
bash /home/devin/.Scripts/script
```

instead of

```
/home/devin/.Scripts/script
```

in the "Command:" field works correctly.

Thanks for the help!

Devin

---

### Post by vttay03 on 2010-07-28
I know you've figured this out but the script may not have the following located at the top:

```

#!/bin/bash

```

Which is probably why you have to type 'bash script_name' instead of just 'script_name'.  It works when you're already in a terminal because you're in a bash environment which interprets the commands as such.

---

### Post by NeoDevin on 2010-07-28
> **vttay03 said:**
> I know you've figured this out but the script may not have the following located at the top:

```

#!/bin/bash

```

Which is probably why you have to type 'bash script_name' instead of just 'script_name'.  It works when you're already in a terminal because you're in a bash environment which interprets the commands as such.

My script already contains that.  The 'bash' command still seems to be required even with that.

---

### Post by blur xc on 2010-07-28
> **NeoDevin said:**
> My script already contains that.  The 'bash' command still seems to be required even with that.

did you make your script executable?

```
chmod u+x script
```

then it could be run by

```
./script
```

if the script is in your working directory, or

```
/path/to/script
```

if it isn't.

BM

---

