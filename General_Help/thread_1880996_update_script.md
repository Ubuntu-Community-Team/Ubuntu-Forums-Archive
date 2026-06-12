---
title: "update script"
date: 2011-11-14
forum: General Help
---

### Post by Synoc on 2011-11-14
every time I ssh into my server it tells me I have updates I should install. I do so every time but it's getting to be a hassle so I want to create  a script and just run that. I was wondering if this script will work? I want it it to tell me if it failed any part of it. I have tested this, after an update so it had not cleared my access yet.

```

#!/bin/bash
#this script is for updating the OS and resquires sudo priveleges. 
A=$NULL
B=$NULL
C=$NULL
function update (){
        sudo apt-get update
}

function upgrade (){
        sudo apt-get upgrade
}
function permission (){
echo "This test requires administrator privileges."
echo "Are you an administrator and/or have sudo privileges?(y,N?)"
read ANSWER
ANSWER=`echo $ANSWER | tr a-z A-Z`
if [[ $ANSWER = "$NULL" ]]
then ANSWER=N
fi

case $ANSWER in
        YES|Y)
                update
                A=$?
                upgrade
                B=$?
                clear
                if (( $A == 0 ))
                then
                echo "Update completed successfully"
                else
                echo "Update did not complete sucessfully"
                fi
                if (( $B == 0 ))
                then
                echo "Upgrade completed successfully"
                else
                echo "Upgrade did not complete successfully"
                fi ;;
        NO | N)
                echo "You do not have sufficient privileges to perform this task"
exit ;;
        *)
                echo "Please answer the question with \"Yes\" or \"No\".";;
esac
}
permission


```

---

### Post by Synoc on 2011-11-15
edit. I would LIKE this to automatically check the sudoers file to see if the person does in fact have permission to use the script. right now all I can do is politely ask thee person

---

