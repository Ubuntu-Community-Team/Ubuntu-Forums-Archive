---
title: "Help needed with disk monitoring script."
date: 2011-06-08
forum: General Help
---

### Post by Trader2699 on 2011-06-08
Hello all.

I have an Ubuntu 9.04 server that I would like to be able to monitor the HDD size. I found a script online that has worked flawlessly on my other Linux servers:

[B]#!/bin/bash
# set -x
# Shell script to monitor or watch the disk space
# It will send an email to $ADMIN, if the (free available) percentage of space is >= 90%.
# -------------------------------------------------------------------------
# Set admin email so that you can get email.
ADMIN="email@mydomain.com"
# set alert level 90% is default
ALERT=75
# Exclude list of unwanted monitoring, if several partions then use "|" to separate the partitions.
# An example: EXCLUDE_LIST="/dev/hdd1|/dev/hdc5"
EXCLUDE_LIST="/auto/ripper"
#
#::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
#
function main_prog() {
while read output;
do
#echo $output
  usep=$(echo $output | awk '{ print $1}' | cut -d'%' -f1)
  partition=$(echo $output | awk '{print $2}')
  if [ $usep -ge $ALERT ] ; then
     echo "Running out of space \"$partition ($usep%)\" on server $(hostname), $(date)" | \
     mail -s "Alert: Almost out of disk space $usep%" $ADMIN
  fi
done
}

if [ "$EXCLUDE_LIST" != "" ] ; then
  df -HP | grep -vE "^Filesystem|tmpfs|cdrom|${EXCLUDE_LIST}" | awk '{print $5 " " $6}' | main_prog
else
  df -HP | grep -vE "^Filesystem|tmpfs|cdrom" | awk '{print $5 " " $6}' | main_prog
fi[/B]

Yet when I run it on this server, I get:

[B]
16: Syntax error: "(" unexpected[/B]

I am assuming this means line 16, which is:

**function main_prog() {**

Can anyone assist me with this and tell me what I am doing wrong?

---

### Post by DaithiF on 2011-06-08
that script is fine when run under bash, but I suspect you are running it under dash instead

```
$ bash blah

$ dash blah
blah: 16: Syntax error: "(" unexpected

```

how exactly are you running it?

---

### Post by Trader2699 on 2011-06-08
The script is named diskalert.sh

I try to execute it as:

sh diskalert.sh

Is this wrong?

If I run it as bash diskalert.sh

I get:

diskalert.sh: line 24: mail: command not found
diskalert.sh: line 24: mail: command not found
diskalert.sh: line 24: mail: command not found
diskalert.sh: line 24: mail: command not found

---

### Post by DaithiF on 2011-06-08
Hi, sh is symlinked to dash on your system, so by running sh yourscript you are running it with dash.

You can either run it as:
/path/to/yourscript
or
bash /path/to/yourscript
if the former then the script needs to be executable:
chmod +x /path/to/yourscript

as to the mail command error, do you have a mail agent installed?  the error is saying that the command 'mail' isn't found on your path.

---

### Post by Trader2699 on 2011-06-08
Thanks, I had just found that out, the difference between sh and bash...

Strange, the system says "sendmail" is installed, but the "mail" command isn't recognized. 

On my other systems (mostly Fedora and RHEL) this works fine.

---

