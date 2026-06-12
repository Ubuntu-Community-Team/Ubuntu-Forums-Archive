---
title: "open cups-pdf output in pdf reader automatically"
date: 2010-01-15
forum: General Help
---

### Post by lykwydchykyn on 2010-01-15
I've got cups-pdf installed and working fine to print to PDF.

What I find kind of annoying is that it prints silently to ~/PDF with an automatic filename and with no feedback when it is done printing.  So I have to monitor that directory manually for when a new file shows up.

What I'd like to have when I print to PDF is the output of cups-pdf piped to a pdf reader (like okular, in my case) which would open automatically when the printing is done so I can review the results and save or discard them. 

I've looked through the options and tried to find documentation on cups-pdf, but I haven't found a way to make this happen yet.  Anyone know if this can be done?

---

### Post by lykwydchykyn on 2010-01-15
Ok, true to form I figured it out on my own AFTER posting a question to a forum.  So here's my hacked-together solution for anyone interested:

1. Disable apparmor profile for cups (I tried adjusting it, but had no luck)
```

sudo ln -s /etc/apparmor.d/usr.sbin.cupsd /etc/apparmor.d/disabled/
sudo /etc/init.d/apparmor restart

```

2. Create a post processing script for cups-pdf.  I called mine "cups-pdf-postproc.sh" and put it in /usr/local/bin.
```

#!/bin/bash
DISPLAY=:0.0
export DISPLAY
XAUTHORITY=/home/$2/.Xauthority
export XAUTHORITY

#open the pdf
xdg-open $1 &

```

3. make the script executable
```

sudo chmod +x /usr/local/bin/cups-pdf-postproc.sh

```

4. Tell cups-pdf to use it as a postprocessing script.  To do this, edit /etc/cups/cups-pdf.conf. Add this line:
```

PostProcessing /usr/local/bin/cups-pdf-postproc.sh

```

5. restart cups.
```

sudo /etc/init.d/cups restart

```

---

### Post by dwitkin on 2011-03-22
I love the idea of this script, but for some reason the script isn't working for me. When I run the script from the command line, it opens evince (minor mod to script to use evince). But when I generate a PDF using CUPS, nothing happens. I restarted the CUPS service twice, but no change.

Any suggestions?

---

### Post by lykwydchykyn on 2011-03-22
Check out the various logs in /var/log/cups.  Probably cups-pdf_log will have some errors in it that may point you to the problem.

If you don't find any errors, you may want to adjust the "LogLevel" setting in /etc/cups/cupsd.conf to "debug", then try it again.

---

