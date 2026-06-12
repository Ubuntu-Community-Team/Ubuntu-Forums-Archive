---
title: "Scheduled Tasks"
date: 2011-07-18
forum: General Help
---

### Post by brown.hornet on 2011-07-18
I am trying to create a batch file that will copy data from a Production data folder to a Dev and Beta data folder daily at a scheduled time late at night.  I have attempted to use Crontab as well as Gnome Schedule Tasks app (Crontab GUI?) with no success.  I reviewed the SYSLOG and could not see any obvious errors (assumes taht I know what too look for).  Below is the script that I am trying to run – I can successfully run the script from the command line.  Also note that I am not able to update the destination DIR permissions with out using ‘sudo’ on the chmod line.  Is it possible to run the script as root or pass the password information when the script is ran?  Finally I also wanted to know if this can be run without the user being logged in.

#!/bin/bash
#
# Daily data re-fresh for DecDev and DecBeta
# environments.  This script is ran after the
# Daily Data backup.
#

echo 'Running Data Refresh Script'

# Development Data Refresh
#
echo 'Moving data to DevData'
cp -r /usr/decind/data/ /usr/decdev/
echo 'Updating Permissions on DevData'
sudo chmod 777 -R /usr/decdev

# Beta Data Refresh
#
echo 'Moving data to BetaData'
cp -r /usr/decind/data /usr/decbeta/
echo 'Updating Permissions on BetaData'
sudo chmod 777  -R /usr/decbeta


Respectfully –

ingram

---

### Post by brown.hornet on 2011-07-18
Major_Bloodnok –

Thanks for the response – I have not been very successful in getting them.  

1. I not sure I fully understand what you are asking here – the data I am trying to copy is for a custom application that is ran out of the /usr DIR.  All I am trying to do is copy the production data to both the Dev and Beta environments.  So I believe that I need to copy within the /usr DIR?

2. Well here in Texas we don’t do things small so overkill is just in our nature :D - I did try lowering the permissions but it seems to mess up the application we are using.  I am sure it is most likely due to the fact I am having a difficult time finding out what permissions are actually needed.  The files in question are data files that all users need to be able to read and write to.  I will work on this.

3. Ok I will give that a try and see what happens.

4. Finally once I have this worked out can I schedule this to run as a user without that user actually being logged in?

Again thanks for your help.

Respectfully –

ingram

---

