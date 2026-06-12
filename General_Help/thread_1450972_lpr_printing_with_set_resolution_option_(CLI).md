---
title: "lpr printing with set resolution option (CLI)?"
date: 2010-04-09
forum: General Help
---

### Post by Rocket J Squirrel on 2010-04-09
This might be more of a Linux question, if so, maybe someone can point me to an appropriate forum to ask it in. 

I have a shell script set up to print a test page on a couple of my rarely-used large format printers. These are expensive boys, and if they are left unused for too long, their cartridges dry up. So once a week, cron runs the script and everyone is happy. 

Except I'd like to change the print resolution for one of the printers. 

lpr does not seem to have an option to send a command to the printer for setting resolution. 

Is there another command that I could use under Ubuntu within Linux to do what lpr does, but also offers the setting of print resolution?

---

### Post by Rocket J Squirrel on 2010-04-09
Oops -- found it. 
[FONT=monospace]
[/FONT]lpr -o ppi=*value* does the job. 

But only for image files, it has no effect on Postscript files, like the Ubuntu-provided test page.

[http://www.cups.org/documentation.php/options.html](http://www.cups.org/documentation.php/options.html)

---

