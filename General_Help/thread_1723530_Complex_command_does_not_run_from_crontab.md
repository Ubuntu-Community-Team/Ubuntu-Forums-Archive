---
title: "Complex command does not run from crontab"
date: 2011-04-07
forum: General Help
---

### Post by Quaxo76 on 2011-04-07
Hello,
I'm trying to add a command to crontab, and I'm having some problems.
I want to add an entry that appends some data to a file, which is named as today's date.

If I add this entry to crontab:

```
* * * * * /path/to/script/myscript >> outputfile.txt
```

then it works; every minute the script's output is appended to the file "outputfile.txt" if it exists (otherwise it is created).

But if I try to add:

```
* * * * * /path/to/script/myscript >> /path/to/destination/folder/`date +%Y%m%d`.csv
```

then no file is created. If I manually run

```

touch /path/to/my/folder/`date +%Y%m%d`.csv

```

or even

```
./myscript >> /path/to/my/folder/`date +%Y%m%d`.csv
```

then the file is created correctly.

So: the complete command works from the terminal, but not from crontab.
The "basic" command, which writes to a fixed filename, works ok both from the terminal and from crontab.

Can anyone tell me why, and how can I do what I need?

Thanks in advance,
Cristian

---

### Post by dandnsmith on 2011-04-07
I'm really ignorant about these matters, but would first check whether giving the full path to date (ie /bin/date) gets what you want.
I seem to recall that the operating environment for the crontab entries is severely limited.

HTH

---

### Post by Quaxo76 on 2011-04-07
Hm... Right now I'm trying to use crontab to launch a script which then runs the command. It more or less works, but there's another quirk.
If in the terminal I type
```
echo -ne `date +%Y`
```
it prints the year, without the trailing newline (which is what I want).
But if I put the same command in a script, it has a different behaviour - in the output, I find "-ne 2011" AND a newline. Which is not what I need. Basically the -ne option is seen as a text to be printed.
How can I append things without a newline? I need that every line of the resulting file has the time of day and then the output of my other script - like this:

15:59 32 25
16:04 33 25

and so on... where the time is the time of the measurement, and the numbers are temperature readings.

Cristian

---

### Post by Quaxo76 on 2011-04-07
Update: 
If in the script I use the command
```
echo -n `date +%Y`
```
using -n instead of -ne, then it works. I have no idea why. But I have to say I'd like if everything was a little more consistent - i.e. if the same command gave the same results in a terminal or in a script or wherever else... :)

Cristian

---

### Post by SeijiSensei on 2011-04-08
This might depend on the shell you're using.  Does your script begin with "#!/bin/bash" to force the use of bash?  Ubuntu defaults to using a smaller, but more limited shell than bash called "dash".  If your script starts with "#!/bin/sh" on Ubuntu, it'll be run by dash which may not support all the options bash does.  Try specifying bash specifically and see if that helps.

To make bash be the default shell, run:

```
cd /bin
sudo rm -f sh
sudo ln -s bash sh

```

---

### Post by lloyd_b on 2011-04-08
> **SeijiSensei said:**
> This might depend on the shell you're using.  Does your script begin with "#!/bin/bash" to force the use of bash?  Ubuntu defaults to using a smaller, but more limited shell than bash called "dash".  If your script starts with "#!/bin/sh" on Ubuntu, it'll be run by dash which may not support all the options bash does.  Try specifying bash specifically and see if that helps.

To make bash be the default shell, run:

```
cd /bin
sudo rm -f sh
sudo ln -s bash sh

```

It probably is a dash vs bash issue, but I don't like your solution...

This might solve this particular problem, but it has the potential to create a lot of problems elsewhere in the system - if a script specifies "#!/bin/sh", it probably does so for a reason, and may not run correctly under bash.
  
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

The root problem appears to be dash barfing when it comes to the backtic'ed command(`date +%Y%m%d`).

You *might* be able fix this by telling cron to use bash rather than sh to interpret commands from a crontab.  This is done by editing the file "/etc/crontab", and changing the "SHELL=" line (note you'll need a 'sudo' to edit this file).

Personally, I'd just use a "wrapper" script:```
#!/bin/bash

/path/to/script/myscript >> /path/to/destination/folder/`date +%Y%m%d`.csv
```and then modify the crontab so that it just runs this script.

Lloyd B.

---

### Post by Quaxo76 on 2011-04-08
Thanks for the replies... it makes sense.
@ Lloyd: that is exactly what I ended up doing. Except that I haven't specified the shell yet. I made a script like this:

```
echo -n `date +%H:%M` >> /home/cristian/Desktop/Temperature/`date +%Y%m%d`.csv
echo -n " " >> /home/cristian/Desktop/Temperature/`date +%Y%m%d`.csv
/home/cristian/Desktop/Temperature/templog >> /home/cristian/Desktop/Temperature/`date +%Y%m%d`.csv
```

where 'templog' is the program that outputs the temperature. This script is run every minute by an entry in crontab. So I get a file every day, with all the temperature readings for the day - as long as the computer is running and the usb thermometer is connected. And then I can import the csv into openoffice and make a nice graph of the temperature trend. It's probably a really nasty "hack" but it works, and I'm not a programmer! :)

By the way... how can I add a blank space (" ") to the first line, without having to add it with the second "echo" command?

Thanks again,
Cristian

---

### Post by Krytarik on 2011-04-08
> **Quaxo76 said:**
> 
```
echo -n `date +%H:%M` >> /home/cristian/Desktop/Temperature/`date +%Y%m%d`.csv
echo -n " " >> /home/cristian/Desktop/Temperature/`date +%Y%m%d`.csv
/home/cristian/Desktop/Temperature/templog >> /home/cristian/Desktop/Temperature/`date +%Y%m%d`.csv
```
By the way... how can I add a blank space (" ") to the first line, without having to add it with the second "echo" command?

Simply put it this way :D:
```
echo -n "`date +%H:%M` " >> /home/cristian/Desktop/Temperature/`date +%Y%m%d`.csv
/home/cristian/Desktop/Temperature/templog >> /home/cristian/Desktop/Temperature/`date +%Y%m%d`.csv
```
Greetings.

---

### Post by Quaxo76 on 2011-04-12
> **Krytarik said:**
> Simply put it this way :D:
```
echo -n "`date +%H:%M` " >> /home/cristian/Desktop/Temperature/`date +%Y%m%d`.csv
/home/cristian/Desktop/Temperature/templog >> /home/cristian/Desktop/Temperature/`date +%Y%m%d`.csv
```
Greetings.

Thank you! I didn't know that ticks embedded in quotes would still be evaluated! :)

Cristian

---

