---
title: "Scripting Newbie Needs help to Automate"
date: 2011-04-07
forum: General Help
---

### Post by Barajqial on 2011-04-07
I've been using this script to take a text file of Users/groups/passwords and add them as a linux user and enable as a samba user.
This comes from [[COLOR=blue]http://www.linuxquestions.org/questions/programming-9/shell-script-to-add-samba-users-309812/[/COLOR]]("http://www.linuxquestions.org/questions/programming-9/shell-script-to-add-samba-users-309812/") but i've changed it abit to fit my needs
```

#!/bin/bash
#
# Ensure that root is running the script.
##
WHOAMI=`/usr/bin/whoami`
if [ $WHOAMI != "root" ]; then
echo "You must be root to add news users!"
exit 1
fi
#
clear
NEW_USERS="/home/empire/Desktop/users.txt"
cat ${NEW_USERS} | \
while read USER GROUP SMBPASS ; do
 
groupadd -f ${GROUP} #2> /dev/null
echo Group ${GROUP} added
useradd -g ${GROUP} -s /bin/true ${USER}
#(echo $SMBPASS; echo $SMBPASS) #| passwd --stdin ${USER} > /dev/null
echo Added user ${USER}
smbpasswd -L -a ${USER} #-w ${SMBPASS} > /dev/null
(echo {$SMBPASS}; echo ${SMBPASS}) #| smbpasswd -as ${USER}
echo User added to samba ${USER}
smbpasswd -L -e ${USER}
echo User Activated ${USER}
echo -e "${USER} = ${USER}" >> /etc/samba/smbusers
done

```
 
This works well and great except for when its time to enter the password then I have to manually enter them. I want to automate that part, and I'm not sure where to begin.
 
 
Thanks in advance
-Bar

---

### Post by Barajqial on 2011-04-08
Hmm a little over zealous commenting and not understanding exactly what the script did on my part problem solved:)

---

