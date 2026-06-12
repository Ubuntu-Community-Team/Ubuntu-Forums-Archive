---
title: "Adding program to path"
date: 2012-01-13
forum: General Help
---

### Post by Raff1 on 2012-01-13
Hello! I have currently installed a number of programs like Matlab and Maple and am currently trying to add those to path somehow, so I can run them with Alt+F2 and the program name.

I created a folder ~/bin and put the following files there:
A symbolic link to /pathToMaple15/bin/xmaple called maple,
where xmaple:
 ```

#!/bin/sh

# Copyright (c) 1993-2010 by Maplesoft, bla bla bla....

# This script runs Maple with the Java interface.
MAPLE='/pathToMaple15'
export MAPLE 

"${MAPLE}/bin/maple" -x "$@"

```and a script called matlab:
 ```

cd ~/Software/MATLAB_R2011a/; ./bin/matlab

```Running (with Alt+F2; or Double-click + "Run") works with "maple" but not with "matlab". Double-click + "Run in Terminal" works for "matlab".

I don't know how to modify the file "matlab" so that the terminal session stays open, or so the file is executed similarly to the "xmaple" file so it is independent of the terminal. I would very much like to know how to do it both ways.

Also, if I wished these programs to be exectuable for all users, where does it make most sense to put the files/scripts? /bin or /user/bin? (Are these even added to my PATH by default?)

Regards, Raff1

---

### Post by forestG on 2012-03-12
One solution would be to to go to your home directory and open the .bashrc file

then at the end you can add the lines

PATH=PATH=/path/to/your/dir:$PATH
export PATH

The dir that you are put there should contain no other directories. Therefore you should create links to your programs that you want to use. To see how to create links type in google "linux how to create hard links". 

If you want the changes to affect all the users and not only you you can put the lines in the file /etc/profile (you need sudo privileges) instead of the .bashrc file.

---

