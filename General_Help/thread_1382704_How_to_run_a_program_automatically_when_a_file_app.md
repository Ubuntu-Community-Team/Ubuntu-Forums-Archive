---
title: "How to run a program automatically when a file appears in a directory?"
date: 2010-01-16
forum: General Help
---

### Post by buteomont on 2010-01-16
Does anyone know how I can make a program run automatically when a file appears in a particular directory?  

I have two computers, one to program the firmware on a microcontroller (command line only), and the other is my desktop machine running Ubuntu.  I have an NFS share between the two.  What I want is to be able to drop a new firmware load into the shared directory from the desktop, and have the other computer notice it and program the microcontroller with it.  Right now I have to open an SSH session to the other computer, run the program manually, and then delete the file.  I would like to automate all of that.

---

### Post by viralmeme on 2010-01-16
> **buteomont said:**
> Does anyone know how I can make a program run automatically when a file appears in a particular directory?  ..

#!/bin/bash[FONT=monospace]
[/FONT]while [ 1 ]
[COLOR=#000000]do
[/COLOR]if [ -f file.name ]; then
        run.microcontroller.prog
fi
done

---

### Post by Locutus_of_Borg on 2010-01-16
here is a bash script that will check for a certain file every five minutes then run whatever you specify if it exists
```

#!/bin/bash
file=/path_to/file
run='command'

while true; do if [ -x $file ]; then $run; fi && sleep 300; done

```

there's probably a better way to do this though



edit: looks like i was too slow...

---

### Post by buteomont on 2010-01-16
Thanks!  Both scripts look like they should work fine.  I like the 5-second sleep in the 2nd one - seems like without something like that it will eat up cycles.  Would it be better to run something like that as a cron job instead?

Edit: oops, I mean 5-minute.

---

### Post by john newbuntu on 2010-01-17
You can in general go for a system as you proposed with a few bells and whistles such as:
1. verifying that the file got transmitted fully (perhaps by verifying the md5sum or CRC).  You might want to send a trailer file with that info.
2. Moving files on to a staging directory and then applying your firmware from there.
3. Logging operations at every stage.
4. Checking for files that fail transmission.
5. e-mail if something goes wrong.

---

### Post by buteomont on 2010-01-17
That would certainly be appropriate if this were for a customer or was a critical kind of application, but this is essentially a band-aid to allow me to program an Arduino under Linux.  I had no troubles doing it under XP, but then had 64-bit Vista thrust upon me when I upgraded my antique computer.  I decided to make the jump to Ubuntu Linux instead, but have never been able to get the USB to work right.

So, until khubd gets fixed for 64-bit processors, I have an NSLU2 with Debian running on a thumb drive sitting on my desk with a shared directory.  When I write a new program for the Arduino, I can drop in on the shared drive and avrdude pokes it into the Arduino. 

I wound up using a combination of the two suggestions by Locutus_of_Borg and ymitchell above.  I changed the sleep time to 10 seconds, and changed the if statement to use -e instead of -f or -x, since my script deletes the firmware file after it loads it to the Arduino.

Thanks, it works like a well-oiled machine!

---

