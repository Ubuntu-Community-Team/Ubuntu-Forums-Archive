---
title: "Making a &quot;program&quot; in terminal..."
date: 2010-05-05
forum: General Help
---

### Post by Diablosblizz on 2010-05-05
Okay, this may seem like a pretty stupid question but I'm still pretty new with Ubuntu (even though I say it in basically all my posts. :P) I just want to basically make a terminal "program" that does the following:

Show ATI card temperature which is found by running this command:
> aticonfig --adapter=0 --od-gettemperature | tail -n1 | awk '{print "Current temp: " $5}'

I then would like to ask me when fan speed I would like to set my card to, which is done with this command (with the 100 being the fan speed):

> sudo aticonfig --pplib-cmd "set fanspeed 0 100"

Kind of like a command window that requires input. I hope you understand what I mean.

Thank you, and sorry if this was already posted I don't exactly know what to search for.

---

### Post by mb_webguy on 2010-05-05
Ok, first of all, let's put that in a script.  Use a text editor to copy those lines into a new file, and then put a shebang (the line that points to the shell you want to use to interpret the script) at the top.  I'll use the bash shell, but you could use sh, dash, csh, or even the php interpreter.```
#! /bin/bash

aticonfig --adapter=0 --od-gettemperature | tail -n1 | awk '{print "Current temp: " $5}' 

sudo aticonfig --pplib-cmd "set fanspeed 0 100" 
```Of course, the obvious problem here is that there's no interactivity.  We could do that a couple of ways.  A script can take a space-separated list of input when it's called, which is put in the variables $1, $2, $3, etc.  For example, if you called the script with "myscript foo bar", within the script "myscript", the variable $1 would be "foo" and the variable $2 would be "bar".  But since you want to see the temperature before being asked to set the fan speed, we'll have to do something different.

If you are going to be doing this in the terminal exclusively, we can use the command "read" to basically do the same as above but within the script.  The "read" command also takes a space-separated list of input, but you decide the names of the variables.  So this simple addition to your script will do the job.```
#! /bin/bash

aticonfig --adapter=0 --od-gettemperature | tail -n1 | awk '{print "Current temp: " $5}' 

[COLOR="Blue"]echo "Enter the desired fan speed:"
read speed[/COLOR]

sudo aticonfig --pplib-cmd "set fanspeed 0 [COLOR="Blue"]$speed[/COLOR]" 
```If you don't run this script using "sudo" initially, it will prompt you to enter your password after entering the fan speed.

Now ideally, you'd want to do some validation on the fan speed to make sure that the user is entering a valid value rather than text or a number out of range.  But I'll leave that up to you.

If you want to run the script from a launcher on the desktop, you'll need to do something a bit different.  Zenity is a program that allows you to create graphical dialog boxes from within a script.  You'll need to install it with "sudo apt-get install zenity".  I'll let you look up all of the various options, but the following script will do the same as the above, but using graphical input and output.
```
#! /bin/bash

[COLOR="Blue"]zenity --info --title="Fan Speed Control Script" \
   --text="`[/COLOR]aticonfig --adapter=0 --od-gettemperature | tail -n1 | awk '{print "Current temp: " $5}'[COLOR="Blue"]`"[/COLOR]

[COLOR="Blue"]zenity --entry --title="Fan Speed Control Script" \
   --text="Enter the desired fan speed:" --entry-text "speed"[/COLOR]

[COLOR="Blue"]gksu[/COLOR] aticonfig --pplib-cmd "set fanspeed 0 $speed" 
```Note the backticks around the command in the first zenity statement.  These tell the shell to interpret the command inside the backticks first, and use the output in the current command.  Also note the "gksu" in the second of your original commands.  That's basically just a graphical version of "sudo".  If you used "sudo" here, the script would hang since it would be expecting you to type your password, but wouldn't give you a prompt to do so.

Now you can create a launcher that calls that script, and interact with it graphically rather than in a terminal.

[NOTE: I'm pretty sure the scripts above will work, but I wasn't able to test them since I have an nVidia card rather than an ATI.]

---

### Post by gadolinio on 2010-05-05
Nice post! One doubt: I've tried to adapt the scrip in order to make somethin really simple, just to test how zenity can take inputs... but had no success. How would you write a script that asks you to write any string, and then just shows it? I mean, how could I enter some text and turn it into a variable that the script can use? Having that tool one could do many things, like entering a path that the shell could cd to, for example.
Thanks in advance!

---

### Post by Diablosblizz on 2010-05-06
Thanks, very detailed and informational. One thing though, what do I save it as? I tried with no extention and tried using ./fanspeed from the terminal but I get permission denied (even with sudo). Sorry! :P

