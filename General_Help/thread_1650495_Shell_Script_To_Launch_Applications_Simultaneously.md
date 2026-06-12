---
title: "Shell Script To Launch Applications Simultaneously"
date: 2010-12-21
forum: General Help
---

### Post by clockworkpc on 2010-12-21
Thanks to lovinglinux from Brazil for providing the insight that helped me to solve my problem:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1259448]("http://www.uluga.ubuntuforums.org/showthread.php?t=1259448")

I wanted to create a BASH script to launch my favourite applications **simultaneously**.  I did not want to simply add them Start Up Applications for the following reasons:

[LIST=1]
[*]Sometimes I don't want to launch them at start up
[*]Sometimes I want to launch them after start  up
[/LIST]

The key to launching them **simultaneously** is to use a single ampersand [&] at the end of each line excepting the last.  Otherwise the first line will be executed, but every subsequent application will wait for the preceding one to be closed.

Here is how I did it:

[LIST=1]
[*]cd Documents
[*]gedit startup.sh #You can call it whatever you want
[*]chmod +x startup.sh
[*]ln -s startup.sh linktostartup.sh
[*]sudo mv linktostartup.sh /usr/local/bin/startup.sh
[/LIST]

Voilà! You now have an executable file that will launch all of your favourite applications simultaneously.

For extra points create a menu item in the Gnome Menu and give it an icon too.  I recommend a Faenza > Scalable icon.

Here is my personal script.  Feel free to hack it :-)

#!/bin/bash

# Open Gmail in a standalone Chromium window
gnome-terminal -x /usr/bin/chromium-browser --app="https://mail.google.com/mail" [COLOR="Red"]&[/COLOR]
# Open Google Calendar in a standalone Chromium window
gnome-terminal -x /usr/bin/chromium-browser --app="https://www.google.com/calendar/render?tab=mc" [COLOR="red"]&[/COLOR]
# Open Remember The Milk in a standalone Chromium window
gnome-terminal -x /usr/bin/chromium-browser --app="http://www.rememberthemilk.com/home/alexandergarber/"

---

