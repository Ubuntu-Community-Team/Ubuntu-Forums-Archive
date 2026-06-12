---
title: "starting upstart job when graphics card is available"
date: 2010-08-19
forum: General Help
---

### Post by NetForce1 on 2010-08-19
I have a Python script to control the speed of the fan of my videocard since there is no speed control on the card itself. I want to run this script as a daemon, and tried to have it auto-start using Upstart. 
Of course, the script can only run when the video card is available, so I tried to start when gdm is starting. Since the gdm job contains a line reading 'emits starting-dm' I thought I could use the starting-dm event like this: 'start on starting-dm'. Unfortunately this does not work. Then I tried 'start on starting gdm', but that doesn't work either. 

Does anyone know how to configure my job correctly so that it starts only when the video card is available?

The job does run when I launch it manually with 'sudo start jobname'

---

