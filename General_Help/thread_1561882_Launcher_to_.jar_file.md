---
title: "Launcher to .jar file?"
date: 2010-08-26
forum: General Help
---

### Post by zami on 2010-08-26
I have this file
*AlienFXLite-0.4b.jar*

in this directory
*/home/laura/AlienFX*

that I open/run with this command
sudo java -jar AlienFXLite-0.4b.jar 

Instead of using the terminal every time, I'd like to make a launcher. How can I do this?

I've tried...
[I]/home/AlienFX/ && gksudo java -jar AlienFXLite-0.4b.jar 
gksudo java -jar /home/laura/AlienFX/AlienFXLite-0.4b.jar [/I]
And about 50 varients on those two lines.  Heh.  I'm stumped.

Thanks for any help!

-zami

---

### Post by Vaphell on 2010-08-26
what about gksu sh -c "java -jar /home/laura/AlienFX/AlienFXLite-0.4b.jar" ?

---

### Post by spcwingo on 2010-08-26
I would create a shell script which is what I think Vaphell was suggesting.  To do that open your text editor and enter this:

```
/bin/bash

gksudo java -jar /home/laura/AlienFX/AlienFXLite-0.4b.jar
```

Then save (I would suggest naming it something starting with a . in your home folder so it will be hidden) and quit.  Then just right-click on your menu and select "Edit Menus".  Then just add it anywhere you want it on your menu.  :)

Oh, I almost forgot...you also have to make it executable.  Navigate to wherever you saved it and right-click it.  Select "Properties"  and then the "Permissions" tab.  Finally tick the box beside "Allow executing file as program".  You should now be golden.

---

### Post by zami on 2010-09-05
Well I finally put the entire .jar file into my home directory (just take the variables of slashes and home and my name out of the equation!) and then it opened just fine with

gksu "java -jar AlienFXLite-0.4b.jar"

Thanks for scooting me along the right path, all.  :)

-zami

---

