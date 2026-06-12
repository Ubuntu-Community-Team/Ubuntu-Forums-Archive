---
title: "Recording TNT TV using mplayer and cron on karmic..."
date: 2009-11-28
forum: General Help
---

### Post by nautic on 2009-11-28
Recording TNT TV using mplayer and cron on karmic...

Hello, 
To record TNT tv with my PC, I use a script activated with crontab.
With hardy I just needed to start the PC without opening a session user.
Since I am with karmic, it does not work any more the same !
I need to start a user session corresponding to the crontab.
Otherwise the script starts well but the line which contains the mplayer command to record  tnt stream not !
On the other hand, once the recording is started, I can close or change the user session, mplayer continue to record.

Without a open user session, DVB-T can not be used or a need module witch is not already loaded ?
I'm not skilled enough to understand what 's wrong.
One thing is sure, there is something changed with regard to hardy...

Thank you for your help

Script I use :  tvrecord.sh :

#!/bin/bash
#verification du nombre d'argument :
if [ $# -eq 3 ]
then
  date=`date +%Y-%m-%d-%Hh%M`
  nomfichier=$3_$date.ts
  echo Enregistrement_Chaine_$1_$nomfichier >> /home/famille/scripts/log_enregistrement_tv.txt
  mplayer -dumpstream -dumpfile $nomfichier dvb://$1 &
  sleep $2
  kill %1
else
  echo "#############  Il manque des arguments ! ##################"
  echo "# Utilisation :                                           #"
  echo "# tvrecord chaîne temps(sec) nomdefichier                 #"
  echo "# liste des chaînes dispo :                               #"
  echo "# ARTE FRANCE2,3,4,5 M6 CANAL+ TMC BFMTV i>TELE Europe2TV #"
  echo "# Gulli Direct8 LCP TF1 NRJ12 W9                          #"
  echo "###########################################################"
fi
exit 0;

---

