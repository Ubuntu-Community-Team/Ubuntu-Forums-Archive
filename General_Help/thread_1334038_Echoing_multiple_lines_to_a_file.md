---
title: "Echoing multiple lines to a file"
date: 2009-11-22
forum: General Help
---

### Post by redhotfire on 2009-11-22
Hello, I my problem is using echo to output multiple lines, such as in my code. I need to add a new line between each command but I know so little of shell to do else. What are some ways that may work.

Thanks,
red 


```

#!/bin/bash

#Variables
fileLocation="/root/.bash_profile"
fileLocation2="/etc/event.d/tty1"

Bash_profileCommands="startx
/etc/init.d/networking start
italc"

rungettyCommands="start on stopped rc2
start on stopped rc3
...

respawn
exec /sbin/mingetty --autologin user tty1"
#End of variables

#INT MAIN
echo "Creating new Bash profile for autologin and networking start"
echo $Bash_profileCommands > $fileLocation
echo "Successful"

#Echos the rungetty commands into /etc/event.d/tty1
echo "Echoing commands to /etc/event.d/tty1 for autologin"
echo $rungettyCommands > $fileLocation2
echo "Successful"

exit 0

```

---

