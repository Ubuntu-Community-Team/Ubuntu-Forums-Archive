---
title: "Shell script question, how to display shell script output in a window"
date: 2009-11-17
forum: General Help
---

### Post by Green_Star on 2009-11-17
I am writing a shell script, it will be executed with nautilus right click menu. I want to monitor the output of the shell script. I would like to do something like how the ubuntu updates window works(on top it shows the process bar and in the bottom in black window it actually shows the terminal output). not exactly like this ubuntu update window but something like that. can you guide me in that.

When I execute the shell sctipt from right click it is executing in background. After some research if found a syntax and tried, but still failed, it is giving an error saying 'There was an error creating the child process for this terminal' and nothing happening.

> #!/bin/bash

tty -s; if [ $? -ne 0 ]; then gnome-terminal -x "cd $1;lxsplit -j $2" --hide-menubar --title="Joining files" ; exit; fi


$1 and $2 variables will be passed by 'nautilus action configuration' application. This script works well in following manner but I can not see the output.

> #!/bin/bash

cd $1
lxsplit -j $2


---

### Post by VCoolio on 2009-11-17
You could maybe use zenity for that; just pipe into a text-info window:

```
echo blahblah | zenity --text-info
```

It does live monitoring too; if I have a script

```
#!/bin/bash

echo blah;
sleep 5;
echo blah5;
sleep 5;
echo blah10;
exit 0
```

and call it with "sh script.sh | zenity --text-info" the lines are added one after another.

---

### Post by Green_Star on 2009-11-17
> **VCoolio said:**
> You could maybe use zenity for that; just pipe into a text-info window:

```
echo blahblah | zenity --text-info
```

It does live monitoring too; if I have a script

```
#!/bin/bash

echo blah;
sleep 5;
echo blah5;
sleep 5;
echo blah10;
exit 0
```

and call it with "sh script.sh | zenity --text-info" the lines are added one after another.

I played with zenity before, but it didn't come into my mind  about using it for this purpose. Thanks man, I will try and let you know.

---

### Post by Green_Star on 2009-11-17
Yup, it is working fine. Thanks man.

The terminal shows the log line by line with some delay while working. but it looks like zenity wait till the process completes and shows the whole script log at last. I think I can live with it.

Thanks again.

---

### Post by Nostoc on 2009-11-17
> **Green_Star said:**
> Yup, it is working fine. Thanks man.

The terminal shows the log line by line with some delay while working. but it looks like zenity wait till the process completes and shows the whole script log at last. I think I can live with it.

Thanks again.

gnome-terminal -e *pathToYourScript*

Should execute your script in a terminal.

---

### Post by Green_Star on 2009-11-17
> **Nostoc said:**
> gnome-terminal -e *pathToYourScript*

Should execute your script in a terminal.

I tried this now, it is not working, i mean it is working in background and completed the task when I tried using nautilus right click menu, but not showing the terminal window

in nautilus action configuration

script path: gnome-terminal -e /home/.scripts/join-files.sh
Parameters are : %d %f

script is 
> #!/bin/bash

cd $1
lxsplit -j $2

---

