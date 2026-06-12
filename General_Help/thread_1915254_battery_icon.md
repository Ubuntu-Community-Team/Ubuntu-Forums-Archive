---
title: "battery icon"
date: 2012-01-25
forum: General Help
---

### Post by tongsak77 on 2012-01-25
I have tried acpi and ibam to display the battery status in the terminal window but in vain. this is all I get:

Adapter 0: off-line
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
tongsak@yoshi:~$ /sys/class/power_supply/BAT0/energy_ful
bash: /sys/class/power_supply/BAT0/energy_ful: No such file or directory
tongsak@yoshi:~$ ibam
No apm data available.
tongsak@yoshi:~$ acpi
tongsak@yoshi:~$ display acpi
display: unable to open image `acpi':  @ error/blob.c/OpenBlob/2489.
tongsak@yoshi:~$ sudo acpi -v
acpi 1.5

Copyright (C) 2001 Grahame Bowland.
              2008 Michael Meskes.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
tongsak@yoshi:~$ sudo acpi -V
Adapter 0: off-line
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10

Please tell me what I need to do. Thank you

---

### Post by claracc on 2012-01-26
What ubuntu are you running?

This link: [http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/](http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/) can help.

Specifically:

> Battery Status

The default power indicator in Ubuntu 11.10 works out of the box, but in previous releases support was patchy at best.

For Lucid, Maverick and Natty users installing the Battery Status Applet is a no-brainer. It offers up stats on your current battery charge, grants quick access to performance scaling and Power Management settings, all within easy reach.
Battery Status is available for Ubuntu 9.10 through 11.04 via the following PPA:

    * sudo add-apt-repository ppa:iaz/battery-status && sudo apt-get update
    * sudo apt-get install battery-status

The applet will, initially, run as a standard gnome applet. To intitate &#8216;indicator applet&#8217; mode you will need to run the following command in a Terminal : -

    * /usr/lib/battery-status/battery-status --indicator

---

### Post by tongsak77 on 2012-01-27
thanks, im running ubuntu 11.10

---

### Post by tongsak77 on 2012-01-27
i tried the commands in the terminal but got the following:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
tongsak@yoshi:~$ sudo apt-get install battery-status
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package battery-status
tongsak@yoshi:~$ /usr/lib/battery-status/battery-status --indicator
bash: /usr/lib/battery-status/battery-status: No such file or directory

---

### Post by claracc on 2012-01-28
This repository ppa:iaz/battery-status is not valid for oneiric ocelot, so if you have installed you have to remove it from sources list.

I have find this link [http://askubuntu.com/questions/78979/battery-indicator-missing](http://askubuntu.com/questions/78979/battery-indicator-missing), where the answer to the question is:
> he indicator is:

    indicator-power

Uninstall the indicator

    sudo apt-get purge indicator-power

Reinstall the application

    sudo apt-get install indicator-power


But I am not on oneiric and I don't know if it is a valid solution.

---

