---
title: "problem with canon mp560 series printer"
date: 2012-09-05
forum: General Help
---

### Post by bmc8ak on 2012-09-05
Hey so I've been using ubuntu for a few months and I used the forums to help me install the drivers so that I could use my canon mp560 printer. This all worked fine until I now moved to my new house recently and I have no idea why. I've tried both wireless and direct connection with the usb cord. Basically what happens is it will recognize the printer and send the job then the printer will say processing for about 1 second and immediately stop and then a little bit later the computer will say the job was completed. The printer won't print any kind of test page, PDF, text file, etc.

---

### Post by e-a-c on 2013-01-21
Did you ever solve this? I'm having the exact same problem.

---

### Post by pdc on 2013-01-22
[LIST]
[/LIST]a debugging how-to;

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

go down to CUPS error log

read point 1 and see the thumbnail that I enclose that shows what to do

then in a terminal

> [COLOR="Red"]cupsctl LogLevel=debug[/COLOR] to activate debug logging

then see point 3: > [COLOR="Red"]cupsctl LogDebugHistory=999999[/COLOR]

Note next section: **[COLOR="DarkRed"]TROUBLESHOOTING WIZARD[/COLOR]** ..... open as advised and follow

..... see attached thumbnail ......

**[COLOR="DarkOrchid"]Wizard[/COLOR]**
[LIST]
[*]1
[/LIST]There is a [COLOR="DarkOrchid"]*_troubleshooting wizard_*[/COLOR] in system-config-printer (System -> Administration -> Printing in GNOME classic, Gear icon at the upper right of the screen -> Printers in Unity). 

You find it in the "[COLOR="Blue"]Help[/COLOR]" menu of system-config-printer. 

[LIST]
[*]It produces a text file with a lot of useful information to attach to bug reports. [COLOR="Magenta"]*Follow the instructions of the wizard*[/COLOR]. 

[*]If you reach the test page step, you can either click the button to print the test page or you can print a job to the selected printer from any application or from the command line. 

[*]The job will be shown in the integrated job viewer. Wait until it completes or goes into "Stopped" state. 

[*][COLOR="Magenta"]ONLY THEN AND NOT BEFORE[/COLOR] mark the checkbox at the job, 

[*]........answer whether the job got printed correctly, 

[*]........and click "Forward". 

[*]After that the file will get generated. Save it and attach it to your bug report.......or you may have solved your issue
[/LIST]

---

