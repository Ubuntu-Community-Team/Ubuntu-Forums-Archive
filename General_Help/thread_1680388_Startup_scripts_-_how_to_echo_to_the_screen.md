---
title: "Startup scripts - how to echo to the screen?"
date: 2011-02-02
forum: General Help
---

### Post by bjelakrez on 2011-02-02
Hello!

I have ubuntu desktop 10.10. I wrote a simple script that I want to execute at system startup. The only problem I have (and one that I've been struggling with for the better part of the day) is that I don't see the outputs of the script during startup.

Here's part of the script

```
#!/bin/bash
logger -i "Script starting.";
read -p "Press 'y' or 'Y' to stop the script! Otherwise continuing in 10 seconds." -n1 -t 10 -s answer
if [ "$answer" == "y" ] || [ "$answer" == "Y" ]; then
	echo
	echo "You opted to stop the script! Exiting...";
	exit;
fi
echo
echo "You didn't press any key for 10 seconds (or you didn't press 'y' or 'Y'). Continuing with the script....";
```

Basically what I want to do is have the option to prevent the script from running at startup if I wish to do so.

I have the script wait for 10 seconds and if I press y or Y, the script stops. Otherwise continue with the script.

If I execute the script from the terminal, it works. If I run it at startup, I'm sure it works as well, I just don't see the 'echos'.

Notice I have the 'logger' command at the beginning of the script. When I check the syslog, I see that the script had started.

**How do I force the script to output the 'echos' to the screen so that I know when to press the button to stop it?**

Note that I'm currently running this on a desktop ubuntu. I will ultimately run it on ubuntu server. Will it for some reason work there as is?

Any help will be greatly appreciated! Thanks in advance!

---

### Post by SeijiSensei on 2011-02-02
If you're running this from /etc/init.d or /etc/rc.local, the short answer is that you can't.  The whole notion of a startup script is that it runs unconditionally at boot.  It shouldn't throw errors or require any intervention on your part.  This is especially true on a server where there often isn't anyone around when the server boots up.  Suppose you had a server running in some remote hosting facility.  If you need to reboot it, you certainly don't want it to wait for user intervention when it starts back up.  There won't be anyone there to intervene.

One alternative might be to design a script that runs in a terminal window when your desktop environment starts up and permits user intervention.

---