Thanks again.

---

### Post by tgm4883 on 2010-05-06
> **Diablosblizz said:**
> Thanks, very detailed and informational. One thing though, what do I save it as? I tried with no extention and tried using ./fanspeed from the terminal but I get permission denied (even with sudo). Sorry! :P

Thanks again.

.sh, although you don't need that. You probably just need to set it as executable "chmod +x FILENAME"

---

### Post by tgm4883 on 2010-05-06
> **gadolinio said:**
> Nice post! One doubt: I've tried to adapt the scrip in order to make somethin really simple, just to test how zenity can take inputs... but had no success. How would you write a script that asks you to write any string, and then just shows it? I mean, how could I enter some text and turn it into a variable that the script can use? Having that tool one could do many things, like entering a path that the shell could cd to, for example.
Thanks in advance!

```
#! /bin/bash
 
echo "Enter text here:"
read text

echo $text
```

---

### Post by Diablosblizz on 2010-05-06
I can't get it to work, the second one pops up and asks me the temperature but it doesn't work. I even changed it to sudo. First one does nothing (I guess I need to run it from terminal but I'd prefer the other way)

---

### Post by Timtro on 2010-05-06
> **Diablosblizz said:**
> I can't get it to work, the second one pops up and asks me the temperature but it doesn't work. I even changed it to sudo. First one does nothing (I guess I need to run it from terminal but I'd prefer the other way)

Yes, these are all scripts that you'd run from inside a terminal in order to get output. If you want something a little more graphical, try this:
```

#!/bin/bash

temperature=`aticonfig --adapter=0 --od-gettemperature | tail -n1 | awk '{print $5}'`

fansp=`zenity --entry --text="GPU Temperature is $temperature. Enter fanspeed:"`

gksu aticonfig --pplib-cmd "set fanspeed 0 $fansp"


```

Copy and paste the above text into a text editor. Save the file anywhere you like, but let's just say you saved it as /home/yourname/fansp.sh. Now, open a terminal and enter 'chmod u+x /home/yourname/fansp.sh', which will make the file executable. Now run using './fansp.sh' and it should pop up a dialog box telling you the temperature and asking you for the fan speed. After you enter the fan speed, it should set it to that, but will pop up a box to get your sudo pass.

I don't have an ATI card, so I can't test it.

---

### Post by gadolinio on 2010-05-06
> **tgm4883 said:**
> ```
#! /bin/bash
 
echo "Enter text here:"
read text

echo $text
```

Great! Thanks!

---

### Post by Diablosblizz on 2010-05-06
> **Timtro said:**
> Yes, these are all scripts that you'd run from inside a terminal in order to get output. If you want something a little more graphical, try this:
```

#!/bin/bash

temperature=`aticonfig --adapter=0 --od-gettemperature | tail -n1 | awk '{print $5}'`

fansp=`zenity --entry --text="GPU Temperature is $temperature. Enter fanspeed:"`

gksu aticonfig --pplib-cmd "set fanspeed 0 $fansp"


```

Copy and paste the above text into a text editor. Save the file anywhere you like, but let's just say you saved it as /home/yourname/fansp.sh. Now, open a terminal and enter 'chmod u+x /home/yourname/fansp.sh', which will make the file executable. Now run using './fansp.sh' and it should pop up a dialog box telling you the temperature and asking you for the fan speed. After you enter the fan speed, it should set it to that, but will pop up a box to get your sudo pass.

I don't have an ATI card, so I can't test it.

Awesome, that works! I suppose it won't be possible to run it without entering the password all the time? I also had to replace gksu with sudo.

---

### Post by Timtro on 2010-05-17
> **Diablosblizz said:**
> Awesome, that works! I suppose it won't be possible to run it without entering the password all the time? I also had to replace gksu with sudo.

Ummm, I think there are ways to get around the password, but I don't know how secure they are.

Why did you have to replace gksu with sudo? That's a drag.

---

### Post by ryan858 on 2010-05-17
I would suggest you just live with the password prompting... But if it really irks you that bad, you can exclude the script from needing a password by editing */etc/sudoers*.

You will have to do some serious reading-up on it though... I have been trying to do this for a week and have had no success. Everyone says its very possible but nothing works. I can get rid of the password prompting completely, either by making the timestamp *9999*, or by *%admin ALL=NOPASSWD: ALL.* But those are really insecure methods, as they let you run everything without password. You might as well be logged in as root. And if you do that, you might as well just get rid of all the rest of the security features, all the firewalls, etc, and turn on remote desktop and put up a web page saying "FREE COMPUTER UP FOR GRABS! JUST LOGIN TO 67.220.19.91!".

---

