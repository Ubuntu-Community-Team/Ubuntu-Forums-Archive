---
title: "Help with sudo ./wlan0up scripting"
date: 2010-03-05
forum: General Help
---

### Post by reerdo on 2010-03-05
I am new to ubuntu and have written a basic script that navigates to a drivers folder and then does the sudo ./wlan0up command. I made the script executable but to get it to work I can't just use the 'Run' command on it I need to use the 'Run in Terminal'.
 
I want this script to run automatically on start up but even know I have added it to startup I can't get it to work without manually running it.
 
The script I have written could quite easily be totally wrong so I was hoping you guys could help me out.
 
The script is as follows:
 
#!/bin/bash
 
cd Documents/
cd 8192e_realtek_0012_2010_2009
sudo ./wlan0up
 
Any help will be very much appreciated.

---

### Post by carlosgs91 on 2010-03-05
.

---

### Post by reerdo on 2010-03-05
If I type sudo ./wlan0up into Terminal it works fine but I am having to do it manually. I just can't get it to work as a log on script so it is all automated.

---

### Post by nunovi on 2010-03-05
When you run it on the terminal, does it request a password for sudo? If yes, then you'll have to add the command to sudoers file, so the script can be executed without user intervention. 

Let me know if this is the case and I can explain how to add the command to the sudoers file.

Hope this helps,

Nuno

---

### Post by reerdo on 2010-03-05
It sure does request my password each time.
 
Thanks in advance for your help Nuno.

---

### Post by nunovi on 2010-03-05
OK then. This is what you have to do:

On a terminal window type:

```
sudo visudo
```

Then at the end of the file insert:

```

<user>    ALL=NOPASSWD: <full path>/wlan0up

```

Where <user> is the username of the user executing the script.
After this, open a terminal window and try executing sudo ./wlan0up. It should execute without asking the password. It should then work as a startup script.

Let me know if this works.

Nuno

---

### Post by reerdo on 2010-03-05
That has worked in terms of the fact I now don't need my password but it is still not working on start up. Thanks for your help on this Nuno. I am pretty sure I am missing something obvious.

---

### Post by rnerwein on 2010-03-05
hi
you have to place your script in /etc/init.d  ( that's the place where the system startup scripts are stored).
to place it there use the command ( as root ): update-rc.d
for further information see: man update-rc.d
ciao

---

