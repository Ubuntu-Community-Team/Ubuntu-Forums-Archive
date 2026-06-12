---
title: "Shell Scripts"
date: 2010-07-25
forum: General Help
---

### Post by snowmanman on 2010-07-25
How can I run a .sh file that I wrote without going into the terminal and putting in ```
sh file.sh
```
How can I just click on it and have it run?

---

### Post by TeoBigusGeekus on 2010-07-25
[http://www.linuxquestions.org/questions/programming-9/executing-shell-script-in-terminal-directly-with-a-double-click-370091/]("http://www.linuxquestions.org/questions/programming-9/executing-shell-script-in-terminal-directly-with-a-double-click-370091/")

---

### Post by limestone on 2010-07-25
first you'll have to set permissions. open a terminal and do,
```
chmod a+x file.sh
```
then you can simply click on the file and run or type ./file.sh

---

### Post by prodigy_ on 2010-07-25
You can add launchers to your desktop and/or panel. Put ```
sh /<path_to_your_script>/<your_script_name>
``` into the "Command" field of a launcher and it'll act as a shortcut to your script.

---

### Post by snowmanman on 2010-07-25
Thanks guys it worked!

---

