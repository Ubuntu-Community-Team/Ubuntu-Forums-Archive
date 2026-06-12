---
title: "Help with my bash script to run some commands"
date: 2011-08-06
forum: General Help
---

### Post by smilingsidewayz on 2011-08-06
[FONT=Arial]
heres my script the first command runs but then nothing how do I tell the program to continue onto the next program / command
I know what you might be thinking so just please ignore my example choice for programs
further more how do I make the program ask for input for say the spot with (address here)?

thanks

everyone

#!/bin/bash

exec airmon-ng stop wlan0;

command ifconfig wlan0;

exec machhanger -m (address here) wlan0;

exec airmon-ng start wlan0;

command ifconfig mon0 down;

exec macchanger -m (address here) mon0;

command ifconfig mon0 up;[/FONT]

---

### Post by blind2314 on 2011-08-07
> **smilingsidewayz said:**
> [FONT=Arial]
heres my script the first command runs but then nothing how do I tell the program to continue onto the next program / command
I know what you might be thinking so just please ignore my example choice for programs
further more how do I make the program ask for input for say the spot with (address here)?

thanks

everyone

#!/bin/bash

exec airmon-ng stop wlan0;

command ifconfig wlan0;

exec machhanger -m (address here) wlan0;

exec airmon-ng start wlan0;

command ifconfig mon0 down;

exec macchanger -m (address here) mon0;

command ifconfig mon0 up;[/FONT]

First of all, in bash, you don't terminate single lines with a ';'. Also, given the subject matter of the commands you're running here (and the sheer lack of knowledge, which leads me to believe this isn't for educational purposes), I don't think you're going to get much help.

---

### Post by Basher101 on 2011-08-07
Just google. I can't understand why people first ask questions in forums instead of doing some research. Look up some tutorials on how to make bash scripts

---

### Post by bodhi.zazen on 2011-08-07
> **smilingsidewayz said:**
> [FONT=Arial]
heres my script the first command runs but then nothing how do I tell the program to continue onto the next program / command
I know what you might be thinking so just please ignore my example choice for programs
further more how do I make the program ask for input for say the spot with (address here)?

thanks

everyone

#!/bin/bash

exec airmon-ng stop wlan0;

command ifconfig wlan0;

exec machhanger -m (address here) wlan0;

exec airmon-ng start wlan0;

command ifconfig mon0 down;

exec macchanger -m (address here) mon0;

command ifconfig mon0 up;[/FONT]

You do not need the "command" or "exec" , use the full path

```
#!/bin/sh
airmon-ng stop wlan0&

ifconfig wlan0&

machhanger -m (address here) wlan0;

airmon-ng start wlan0&

ifconfig mon0 down&

macchanger -m (address here) mon0&

ifconfig mon0 up&
```

Add a "&" at the end.

See: [http://linuxcommand.org/](http://linuxcommand.org/)

you probably do not need to add the & at the end of most of those lines.

A ";" is used if you put multiple commands on the same line

command_1
command_2

or

command_1 ; command_2

---

