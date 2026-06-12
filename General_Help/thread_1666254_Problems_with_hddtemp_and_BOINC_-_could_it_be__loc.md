---
title: "Problems with hddtemp and BOINC - could it be  localhost"
date: 2011-01-13
forum: General Help
---

### Post by mjjohanson on 2011-01-13
Had Maverick up and running fine but decided to start over to reconfigure the drives. 

-Then: hddtemp showed up in sensors-applet and BOINC ran the client at startup.

-Now: After installing sensors applet and related daemons, hddtemp does not display in applet even though it is running and accessible in the terminal. BOINC client does not start at boot and BOINC manager cannot connect to localhost. Running boinc-client from terminal while BOINC manager is running will cause BOINC manager to immediately make the localhost connection and the client runs with no problems.  I have tried the various config options in both and have removed and reinstalled everything in both. 

Both of the daemons (hddtemp and boinc-client) use localhost (127.0.0.1) for communication with the desktop app (sensors-applet and BOINC manager). BOINC is able to establish communication but sensors is not. lm-sensors presents the acpi and cpu sensors to sensors-applet just fine.

Thoughts and suggestions??? I would appreciate hearing from those with more knowledge and experience than I.

---

