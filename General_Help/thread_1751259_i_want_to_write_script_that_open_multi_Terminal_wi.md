---
title: "i want to write script that open multi Terminal windows and write different command i"
date: 2011-05-06
forum: General Help
---

### Post by jolian ramos on 2011-05-06
i want to write script that open multi Terminal windows and write different command i
i know how to open many terminals by repeating 'gnome-terminal' ,so i just want to know how to select the certain termianl from the opened ones to write specific something i want  . so any help please ? :)

---

### Post by jolian ramos on 2011-05-06
can someone explain to me this command how does it work ? 
 gnome-terminal  -x bash -c  , what is option "x" and "c" and "bash" in between ?

---

### Post by sanderd17 on 2011-05-06
gnome-terinal, x is execute, you want to execute bash and you give a command (c) to the bash program. 

this page gives good info: [http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution](http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution)

---

### Post by jolian ramos on 2011-05-07
how to write the root password in the opened terminal using commands of bash script

---

### Post by Maheriano on 2011-05-07
Why do you need to open terminals? Why can't you just send the script to the system to be executed?

---

### Post by jolian ramos on 2011-05-07
> **Maheriano said:**
> Why do you need to open terminals? Why can't you just send the script to the system to be executed?
because it contains some commands can't be run except from terminal so can you help me finding command that allow me enter root password in the script itself with no need to enter it manually in the terminal

---

### Post by dragonfly41 on 2011-05-07
One approach is to install autokey then write a script (not a phrase) to

launch gnome-terminal       <Shift>+<Ctrl>+N
your command as key strokes
your password as key strokes
<enter>

---

### Post by jolian ramos on 2011-05-07
> **dragonfly41 said:**
> One approach is to install autokey then write a script (not a phrase) to

launch gnome-terminal       <Shift>+<Ctrl>+N
your command as key strokes
your password as key strokes
<enter>
i didn't understand you well . can you give more explanation please about those autokeys?

---

### Post by dragonfly41 on 2011-05-07
open Synaptic Package Manager
search for "autokey"
select all four items
Apply

then after installation .. look in Accessories > Autokey (GTK)

you will see a blue icon A in to top panel

click on this to open

you can run either a phrase

e.g. typing "adr"

when in gedit window

will replace with 

[COLOR=Blue]22 Avenue Street
Brisbane
QLD
4000[/COLOR]

But you are more interested in running scripts

Create a new script
and associate a hotkey with it 

e.g. Ctrl+F1


For example here is a simple script to launch

**[COLOR=DarkSlateBlue]sudo fdisk -l [/COLOR]**

followed by

**[COLOR=DarkSlateBlue]sudo ls[/COLOR]**

in terminal

```

keyboard.send_keys("sudo fdisk -l<enter>sudo ls<enter>")

```Or you can record your own macro.


[EDIT]

Another example .. this more complicated script installs tomcat6 

```

# http://www.blog.highub.com/jsp/jsp-core/install-and-configure-tomcat-on-ubuntu/

keyboard.send_keys("sudo apt-get install sun-java6-bin sun-java6-jdk sun-java6-jre")

keyboard.send_keys("sudo apt-get install libapache2-mod-jk libservlet2.4-java libtomcat5.5-java tomcat5.5 tomcat5.5-admin tomcat5.5-webapps")

keyboard.send_keys("sudo gedit ~/.bashrc")

keyboard.send_keys("export JAVA_HOME=/usr/lib/jvm/java-6-sun")


```
Another option .. instead of autokey is to use **[COLOR=DarkSlateBlue]clicompanion.[/COLOR]**

[https://launchpad.net/clicompanion](https://launchpad.net/clicompanion)

This holds a directory of frequently used commands.

---

### Post by Maheriano on 2011-05-09
> **jolian ramos said:**
> because it contains some commands can't be run except from terminal so can you help me finding command that allow me enter root password in the script itself with no need to enter it manually in the terminal

A terminal is just a GUI that pipes the commands through to the backend. You can just send them yourself, you don't need the terminal.

---

