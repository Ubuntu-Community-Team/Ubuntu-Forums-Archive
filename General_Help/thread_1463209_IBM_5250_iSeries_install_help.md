---
title: "IBM 5250 iSeries install help"
date: 2010-04-26
forum: General Help
---

### Post by davisty on 2010-04-26
Hello

First of all. when you look up the work Newbie in the dictionary it has my picture next to it.

I have (I think) installed an rpm application from IBM. It is a safe and standard telnet development program.

The problem is ... I cant find it. It's in the Synaptic package manager but how do I execute the program?

---

### Post by ubunterooster on 2010-04-26
It's likely a command-line started program.

Look at the Synaptic name for it. Run that name in the terminal.

---

### Post by donespo on 2010-05-27
If your installation worked, you should be able to open a session by running the following command in the terminal:

> ibm5250 xxx.xxx.xxx.xxx -title AS400/Linux -DISPLAY_NAME "LUCID-A LUCID-B LUCID-C" -LANGID en_US

where xxx.xxx.xxx.xxx is the IP address of your iSeries.  You can also change the display names to suit your needs but you'll have to keep it to 8 characters or less before the -A, -B, etc.

To make your life easier for day-to-day operations you can make a launcher with the above as the command line..

---

### Post by donespo on 2010-05-27
One more thing.  If you haven't already stumbled across this [http://www.redbooks.ibm.com/abstracts/sg246551.html]("http://www.redbooks.ibm.com/abstracts/sg246551.html") I highly recommend it.  If you're an iSeries admin trying to migrate from Windows to 'nix environment the sections on ODBC and SQL will be of particular interest.

Good luck on your quest. I was exactly where you are now when I did my first Ubuntu install (Edgy) and I couldn't have done it without this forum and all the helpful souls therein.

---

### Post by davisty on 2010-05-27
> **donespo said:**
> One more thing.  If you haven't already stumbled across this [http://www.redbooks.ibm.com/abstracts/sg246551.html]("http://www.redbooks.ibm.com/abstracts/sg246551.html") I highly recommend it.  If you're an iSeries admin trying to migrate from Windows to 'nix environment the sections on ODBC and SQL will be of particular interest.

Good luck on your quest. I was exactly where you are now when I did my first Ubuntu install (Edgy) and I couldn't have done it without this forum and all the helpful souls therein.
Thank You for your reply. I was able to get the program working. Sorry. I forgot to close the thread.

Thank You for a very through reply, and all your time.

---

