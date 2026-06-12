---
title: "Auto Sleep/Hibernate (without a Desktop GUI)"
date: 2009-10-29
forum: General Help
---

### Post by Methanoid on 2009-10-29
Right I have searched and not found an answer so here goes with the problem.

I have a minimal Ubuntu install without desktop as it boots straight into XBMC for my HTPC duties. The box also runs as a download box in the background. I have Wake on Lan enabled which means I can wake the box remotely from iPhone and start it downloading stuff but I want to get it to sleep (standby or hibernate) when not in use. In Winblows its simple - set it to Hibernate after 10 mins of inactivity. How is this done in Ubuntu WITHOUT having a desktop to config it? 

I should add I don't want it hibernating if I am downloading or if I am streaming a video from my other network boxes - so it needs to be somewhat clever

Any help is appreciated. I am really getting rather impressed with Ubuntu!!

---

### Post by albandy on 2009-10-29
make an user to do this stuf (download, streaming, etc ...)
then monitorize the processes of this user, if no processes running launch the hibernate command.

Yo can see how hibernate works in this script:  /etc/acpi/hibernate.sh

for example:
#! /bin/bash
while :
do
RESULT=$(ps -u userx | grep -v PID)
if [ "$RESULT" == "" ]
then 
launch hibernate command
fi
sleep 10
done

---

