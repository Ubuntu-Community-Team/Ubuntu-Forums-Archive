---
title: "Ubuntu and grep /egrep"
date: 2012-05-10
forum: General Help
---

### Post by 01blackerado on 2012-05-10
Hello,

Im trying to get some help with a script that was originally written in Amazon Linux flavor. I test this script on a RHEL server and it also works fine...but when i try to run this script on ubuntu, it does nothing... i dont even get an error message!!

Heres the script.... it is designed to describe an EC2 instance, grep the name OKR and stop any instance matching the OKR name:

#####################################################

```

#!/bin/bash

yesterday=`date -d 'yesterday' +"%m%d%Y"`
today=`date  +"%m%d%Y"`
logfile=/home/ubuntu/logs/shutdown_${today}.log

# set up some email vals
fromAddress="catalog.ec2@abc.com"
toAddress="gsc-all@abc.com"

# We're going to have to mangle some output to get the fields we want 
# first we set the field separator to newline, so that each array element will contain one instance's id and name
IFS=$'\n'

# now we use the ec2 api to get instance info.  We call describe instances, look only at lines with the word Name (which is the actually a TAG,
# filter further by looking only at lines with dev or staging, and then pull the third and fifth fields, and store in an array
runningInst=($(ec2-describe-instances -H --filter instance-state-name=running  | grep Name | egrep -i 'OKR : dev|OKR : staging' |  cut -f 3,5))

echo -ne "The following instances will be shutdown in 5 minutes:\r" > ${logfile}

# so now we have an array with an element for each instance to shut down.  each element is in the form of id<tab>name
for inst in "${runningInst[@]}"
do
 # add to the email notification
 echo ${inst} >> ${logfile}
done

# email the log
#/usr/sbin/sendmail -oi -t << EOF
#From: ${fromAddress} 
#To:   ${toAddress}
#Subject: Warning:  Auto Instance shutdown in 5 minutes
#`cat ${logfile}`
#EOF

sleep 1

for inst in "${runningInst[@]}"
do
 # using just the instance id, stop them
 ec2-stop-instances ${inst:0:10}
done

```

#########################################################

The hiccup seems to happen when it reaches:

ec2-describe-instances -H --filter instance-state-name=running  | grep Name | egrep -i 'OKR : dev|OKR : staging'

If anyone can tell me what im missing that would be great.

Thanks,

SOLVED!!!!

Should've checked the ec2 tools version... it was outdated

---

