---
title: "Executing a shell script from any directory"
date: 2010-01-20
forum: General Help
---

### Post by Ernir on 2010-01-20
I recently installed Matlab, and as-is, I have to start it by entering the Matlab/bin/ directory, and typing ./matlab to run the shell script there.

I know it is possible to start the program by typing "matlab" regardless of what directory you're in, I have seen it done. But I can't figure out how he did it, and he isn't available right now. Can you help? :)

Thanks in advance.

---

### Post by synapsys on 2010-01-20
```
cd Matlab/bin/
sudo cp matlab /usr/bin/
matlab
```

---

### Post by Ernir on 2010-01-20
Thanks. :D

The last step gives me an error, though.
```
$ matlab
.: 861: Can't open /usr/bin/util/arch.sh
```

Is this something specific to the program, or did I screw something up? :/

---

### Post by SlugSlug on 2010-01-20
sudo rm /usr/bin/matlab

and then 

sudo gedit /usr/local/bin/matlab

paste the following 

#!/bin/bash
[full path to] /Matlab/bin/matlab   maybe ~/Matlab/bin/matlab  ?


save and exit

and finally make it executable

sudo chmod +x /usr/local/bin/matlab

---

### Post by Ernir on 2010-01-20
> **SlugSlug said:**
> sudo rm /usr/bin/matlab

and then 

sudo gedit /usr/local/bin/matlab

paste the following 

#!/bin/bash
[full path to] /Matlab/bin/matlab   maybe ~/Matlab/bin/matlab  ?


save and exit

and finally make it executable

sudo chmod +x /usr/local/bin/matlab

This worked! Whoo! Thanks. \o/

Now, so that I know what I was doing... did this work because /usr/local/bin is in my PATH, and the file I created in there calls bash and tells it to execute [stuff]/Matlab/bin/matlab ? =)

---

### Post by SlugSlug on 2010-01-20
> **Ernir said:**
> This worked! Whoo! Thanks. \o/

Now, so that I know what I was doing... did this work because /usr/local/bin is in my PATH, and the file I created in there calls bash and tells it to execute [stuff]/Matlab/bin/matlab ? =)

sort of.

Firstly you moved the matlab file to /usr/bin -- this moved the exec away from all the files it needs inside /matlab

so what you did was basically make a script that called the matlab exec from /Matlab/bin/matlab 

placed it in /usr/local/bin so when you type matlab it's really typing 
[full path to] /Matlab/bin/matlab

all bash commands are in  /bin /usr/local/bin  and it knows that so you
dnt have to type /bin/ls  in order to execute the ls command
you could have also looked into bash aliases  you could have acheved the same with that.

---

### Post by Ernir on 2010-01-20
OK. Makes sense. Thanks again. :D

---

