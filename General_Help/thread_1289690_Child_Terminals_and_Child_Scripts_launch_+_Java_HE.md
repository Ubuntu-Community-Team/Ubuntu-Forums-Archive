---
title: "Child Terminals and Child Scripts launch + Java HELP!"
date: 2009-10-12
forum: General Help
---

### Post by jmclarty on 2009-10-12
Hello Ubuntu scripting pros,

I'm trying to get a script which I can launch from an icon on the desktop that will launch several programs/files/other scripts/other terminals onto specific desktops, and have them all ready almost instantaneously.  I have a script that is almost complete, however, **ubuntu seems to stop after each line of the script**, until I close the window it just launched.  Almost as if it's waiting for a window to close, before it proceeds with the rest of the script.

This is the script I have now, "MorningRoutine.sh", the file is enabled to be executed:

```

cd
cd Desktop
echo "Time for the Morning Routine"
echo "Launching MP.R, Gmail and Bloomberg Calendar on Desktop 2"
wmctrl -s 1
gedit MP.R
firefox www.gmail.com
firefox www.bloomberg.com/markets/ecalendar/index.html
echo "Launching Interactive Brokers and Positions.data on Desktop 1"
wmctrl -s 0
gedit Positions.data
# TODO: ./RunIBBeta.sh in a separate terminal - I don't know how to do this part yet.
echo "Launching R and Governance.ods on Desktop 3"
wmctrl -s 2
ooffice -o Governance.ods
# TODO: have R execute the file MP.R in this terminal, without me copying and pasting this line I have echo'd to the screen just before, for reference.
echo "source('MP.R', local = TRUE, echo = TRUE, print.eval = TRUE)"
R 
echo "Ready for Breakfast"
```This is a second script, RunIBBeta.sh, which I would like to run in a seperate terminal, but launched from the first script

```
# Script to launch IB
echo "Launching IB Beta"
cd
cd IBJts
java -cp jts.jar:pluginsupport.jar:riskfeed.jar:hsqldb.jar:jcommon-1.0.12.jar:jfreechart-1.0.9.jar:jhall.jar:other.jar:rss.jar -Xmx256M jclient.LoginFrame ./Beta
echo "Successfully Launched IB"
```If I was not clear, let me know.  Below is the pseudo for what I want:

double click icon to execute MorningRoutine.sh in a terminal
Open the file MP.R in gedit and 2 URL's on Desk 2
Open Positions.data in gedit and launch a new terminal which executes RunIBBeta.sh on Desk 1
Open Governance.ods and Execute MP.R in R on Desk 3

Thanks to any and all who can offer any words of wisdom,
Jeff

---

### Post by jmclarty on 2009-10-12
I figured out how to launch a second terminal, for the other script (see below)...now, I just need to figure out how to get the main script to continue to execute without me closing each window while it does.

```
gnome-terminal -e ./RunIBBeta.sh
```

---

### Post by oneiric on 2009-11-24
Did you find a solution for this? 

I am trying to do the exact same thing (launch 3 terminals with the command "gnome-terminal -e /home/script.sh" but the 2nd and 3rd terminals don't execute until the first terminal is closed)  but I know very little about scripting.

---

