---
title: "&quot;Pop-up&quot; message via SSH"
date: 2010-11-02
forum: General Help
---

### Post by pelikan555 on 2010-11-02
Hi,

On our home network all the PCs are running Ubuntu, including my dad's.
Is there any way when he is on his computer that I can log-in via SSH console and display on his desktop an unmissable, mean-spirited message in order to upset him (just a bit)?

Thank you!

---

### Post by HermanAB on 2010-11-02
It is a bit late for a halloween message.

https://encrypted.google.com/search?q=x+message&ie=utf-8&oe=utf-8&aq=t&rls={moz:distributionID}:{moz:locale}:{moz:official}&client=firefox

---

### Post by matt_symes on 2010-11-02
Hi

Also, i think gdialog or one of its variants would work. (Please correct me if i am wrong, i've never tried it).

Be nice though. :)

Kind regards

---

### Post by steevven1 on 2010-11-02
Here's a script I wrote to do just that! You'll need root access though:

```
#!/bin/bash
## gwall, short for "graphical wall," will write a wall message (given
## as standard input) to each remote ssh user's terminal as usual, but
## will also cause a GUI popup to appear on the monitor of the physical 
## ssh server, if there is one.
## Written by Steven H. Keys
## Last Updated: 2010-08-31

## Take standard input
read message
## Write to all command-line terminals
echo $message | sudo wall
## Export the DISPLAY variable to enable server monitor access
export DISPLAY=:0.0
## Write the message to the popup window.
sudo zenity --info --text="$message"

```Enjoy!

EDIT: I should mention for newer users, you have to give this thing some input, so the syntax I recommend and use is: echo "Put your popup message here." | gwall (after having put gwall in one of your bins and making it executable.)

---

