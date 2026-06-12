---
title: "Prevent search in executing folder"
date: 2012-04-19
forum: General Help
---

### Post by Tr4ffic on 2012-04-19
hi, 

I'm going to try and explain my predicament here. 

I have the program rdesktop which is executed by way of  a script run by another program. That script is located in the same folder as the rdesktop executable is (/usr/bin) and the program. It is not possible for me in any way to modify the script or the executables. 

I have to add an option to the rdesktop command that is executed by the script. I was reasoning that the script used the path variable to locate the command so i modified the PATH variable so it would point to a script i wrote myself which :

#!/bin/bash

/usr/bin/rdesktop -N "$@" 


Now when i execute it, it doesn't use the -N argument. Apparently when you call a script or program from another script or program that are in the same folder they circumnavigate the PATH variable.

I hope I explained it properly.

Is there anyone that can help me ?

---

### Post by papibe on 2012-04-19
Hi Tr4ffic. Welcome to the forums!

If you have a script with the same name as an installed application, when you 'just' run it by its name, always the system app will be called.

That is because to execute a command the system looks at a environment variable called PATH that set the rules not only where to look, but also in what order.

These is a simple solution for personal use:
[LIST]
[*]Unmodify the PATH, so it's the same as before.
[*]Create a bin directory under your home (~/bin).
[*]Move your script to ~/bin
[/LIST]
For all new terminals, your the directory ~/bin will be inserted at the beginning of the PATH, so anything there will be run first (restart your machine if you want the change to take effect for all the environment).

I hope that helps, and tell us how it goes.
Regards.

---

### Post by Tr4ffic on 2012-04-20
Hi,

Thank you for the quick response. 

I have tried your way but i still keep having the same problem. 

The program which calls the script is 

hptc-control-center ( hp thin client control center)

The program script is  

*/usr/bin/rdesktop_wrapper.sh*
              
the rules in the script are:

[I]case &1 in 
    start) 
           /usr/bin/SetCursorOnRightScreen.sh
           eval "rdesktop $OPTIONS ${ADDRESS}:${PORT}"
           exit $?
           ;;
    *) usage ;;
esac;[/I]

( i have tried using eval in another script that called my rdesktop script and it worked with my added options)

The program used in the script 

*rdesktop *


I have created a script in the user directory 
*/home/user/bin/rdesktop *
It contains the following rules

[I]#!/bin/bash

/usr/bin/rdesktop -N -a 8 -k be-wincompat "$@"[/I]

Now whenever I execute a rdesktop command it correctly uses the options is specified in the /home/user/bin/rdesktop file.

However when I make an rdp connection from the hptc-control-center it still uses the original rdesktop command without my options added to it.

Thx in advance

---

