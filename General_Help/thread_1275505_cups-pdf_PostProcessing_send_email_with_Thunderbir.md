---
title: "cups-pdf PostProcessing send email with Thunderbird"
date: 2009-09-25
forum: General Help
---

### Post by mmullis on 2009-09-25
I would like my cups-pdf printer post processing to launch Mozilla Thunderbird with the .pdf as an attachment.

In /etc/cups/cups-pdf I have the PostProcessing key set to /usr/local/bin/cupscript.sh

cupscript.sh

```

#!/bin/bash
CURRENT_PDF="${1}"
CURRENT_USER="${2}"
DISPLAY=:0.0 /
export DISPLAY
XAUTHORITY=/home/${CURRENT_USER}/.Xauthority
export XAUTHORITY
thunderbird -compose attachment=file:$CURRENT_PDF
exit

```If I execute the script from the shell it works. Example:

$ ./cupscript.sh /home/user/PDF/file.pdf

If I print to the pdf printer it will not launch Thunderbird.

If I have the script launch Evolution it works but I would rather use Thunderbird.

```

#!/bin/bash
CURRENT_PDF="${1}"
CURRENT_USER="${2}"
DISPLAY=:0.0
export DISPLAY
XAUTHORITY=/home/${CURRENT_USER}/.Xauthority
export XAUTHORITY
evolution mailto:?attach=$CURRENT_PDF
exit

```aa-complain or even stopping the apparmor service makes no difference.

Setting the loglevel to 7 in cupd-psd.conf does not give any errors about thinderbird.
If Thunderbird leaves a logfile somewhere I don't know where it is.

Anyone care to take a stab at this or throw me a bone? I'm stumped.

---

### Post by mmullis on 2009-09-26
Update:

It works if a Thunderbird is already open.

The same is true for Evolution (sort-of). It only works if the evolution background processes are running.

---

