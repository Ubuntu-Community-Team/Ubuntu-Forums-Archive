---
title: "conky config help"
date: 2009-07-01
forum: General Help
---

### Post by insanity99 on 2009-07-01
where do i but my config file for conky? and what filename/extension should i use?

---

### Post by VCoolio on 2009-07-01
Default is ~/.conkyrc, so if you run just "conky" it will search for that file. But you can put it anywhere and name it as you wish and point to it with the command "conky -c /path/to/conkyconfig". This way you can load multiple conkies: "conky -c /path/to/conkyconfig1 & conky -c /path/to/conkyconfig2". No extension needed.

---

### Post by insanity99 on 2009-07-01
ok, but where will it search for ~/.conkyrc? will it search anywhere on the computer?

EDIT: the path method worked but it their a way to make it open automatically?

---

### Post by VCoolio on 2009-07-01
ah, sorry, no. ~/ is short for your home folder, so ~/ = /home/username. The dot in front of the filename indicates that it is hidden. You can make a launcher with the command in it so you won't have to type it each time. Or if you want to run from a terminal make an alias for it in ~/.bashrc. Add a line like
alias myconky='conky -c /path/to/conky'
and now when you enter myconky in a terminal it will run conky with the specified config.

Maybe even easier, write a little script and make it executable, so you can run that instead of conky. E.g. paste this in a texteditor:

#!/bin/sh
conky -c /path/to/config

Save in your home folder like 'myconky', in terminal run "sudo chmod u+x ~/myconky" to make it executable and now run 'myconky' instead of 'conky' to automatically have your specified config.

---

### Post by insanity99 on 2009-07-01
thanks man, i made a launcher in the aplication menu which works well but the only problem is i dont know how to close it once it's open, since terminal isn't open and theres no windows to close.

---

### Post by VCoolio on 2009-07-01
You can run "killall conky" or make a launcher for the following script (which isn't mine btw); it will run conky if it isn't running or kill it if it is running :

#!/bin/sh
if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 conky -c /path/to/conkyconfig1
fi

---

### Post by insanity99 on 2009-07-01
thanks that worked great, is there a script to make it display CPU temp?

---

