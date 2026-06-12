---
title: "How to make a script ?"
date: 2010-12-20
forum: General Help
---

### Post by kanishkdudeja on 2010-12-20
i need to make a script..

its basically a cleanup script which will clean all my trash folders..

n run

apt-get clean
apt-get autoclean
apt-get autoremove..

how can i do so ?

---

### Post by CheetoBandito on 2010-12-20
Create a file with those three commands that you want to run in it.  Place this line at the top of the file

#!/bin/bash

and then save the file and give it execute permissions.  The line you put at the top is telling the computer that the bash interpreter should be used to process the file.

---

### Post by skillet-thief on 2010-12-20
Make a text file with those commands as its contents, call it clean.sh.

```
apt-get clean
apt-get autoclean
apt-get autoremove

```

Then, when you are ready to run it, you just type: 
```
sudo bash clean.sh
```

If you want to get fancy,  you can include the shebang:

```

#!/bin/bash

apt-get clean
apt-get autoclean
apt-get autoremove

```

Then you have to make your script executable (chown +x clean.sh), and  then you can just type:

```
$ sudo ./clean.sh
```

---

### Post by kanishkdudeja on 2010-12-20
okay..thanks..

but if i run these commands in the terminal..

it asks for the password..

how do i enter the password in this script ?

or if the commands require any default input how can that input be stored in the script ?

---

### Post by CheetoBandito on 2010-12-20
It is a little more tricky to answer the password within the script.  However, for this implementation you can just call the script with sudo:

```
sudo myscript.sh
```

---

### Post by kanishkdudeja on 2010-12-20
okay..

but if the commands require any other input..

like press y for yes or n for no..

how can this be possible ?

---

### Post by CheetoBandito on 2010-12-20
You need a supplemental tool to accomplish this.  I personally like expect:
[http://en.wikipedia.org/wiki/Expect](http://en.wikipedia.org/wiki/Expect)

Basically you'll have to invoke expect within your script to expect a question and return the appropriate response.

---

### Post by kanishkdudeja on 2010-12-20
oh okay..thanks a lot mate..:)

---

### Post by colobix on 2010-12-20
> **skillet-thief said:**
> Make a text file with those commands as its contents, call it clean.sh.

```
apt-get clean
apt-get autoclean
apt-get autoremove

```

Then, when you are ready to run it, you just type: 
```
sudo bash clean.sh
```

If you want to get fancy,  you can include the shebang:

```

#!/bin/bash

apt-get clean
apt-get autoclean
apt-get autoremove

```

Then you have to make your script executable (chown +x clean.sh), and  then you can just type:

```
$ sudo ./clean.sh
```

Or a much easier way:

Create a new document, call it clean.
Open it and type in these 4 lines:

#!/bash
apt-get clean
apt-get autoclean
apt-get autoremove

Save the file and make it executable and, move it to /usr/bin Now open up the ALT+F2 command and type in clean and hit enter.
You can now add this script as a startup process if you wish to.

---

### Post by kanishkdudeja on 2010-12-20
thanks guys..:)

---

### Post by efflandt on 2010-12-20
Standard input and output would still be the terminal you are running it from, so you would be prompted just like if you ran the individual commands.  If you want to totally automate response to prompts, you could use **-y** switch for those commands to assume **yes**.

Or you could install **expect** (or **expect-lite**) if you want to automate different responses to different situations.  Then see man pages for those.

Note that it is a good idea to put your scripts in one place, so you can run them without requiring a path.  If you create a **bin** directory in your home ( **mkdir ~/bin** ) the next time you login, that will automatically be included in your PATH.  Then you could make a panel or desktop launcher as "Application in Terminal" to run your script with a click or double click of the mouse.

---

### Post by kanishkdudeja on 2010-12-20
okay. Thanks :)

---

### Post by Spyderkid on 2010-12-20
put 

#!/bin/bash 




at the beggining then you cann add in 

&& - inbetween commands which means the last must have been successful to continue

|| -  inbetween commands which means the last must failed to continue

---

