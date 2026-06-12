---
title: "Python running as a process in Ubuntu?"
date: 2012-07-31
forum: General Help
---

### Post by eazar001 on 2012-07-31
Hi, I apologize if this is a ridiculous question, but:

When running:

ps ax | grep "python", I see....

 1632 ?        S      0:00 python /usr/share/system-config-printer/applet.py
 1873 ?        S      0:00 /usr/bin/python /usr/sbin/aptd
---------------------------------------------------------------

This is just a simple question, not a problem, but why is python running as a process in the background? Is this essential for the OS? It appears as if the printer is dependent on it? Link to CUPS? I know it looks obvious, but a little enlightenment would help. This process always runs after reboot. Thanks in advance.

---

### Post by vancouverite on 2012-07-31
The python interpreter is running the programs listed after the name python, in the first case it's an applet related to the printer configuration, and in the second case, it's aptd (a part of the package management system, apt [http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)).

The critical thing is that Python is a language, and the python interpreter is a program that executes code written in python. Many linux programs and system tools are written in python and are executed using the command: "python [insert path to program]", or, if the programmer had reason to do so, they may specify the exact location of the python interpreter using "/usr/bin/python [program path]". In Ubuntu these are equivalent. This will then show up in ps as "python [program path]" or "/usr/bin/python [program path]". Putting "python" or "/usr/bin/python" in the command tells the OS what interpreter to use.  There are lots of interpreted languages, like bash, ksh, tcl, and more. To run tcl code you may use the command "tcl [program name]" or "/usr/bin/tcl [program name]".

In the case of the two programs you are seeing, I do not think they are malicious and they would likely be restarted by the system after a reboot.

If you do see a program that you don't like you can terminate it using its PID (*P*rocess *ID*entification) along with the command "kill".  For example, if you have firefox running and it freezes, do a search for it using ps and then issue the command "kill [insert firefox PID]" to end the process.  Type "man kill" into the terminal for more information. Another useful one is "killall", but watch out for that one as it terminates processes based on their name (eg "killall firefox") and can terminate some stuff that will make you have to hard reboot (or issue the REISUB command...google it).

---

### Post by eazar001 on 2012-07-31
> **vancouverite said:**
> The python interpreter is running the programs listed after the name python, in the first case it's an applet related to the printer configuration, and in the second case, it's aptd (a part of the package management system, apt [http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)).

The critical thing is that Python is a language, and the python interpreter is a program that executes code written in python. Many linux programs and system tools are written in python and are executed using the command: "python [insert path to program]", or, if the programmer had reason to do so, they may specify the exact location of the python interpreter using "/usr/bin/python [program path]". In Ubuntu these are equivalent. This will then show up in ps as "python [program path]" or "/usr/bin/python [program path]". Putting "python" or "/usr/bin/python" in the command tells the OS what interpreter to use.  There are lots of interpreted languages, like bash, ksh, tcl, and more. To run tcl code you may use the command "tcl [program name]" or "/usr/bin/tcl [program name]".

In the case of the two programs you are seeing, I do not think they are malicious and they would likely be restarted by the system after a reboot.

If you do see a program that you don't like you can terminate it using its PID (*P*rocess *ID*entification) along with the command "kill".  For example, if you have firefox running and it freezes, do a search for it using ps and then issue the command "kill [insert firefox PID]" to end the process.  Type "man kill" into the terminal for more information. Another useful one is "killall", but watch out for that one as it terminates processes based on their name (eg "killall firefox") and can terminate some stuff that will make you have to hard reboot (or issue the REISUB command...google it).

I see, thank you very much. I am kind of a newbie to Linux, and have written scripts in python before, I just had no idea it was linked to aptitude and printer configurations in Ubuntu. I just wanted to make sure this was a normal thing. Thanks again, I appreciate the prompt response.

---

