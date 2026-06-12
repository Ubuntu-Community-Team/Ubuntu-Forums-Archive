---
title: "bash Command"
date: 2012-06-07
forum: General Help
---

### Post by Quarkrad on 2012-06-07
Newbie running 12.04.  I've started playing with conky and have a working script - following a begineers thread.  Created a file in Home called .startconky that contains instructions to autostart conky.  In Startup Applications no matter what I input as the command (.startconky) I could not get conky to autostart - or run it via the Terminal.  However, when I input (in Terminal or Startup Applications) **bash .startconky** it all works perfectly.  When I google bash all I get is a list of terminal commands like **apt-get** or **cd** - not what bash actually means. To me (a newbie!), it has the ability to say to the OS that I want to execture/run the following file -  **bash .startconky** = **run .startconky**.  In permissions of .startconky I made sure it was ticked as an executable file but I'm not sure exactly why I need the command **bash**.

---

### Post by Vaphell on 2012-06-07
bash is a shell and shells are things that understand scripts and run them. Usually you don't have to provide a shell name when executing a script. Either the system uses some default or looks at the very first line of the script where the flavor of shell that should be used is defined, eg #!/bin/bash, #!/bin/sh

Have you tried to type the full path of your script? (/home/yourname/.startconky)?

---

### Post by Quarkrad on 2012-06-07
That worked - thanks.

---

