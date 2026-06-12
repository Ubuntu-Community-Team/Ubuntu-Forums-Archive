---
title: "auto executable .sh file"
date: 2010-11-21
forum: General Help
---

### Post by bitttttor on 2010-11-21
Hi All,

I've been checking the posts on how to make a bash file executable and most of the answers point to either right click + permissions  or chmod a+x /path/script.sh in the terminal.

Is possible to make this within the script? I'm writing a Processing applet that produces and executes .sh files automatically, so I can't change this manually each time.

Any simple way to do this?

Thanks

---

### Post by luvshines on 2010-11-21
Do you mean that the script is produced at runtime and is then being executed ??
If that is the case, then you can add the chmod thing before you execute the script.

---

### Post by papibe on 2010-11-21
> **bitttttor said:**
> 
... I'm writing a Processing applet that...

Which language/tool are you using to write it? If you have access to system calls you can run "chmod a+x yourfile" before running it.

Also, there's a way to execute a script within a file without adding permission to it:
```
$ bash your_file_with_bash_code
```

Regards.

---

### Post by amauk on 2010-11-21
You mean something like this
```
#!/bin/sh

FOO=2

echo "
echo \"Hello,\"
echo \"this is a dynamically generated shell script\"
echo \"FOO = $FOO\"
" | /bin/sh
```

---

### Post by bitttttor on 2010-11-21
Hi, 

I'm working in [processing]("http://processing.org/"). The applet that I have writes a script that executes some commands for other software. The problem is that after writing the script, if with the same applet I try to open it with a command (open() in this case) the script opens in gedit. I don't think processing has system calls...  maybe I have to change the approach.

---

### Post by bitttttor on 2010-11-21
> **luvshines said:**
> add the chmod thing before you execute the script.


the problem is I'm producing the .sh files in processing, so I don't know if I can execute a chmod from there.

---

### Post by papibe on 2010-11-22
Did you try running "/bin/bash my_file" as in post 3?

---

### Post by bitttttor on 2010-11-22
> **papibe said:**
> Did you try running "/bin/bash my_file" as in post 3?


Hi, not sure if I'm doing it right. I've tried this:

```
open(bin/bash/my_file.sh);
```and

```
open($/bash/my_file.sh);
```and

```
open(home/me/Desktop/my_file.sh);
```(please tell me if this is what you meant)

Also I made a launcher that starts the script with double click but I can't open it with the open() method!!! I can open any file with this, but the .sh opens either on a text editor or just doesn't open (even if they have permission).

I'm thinking on writing another small applet so when I open() that, it should start the script, but I may be missing something important and I may get the same result...

---

### Post by papibe on 2010-11-22
It should be something like:
```
open(/bin/bash my_file.sh);
```
or
```
open("/bin/bash my_file.sh");
```

---

### Post by bitttttor on 2010-11-22
> **papibe said:**
> 
```
open("/bin/bash my_file.sh");
```

This one should be (no syntax error because of the "" ) but nothing happens.

---

### Post by The Cog on 2010-11-22
Do you know the name of the file in advance? If it's a constant, perhaps you could create an executable script that runs the script that you write.

Another thing you could try is to manually create an executable file with the name of the script you're going to create. That way, after being overwritten, it should still be executable.

---

### Post by bitttttor on 2010-11-22
Thanks Papibe and The Cog,

It was a problem within the processing script. After a [suggestion]("http://forum.processing.org/#Topic/25080000000418160") I changed the open() method to exec() form the java Runtime class and finally worked.

The problem of the executable file was solved with overwriting: 

> **The Cog said:**
> manually create an executable file with the name of the script you're going to create. That way, after being overwritten, it should still be executable.


Cheers !!!

---

