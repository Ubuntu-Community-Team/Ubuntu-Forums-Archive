---
title: "Create shortcut one for a program and one for a service"
date: 2009-10-24
forum: General Help
---

### Post by ASTRAPI on 2009-10-24
Hello

How can i create a shortcut in the desktop so i don't have to type those 2 commands always in the terminal?

command one:

> sudo /etc/init.d/wicd start

command two: 

> sudo msnshadow

Thank you

---

### Post by blwizard on 2009-10-24
> **ASTRAPI said:**
> Hello

How can i create a shortcut in the desktop so i don't have to type those 2 commands always in the terminal?

command one:



command two: 



Thank you

1. Create a bash script file and put the stuff u wanna run in it.
   a script file starts with #!/bin/bash on the top line
2. add execute permision to the bash script.
   chmod +x filename
3. put it on your desktop.

---

### Post by blwizard on 2009-10-24
or i think the 'normal' way is just creating a desktop launcher.

---

### Post by barthel on 2009-10-24
I'd create a custom launcher, but use `gksudo` instead of `sudo` to prompt for the password (since you won't be in an interactive terminal).

I'm assuming that the issue is having to use the terminal. If the issue is only the typing involved, you could add an alias to ~/.bashrc to minimize the number of keystrokes required.

BTW, if you're simply creating a script to launch another application, you can probably get away with using `#!/bin/sh` instead of `#!/bin/bash` and reduce the overhead. Also, you might want to consider forking the process with ampersand (&) so the shell doesn't have to wait for the launched program to exit.

---

