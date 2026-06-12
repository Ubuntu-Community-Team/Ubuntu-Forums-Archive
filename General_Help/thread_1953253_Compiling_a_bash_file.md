---
title: "Compiling a bash file?"
date: 2012-04-05
forum: General Help
---

### Post by Jitarth on 2012-04-05
I don't know if it goes here or not but i need help with a script.

i have a cdma usb modem which is not recognized by ubuntu.

to use it i have to eject it first from the device manager.
then open terminal and sudo modprobe it and then use wdial.

to cut short of this process i made this script 


```
#!/bin/sh
sudo echo "usb modem"
sudo eject /dev/sr0
sudo sleep 1
sudo modprobe usbserial vendor=0x22f4 product=0x0021
sudo sleep 1
sudo wvdial
```

this eased up my work.

now i am looking for a way that i can compile this code to a binary so that executing it would launch this script in terminal.

i guess it would ease up cut short 2 clicks to one :P and also for educational purpose :P :D

how do i do it?

---

### Post by beanhead on 2012-04-05
Ok for scripting you have to use this line at the top of the file
#!/bin/bash



then put your commands in and when your done you have to make it executable.
commandline >chmod yourscriptfilename a+x

then you can run it like ./scriptFileName

enjoy

---

### Post by Jitarth on 2012-04-05
I am currently running it like that. but i want something much easier lke a .exe file on windows, that could launch it directly in a terminal. i have a sister and explaning such stuff to her is impossible :( so is there any method to compile it into a binary? that can be launched from the desktop?

---

### Post by azmyth on 2012-04-05
You don't compile a bash file as you just run it as there's nothing to compile. You can create a new desktop shortcut and create as a link to an application and then just enter /path/to/your/script/file.

---

### Post by zombifier25 on 2012-04-05
Err, you CAN run it in a terminal and you CAN launch it from the desktop, just like a binary.
As for compiling, no, you can't.

---

### Post by Vaphell on 2012-04-05
shell scripts are like .bat files in windows. They are text files that can be run just like binary executables.

---

### Post by Jitarth on 2012-04-05
When i run it normally it does nothing. when i run it in terminal then it works. cant it directly run in a terminal from the desktop? though it aint that important but still? like the synaptic package downloader. it runs dpkg commands that are run in the terminal directly... when you see the details you can see a black terminal there also? how do they do it?

---

### Post by Vaphell on 2012-04-05
for unknown reasons option to add launchers was removed from rightclick menu
you need this
```
gnome-desktop-item-edit --create-new ~/Desktop
```

---

### Post by zombifier25 on 2012-04-05
Weird. When you double-click a .sh script you usually has the option of running it in a terminal.
Try opening Nautilus, go to Edit > Preferences > Behavior > Executable Text Files and check the "Ask each time" choice.
If that doesn't work, add
```
read
```to the end of your script. It will stop the script from exiting in the terminal until the Enter key is pressed.

---

### Post by oklokl on 2012-04-06
[http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution](http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution)

chmod 755 1.sh
chmod 755 test.sh

```
#!/bin/bash
# 1.sh  The click of a mouse
gnome-terminal -e "bash -c \"~/Desktop/[COLOR=Red]test.sh[/COLOR]; exec bash\""
```or

```
#!/bin/bash
xterm -hold -e "test.sh"

``````
#!/bin/bash
# test.sh
echo "usb modem"
sudo eject /dev/sr0
sudo sleep 1
sudo modprobe usbserial vendor=0x22f4 product=0x0021
sudo sleep 1
sudo wvdial
```

---

### Post by Jitarth on 2012-04-06
> **zombifier25 said:**
> Weird. When you double-click a .sh script you usually has the option of running it in a terminal.
Try opening Nautilus, go to Edit > Preferences > Behavior > Executable Text Files and check the "Ask each time" choice.
If that doesn't work, add
```
read
```to the end of your script. It will stop the script from exiting in the terminal until the Enter key is pressed.

it shows run in terminal. i hadn't performed chmod to the new file.

> **oklokl said:**
> [http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution](http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution)

chmod 755 1.sh
chmod 755 test.sh

```
#!/bin/bash
# 1.sh  The click of a mouse
gnome-terminal -e "bash -c \"~/Desktop/[COLOR=Red]test.sh[/COLOR]; exec bash\""
```or

```
#!/bin/bash
xterm -hold -e "test.sh"

``````
#!/bin/bash
# test.sh
echo "usb modem"
sudo eject /dev/sr0
sudo sleep 1
sudo modprobe usbserial vendor=0x22f4 product=0x0021
sudo sleep 1
sudo wvdial
```

the first code is for the 1.sh file and the other is my code of the test file right?

so it wont ask b4 running whether to run in the terminal or to simply run?

---

### Post by oklokl on 2012-04-06
1.sh Execution(sh Button) > 2.sh Functioning

or


[http://kin.naver.com/qna/detail.nhn?d1id=1&dirId=10302&docId=149034869](http://kin.naver.com/qna/detail.nhn?d1id=1&dirId=10302&docId=149034869)
```
#!/bin/bash
# test.sh


function display_and_run {
echo $*
eval! $*
}

display_and_run  "sudo eject /dev/sr0"
display_and_run  "sudo sleep 1"
display_and_run  "sudo modprobe usbserial vendor=0x22f4 product=0x0021"
display_and_run  "sudo sleep 1"
display_and_run  "sudo wvdial"
```

---

