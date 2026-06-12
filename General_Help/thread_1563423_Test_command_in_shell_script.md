---
title: "Test command in shell script"
date: 2010-08-29
forum: General Help
---

### Post by Mortesins93 on 2010-08-29
Hello,
I was trying to write a script, but for some reason I can't test two variables using -gt:
a=`expr $currentSize + 0`
b=`expr $fileSize + 0`
 [$a -gt $b]
this is what I get:
[22234534: not found

what is the problem? It seems like I can't check if a variable is greater than another but only if a variable is greater than a fixed number. Is that so? By the way the variables $fileSize and $currentSize exist and $a and $b have a value.

---

### Post by sharathcshekhar on 2010-08-29
Space missing? [$a -gt $b] should be [ $a -gt $b ]

---

### Post by Mortesins93 on 2010-09-02
yes that was it but now I get this:

[: 585: =: unexpected operator

what is the problem?

---

### Post by anirudhtomer on 2010-09-02
Why don't u post your shell script here. Don't forget to post it in "code" tag.

---

### Post by Mortesins93 on 2010-09-02
```
#! /bin/bash
echo "Vuoi spegnere il sistema una volta scaricato tutto? (si o no)"
read shutdown
if [ $shutdown = "si" ]
then
echo "Dopo quanti secondi?"
read secondsShutdown
fi
echo "Che processo vuoi che si chiuda una volta scaricato tutto? (se nessuno scrivere 'nessuno')"
read process
if [ $process != "nessuno" ]
then
echo "Dopo quanti secondi?"
read secondsProcesskill
fi
echo "Ogni quanti secondi vuoi che venga controllata la dimensione del file?"
read timeCheck

# Raccolta dati

i=0
a=0
while [ $i = 0 ]
do
 
echo "Dammi il nome completo"
read fileName0
echo "Dammi la dimensione (in bytes)"
read fileSize0
echo "Dammi la directory assoluta (senza barra iniziale)"
read fileDirectory0
cd /${fileDirectory0}
currentSize0=`ls -l| tr -s " "| grep "$fileName0"| cut -d " " -f5`
echo $fileSize0

a=`expr $a + 1`

sleep 3

echo "Dammi il nome completo (se non ci sono più file da controllare scrivi 'quit')"
read fileName1
if [ $fileName1 = "quit" ]
then
break
fi
echo "Dammi la dimensione (in bytes)"
read fileSize1
echo "Dammi la directory assoluta (senza barra iniziale)"
read fileDirectory1
cd /${fileDirectory1}
currentSize1=`ls -l| tr -s " "| grep "$fileName1"| cut -d " " -f5`
echo $fileSize1

a=`expr $a + 1`

sleep 3

echo "Dammi il nome completo"
read fileName2
if [ $fileName2 = "quit" ]
then
break
fi
echo "Dammi la dimensione (in bytes)"
read fileSize2
echo "Dammi la directory assoluta (senza barra iniziale)"
read fileDirectory2
cd /${fileDirectory2}
currentSize2=`ls -l| tr -s " "| grep "$fileName2"| cut -d " " -f5`
echo $fileSize2

a=`expr $a + 1`

sleep 3

echo "Dammi il nome completo"
read fileName3
if [ $fileName3 = "quit" ]
then
break
fi
echo "Dammi la dimensione (in bytes)"
read fileSize3
echo "Dammi la directory assoluta(senza barra iniziale)"
read fileDirectory3
cd /${fileDirectory3}
currentSize3=`ls -l| tr -s " "| grep "$fileName3"| cut -d " " -f5`
echo $fileSize3

a=`expr $a + 1`

sleep 3

echo "Dammi il nome completo"
read fileName4
if [ $fileName4 = "quit" ]
then
break
fi
echo "Dammi la dimensione (in bytes)"
read fileSize4
echo "Dammi la directory assoluta (senza barra iniziale)"
read fileDirectory4
cd /${fileDirectory4}
currentSize4=`ls -l| tr -s " "| grep "$fileName4"| cut -d " " -f5`
echo $fileSize4

a=`expr $a + 1`

sleep 3

echo "Dammi il nome completo"
read fileName5
if [ $fileName5 = "quit" ]
then
break
fi
echo "Dammi la dimensione (in bytes)"
read fileSize5
echo "Dammi la directory assoluta (senza barra iniziale)"
read fileDirectory5
cd /${fileDirectory5}
currentSize5=`ls -l| tr -s " "| grep "$fileName5"| cut -d " " -f5`
echo $fileSize5

a=`expr $a + 1`

sleep 3

echo "Dammi il nome completo"
read fileName6
if [ $fileName6 = "quit" ]
then
break
fi
echo "Dammi la dimensione (in bytes)"
read fileSize6
echo "Dammi la directory assoluta (senza barra iniziale)"
read fileDirectory6
cd /${fileDirectory6}
currentSize6=`ls -l| tr -s " "| grep "$fileName6"| cut -d " " -f5`
echo $fileSize6

a=`expr $a + 1`

sleep 3

echo "Dammi il nome completo"
read fileName7
if [ $fileName7 = "quit" ]
then
break
fi
echo "Dammi la dimensione (in bytes)"
read fileSize7
echo "Dammi la directory assoluta (senza barra iniziale)"
read fileDirectory7
cd /${fileDirectory7}
currentSize7=`ls -l| tr -s " "| grep "$fileName7"| cut -d " " -f5`
echo $fileSize7

a=`expr $a + 1`

sleep 3

echo "Dammi il nome completo"
read fileName8
if [ $fileName8 = "quit" ]
then
break
fi
echo "Dammi la dimensione (in bytes)"
read fileSize8
echo "Dammi la directory assoluta (senza barra iniziale)"
read fileDirectory8
cd /{fileDirectory8}
currentSize8=`ls -l| tr -s " "| grep "$fileName8"| cut -d " " -f5`
echo $fileSize8

a=`expr $a + 1`

sleep 3

echo "Dammi il nome completo"
read fileName9
if [ $fileName9 = "quit" ]
then
break
fi
echo "Dammi la dimensione (in bytes)"
read fileSize9
echo "Dammi la directory assoluta (senza barra iniziale)"
read fileDirectory9
cd /${fileDirectory9}
currentSize9=`ls -l| tr -s " "| grep "$fileName9"| cut -d " " -f5`
echo $fileSize9

a=`expr $a + 1`

i=`expr $i + 1`
done

stop=0

# Elaborazione dati
# Fin qui funziona


case ${a} in
1)
until [ $currentSize0 -gt $fileSize0 ]

do

if [ $currentSize0TMP = $currentSize0 ]
then
currentSize0TMP=`expr $currentSize0TMP + 1`
xfce4-terminal -e 'sh /home/axel/DownloadControl/DownloadControl_alert'
sleep 5
else
sleep $timeCheck
currentSize0TMP=$currentSize0

currentSize0=`ls -l| tr -s " "| grep "$fileName0"| cut -d " " -f5`

fi
sleep 5
done

if [ $process != "nessuno" ]
then
echo "Tra $secondsProcesskill secondi chiudo il programma $process"
sleep $secondsProcesskill
pkill $process
fi
if [ $shutdown = "si" ]
then
echo "Tra $secondsShutdown secondi spengo il sistema" 
fi
;;
2)
until [ $currentSize0 -gt $fileSize0 -a $currentSize1 -gt $fileSize1 ]

do

if [ $currentSize0TMP = $currentSize0 -o $currentSize1TMP = $currentSize1 ]
then
currentSize0TMP=`expr $currentSize0TMP + 1`
currentSize1TMP=`expr $currentSize1TMP + 1`
xfce4-terminal -e 'sh /home/axel/DownloadControl/DownloadControl_alert'
sleep 5
else
sleep $timeCheck
currentSize0TMP=$currentSize0
currentSize1TMP=$currentSize1

currentSize0=`ls -l| tr -s " "| grep "$fileName0"| cut -d " " -f5`
currentSize1=`ls -l| tr -s " "| grep "$fileName1"| cut -d " " -f5`

fi
done

if [ $process != "nessuno" ]
then
echo "Tra $secondsProcesskill secondi chiudo il programma $process"
sleep $secondsProcesskill
pkill $process
fi
if [ $shutdown = "si" ]
then
echo "Tra $secondsShutdown secondi spengo il sistema" 
fi
;;

3)
until [ $currentSize0 -gt $fileSize0 -a $currentSize1 -gt $fileSize1 -a $currentSize2 -gt $fileSize2 ]

do

if [ $currentSize0TMP = $currentSize0 -o $currentSize1TMP = $currentSize1  -o $currentSize2TMP = $currentSize2 ]
then
currentSize0TMP=`expr $currentSize0TMP + 1`
currentSize1TMP=`expr $currentSize1TMP + 1`
currentSize2TMP=`expr $currentSize2TMP + 1`
xfce4-terminal -e 'sh /home/axel/DownloadControl/DownloadControl_alert'
sleep 5
else
sleep $timeCheck
currentSize0TMP=$currentSize0
currentSize1TMP=$currentSize1
currentSize2TMP=$currentSize2

currentSize0=`ls -l| tr -s " "| grep "$fileName0"| cut -d " " -f5`
currentSize1=`ls -l| tr -s " "| grep "$fileName1"| cut -d " " -f5`
currentSize2=`ls -l| tr -s " "| grep "$fileName2"| cut -d " " -f5`

fi
done

if [ $process != "nessuno" ]
then
echo "Tra $secondsProcesskill secondi chiudo il programma $process"
sleep $secondsProcesskill
pkill $process
fi
if [ $shutdown = "si" ]
then
echo "Tra $secondsShutdown secondi spengo il sistema" 
fi
;;

4)
until [ $currentSize0 -gt $fileSize0 -a $currentSize1 -gt $fileSize1 -a $currentSize2 -gt $fileSize2 -a $currentSize3 -gt $fileSize3 ]

do

if [ $currentSize0TMP = $currentSize0 -o $currentSize1TMP = $currentSize1  -o $currentSize2TMP = $currentSize2 -o $currentSize3TMP = $currentSize3 ]
then
currentSize0TMP=`expr $currentSize0TMP + 1`
currentSize1TMP=`expr $currentSize1TMP + 1`
currentSize2TMP=`expr $currentSize2TMP + 1`
currentSize3TMP=`expr $currentSize3TMP + 1`
xfce4-terminal -e 'sh /home/axel/DownloadControl/DownloadControl_alert'
sleep 5
else
sleep $timeCheck
currentSize0TMP=$currentSize0
currentSize1TMP=$currentSize1
currentSize2TMP=$currentSize2
currentSize3TMP=$currentSize3

currentSize0=`ls -l| tr -s " "| grep "$fileName0"| cut -d " " -f5`
currentSize1=`ls -l| tr -s " "| grep "$fileName1"| cut -d " " -f5`
currentSize2=`ls -l| tr -s " "| grep "$fileName2"| cut -d " " -f5`
currentSize3=`ls -l| tr -s " "| grep "$fileName3"| cut -d " " -f5`
fi
done

if [ $process != "nessuno" ]
then
echo "Tra $secondsProcesskill secondi chiudo il programma $process"
sleep $secondsProcesskill
pkill $process
fi
if [ $shutdown = "si" ]
then
echo "Tra $secondsShutdown secondi spengo il sistema" 
fi
;;

5)
until [ $currentSize0 -gt $fileSize0 -a $currentSize1 -gt $fileSize1 -a $currentSize2 -gt $fileSize2 -a $currentSize3 -gt $fileSize3 -a $currentSize4 -gt $fileSize4 ]

do

if [ $currentSize0TMP = $currentSize0 -o $currentSize1TMP = $currentSize1  -o $currentSize2TMP = $currentSize2 -o $currentSize3TMP = $currentSize3 -o $currentSize4TMP = $currentSize4 ]
then
currentSize0TMP=`expr $currentSize0TMP + 1`
currentSize1TMP=`expr $currentSize1TMP + 1`
currentSize2TMP=`expr $currentSize2TMP + 1`
currentSize3TMP=`expr $currentSize3TMP + 1`
currentSize4TMP=`expr $currentSize4TMP + 1`
xfce4-terminal -e 'sh /home/axel/DownloadControl/DownloadControl_alert'
sleep 5
else
sleep $timeCheck
currentSize0TMP=$currentSize0
currentSize1TMP=$currentSize1
currentSize2TMP=$currentSize2
currentSize3TMP=$currentSize3
currentSize4TMP=$currentSize4

currentSize0=`ls -l| tr -s " "| grep "$fileName0"| cut -d " " -f5`
currentSize1=`ls -l| tr -s " "| grep "$fileName1"| cut -d " " -f5`
currentSize2=`ls -l| tr -s " "| grep "$fileName2"| cut -d " " -f5`
currentSize3=`ls -l| tr -s " "| grep "$fileName3"| cut -d " " -f5`
currentSize4=`ls -l| tr -s " "| grep "$fileName4"| cut -d " " -f5`
fi
done

if [ $process != "nessuno" ]
then
echo "Tra $secondsProcesskill secondi chiudo il programma $process"
sleep $secondsProcesskill
pkill $process
fi
if [ $shutdown = "si" ]
then
echo "Tra $secondsShutdown secondi spengo il sistema" 
fi
;;

6)
until [ $currentSize0 -gt $fileSize0 -a $currentSize1 -gt $fileSize1 -a $currentSize2 -gt $fileSize2 -a $currentSize3 -gt $fileSize3 -a $currentSize4 -gt $fileSize4 -a $currentSize5 -gt $fileSize5 ]

do

if [ $currentSize0TMP = $currentSize0 -o $currentSize1TMP = $currentSize1  -o $currentSize2TMP = $currentSize2 -o $currentSize3TMP = $currentSize3 -o $currentSize4TMP = $currentSize4 -o $currentSize5TMP = $currentSize5 ]
then
currentSize0TMP=`expr $currentSize0TMP + 1`
currentSize1TMP=`expr $currentSize1TMP + 1`
currentSize2TMP=`expr $currentSize2TMP + 1`
currentSize3TMP=`expr $currentSize3TMP + 1`
currentSize4TMP=`expr $currentSize4TMP + 1`
currentSize5TMP=`expr $currentSize5TMP + 1`
xfce4-terminal -e 'sh /home/axel/DownloadControl/DownloadControl_alert'
sleep 5
sleep $timeCheck
currentSize0TMP=$currentSize0
currentSize1TMP=$currentSize1
currentSize2TMP=$currentSize2
currentSize3TMP=$currentSize3
currentSize4TMP=$currentSize4
currentSize5TMP=$currentSize5

currentSize0=`ls -l| tr -s " "| grep "$fileName0"| cut -d " " -f5`
currentSize1=`ls -l| tr -s " "| grep "$fileName1"| cut -d " " -f5`
currentSize2=`ls -l| tr -s " "| grep "$fileName2"| cut -d " " -f5`
currentSize3=`ls -l| tr -s " "| grep "$fileName3"| cut -d " " -f5`
currentSize4=`ls -l| tr -s " "| grep "$fileName4"| cut -d " " -f5`
currentSize5=`ls -l| tr -s " "| grep "$fileName5"| cut -d " " -f5`
fi
done

if [ $process != "nessuno" ]
then
echo "Tra $secondsProcesskill secondi chiudo il programma $process"
sleep $secondsProcesskill
pkill $process
fi
if [ $shutdown = "si" ]
then
echo "Tra $secondsShutdown secondi spengo il sistema" 
fi
;;

7)
until [ $currentSize0 -gt $fileSize0 -a $currentSize1 -gt $fileSize1 -a $currentSize2 -gt $fileSize2 -a $currentSize3 -gt $fileSize3 -a $currentSize4 -gt $fileSize4 -a $currentSize5 -gt $fileSize5 -a $currentSize6 -gt $fileSize6 ]

do

if [ $currentSize0TMP = $currentSize0 -o $currentSize1TMP = $currentSize1  -o $currentSize2TMP = $currentSize2 -o $currentSize3TMP = $currentSize3 -o $currentSize4TMP = $currentSize4 -o $currentSize5TMP = $currentSize5 -o $currentSize6TMP = $currentSize6 ]
then
currentSize0TMP=`expr $currentSize0TMP + 1`
currentSize1TMP=`expr $currentSize1TMP + 1`
currentSize2TMP=`expr $currentSize2TMP + 1`
currentSize3TMP=`expr $currentSize3TMP + 1`
currentSize4TMP=`expr $currentSize4TMP + 1`
currentSize5TMP=`expr $currentSize5TMP + 1`
currentSize6TMP=`expr $currentSize6TMP + 1`
xfce4-terminal -e 'sh /home/axel/DownloadControl/DownloadControl_alert'
sleep 5
else
sleep $timeCheck
currentSize0TMP=$currentSize0
currentSize1TMP=$currentSize1
currentSize2TMP=$currentSize2
currentSize3TMP=$currentSize3
currentSize4TMP=$currentSize4
currentSize5TMP=$currentSize5
currentSize6TMP=$currentSize6

currentSize0=`ls -l| tr -s " "| grep "$fileName0"| cut -d " " -f5`
currentSize1=`ls -l| tr -s " "| grep "$fileName1"| cut -d " " -f5`
currentSize2=`ls -l| tr -s " "| grep "$fileName2"| cut -d " " -f5`
currentSize3=`ls -l| tr -s " "| grep "$fileName3"| cut -d " " -f5`
currentSize4=`ls -l| tr -s " "| grep "$fileName4"| cut -d " " -f5`
currentSize5=`ls -l| tr -s " "| grep "$fileName5"| cut -d " " -f5`
currentSize6=`ls -l| tr -s " "| grep "$fileName6"| cut -d " " -f5`
fi
done

if [ $process != "nessuno" ]
then
echo "Tra $secondsProcesskill secondi chiudo il programma $process"
sleep $secondsProcesskill
pkill $process
fi
if [ $shutdown = "si" ]
then
echo "Tra $secondsShutdown secondi spengo il sistema" 
fi
;;

8)
until [ $currentSize0 -gt $fileSize0 -a $currentSize1 -gt $fileSize1 -a $currentSize2 -gt $fileSize2 -a $currentSize3 -gt $fileSize3 -a $currentSize4 -gt $fileSize4 -a $currentSize5 -gt $fileSize5 -a $currentSize6 -gt $fileSize6 -a $currentSize7 ]

do

if [ $currentSize0TMP = $currentSize0 -o $currentSize1TMP = $currentSize1  -o $currentSize2TMP = $currentSize2 -o $currentSize3TMP = $currentSize3 -o $currentSize4TMP = $currentSize4 -o $currentSize5TMP = $currentSize5 -o $currentSize6TMP = $currentSize6 -o $currentSize7TMP = $currentSize7 ]
then
currentSize0TMP=`expr $currentSize0TMP + 1`
currentSize1TMP=`expr $currentSize1TMP + 1`
currentSize2TMP=`expr $currentSize2TMP + 1`
currentSize3TMP=`expr $currentSize3TMP + 1`
currentSize4TMP=`expr $currentSize4TMP + 1`
currentSize5TMP=`expr $currentSize5TMP + 1`
currentSize6TMP=`expr $currentSize6TMP + 1`
currentSize7TMP=`expr $currentSize7TMP + 1`
xfce4-terminal -e 'sh /home/axel/DownloadControl/DownloadControl_alert'
sleep 5
else
sleep $timeCheck
currentSize0TMP=$currentSize0
currentSize1TMP=$currentSize1
currentSize2TMP=$currentSize2
currentSize3TMP=$currentSize3
currentSize4TMP=$currentSize4
currentSize5TMP=$currentSize5
currentSize6TMP=$currentSize6
currentSize7TMP=$currentSize7

currentSize0=`ls -l| tr -s " "| grep "$fileName0"| cut -d " " -f5`
currentSize1=`ls -l| tr -s " "| grep "$fileName1"| cut -d " " -f5`
currentSize2=`ls -l| tr -s " "| grep "$fileName2"| cut -d " " -f5`
currentSize3=`ls -l| tr -s " "| grep "$fileName3"| cut -d " " -f5`
currentSize4=`ls -l| tr -s " "| grep "$fileName4"| cut -d " " -f5`
currentSize5=`ls -l| tr -s " "| grep "$fileName5"| cut -d " " -f5`
currentSize6=`ls -l| tr -s " "| grep "$fileName6"| cut -d " " -f5`
currentSize7=`ls -l| tr -s " "| grep "$fileName7"| cut -d " " -f5`
fi
done

if [ $process != "nessuno" ]
then
echo "Tra $secondsProcesskill secondi chiudo il programma $process"
sleep $secondsProcesskill
pkill $process
fi
if [ $shutdown = "si" ]
then
echo "Tra $secondsShutdown secondi spengo il sistema" 
fi
;;

9)
until [ $currentSize0 -gt $fileSize0 -a $currentSize1 -gt $fileSize1 -a $currentSize2 -gt $fileSize2 -a $currentSize3 -gt $fileSize3 -a $currentSize4 -gt $fileSize4 -a $currentSize5 -gt $fileSize5 -a $currentSize6 -gt $fileSize6 -a $currentSize7 -gt $fileSize7 -a $currentSize8 -gt $fileSize8 ]

do

if [ $currentSize0TMP = $currentSize0 -o $currentSize1TMP = $currentSize1  -o $currentSize2TMP = $currentSize2 -o $currentSize3TMP = $currentSize3 -o $currentSize4TMP = $currentSize4 -o $currentSize5TMP = $currentSize5 -o $currentSize6TMP = $currentSize6 -o $currentSize7TMP = $currentSize7 -o $currentSize8TMP = $currentSize8 ]
then
currentSize0TMP=`expr $currentSize0TMP + 1`
currentSize1TMP=`expr $currentSize1TMP + 1`
currentSize2TMP=`expr $currentSize2TMP + 1`
currentSize3TMP=`expr $currentSize3TMP + 1`
currentSize4TMP=`expr $currentSize4TMP + 1`
currentSize5TMP=`expr $currentSize5TMP + 1`
currentSize6TMP=`expr $currentSize6TMP + 1`
currentSize7TMP=`expr $currentSize7TMP + 1`
currentSize8TMP=`expr $currentSize8TMP + 1`
xfce4-terminal -e 'sh /home/axel/DownloadControl/DownloadControl_alert'
sleep 5
else
sleep $timeCheck
currentSize0TMP=$currentSize0
currentSize1TMP=$currentSize1
currentSize2TMP=$currentSize2
currentSize3TMP=$currentSize3
currentSize4TMP=$currentSize4
currentSize5TMP=$currentSize5
currentSize6TMP=$currentSize6
currentSize7TMP=$currentSize7
currentSize8TMP=$currentSize8

currentSize0=`ls -l| tr -s " "| grep "$fileName0"| cut -d " " -f5`
currentSize1=`ls -l| tr -s " "| grep "$fileName1"| cut -d " " -f5`
currentSize2=`ls -l| tr -s " "| grep "$fileName2"| cut -d " " -f5`
currentSize3=`ls -l| tr -s " "| grep "$fileName3"| cut -d " " -f5`
currentSize4=`ls -l| tr -s " "| grep "$fileName4"| cut -d " " -f5`
currentSize5=`ls -l| tr -s " "| grep "$fileName5"| cut -d " " -f5`
currentSize6=`ls -l| tr -s " "| grep "$fileName6"| cut -d " " -f5`
currentSize7=`ls -l| tr -s " "| grep "$fileName7"| cut -d " " -f5`
currentSize8=`ls -l| tr -s " "| grep "$fileName8"| cut -d " " -f5`
fi
done

if [ $process != "nessuno" ]
then
echo "Tra $secondsProcesskill secondi chiudo il programma $process"
sleep $secondsProcesskill
pkill $process
fi
if [ $shutdown = "si" ]
then
echo "Tra $secondsShutdown secondi spengo il sistema" 
fi
;;

10)
until [ $currentSize0 -gt $fileSize0 -a $currentSize1 -gt $fileSize1 -a $currentSize2 -gt $fileSize2 -a $currentSize3 -gt $fileSize3 -a $currentSize4 -gt $fileSize4 -a $currentSize5 -gt $fileSize5 -a $currentSize6 -gt $fileSize6 -a $currentSize7 -gt $fileSize7 -a $currentSize8 -gt $fileSize8 -a $currentSize9 -gt $fileSize9 ]

do

if [ $currentSize0TMP = $currentSize0 -o $currentSize1TMP = $currentSize1  -o $currentSize2TMP = $currentSize2 -o $currentSize3TMP = $currentSize3 -o $currentSize4TMP = $currentSize4 -o $currentSize5TMP = $currentSize5 -o $currentSize6TMP = $currentSize6 -o $currentSize7TMP = $currentSize7 -o $currentSize8TMP = $currentSize8 -o $currentSize9TMP = $currentSize9 ]
then
currentSize0TMP=`expr $currentSize0TMP + 1`
currentSize1TMP=`expr $currentSize1TMP + 1`
currentSize2TMP=`expr $currentSize2TMP + 1`
currentSize3TMP=`expr $currentSize3TMP + 1`
currentSize4TMP=`expr $currentSize4TMP + 1`
currentSize5TMP=`expr $currentSize5TMP + 1`
currentSize6TMP=`expr $currentSize6TMP + 1`
currentSize7TMP=`expr $currentSize7TMP + 1`
currentSize8TMP=`expr $currentSize8TMP + 1`
currentSize9TMP=`expr $currentSize9TMP + 1`
xfce4-terminal -e 'sh /home/axel/DownloadControl/DownloadControl_alert'
sleep 5
else
sleep $timeCheck
currentSize0TMP=$currentSize0
currentSize1TMP=$currentSize1
currentSize2TMP=$currentSize2
currentSize3TMP=$currentSize3
currentSize4TMP=$currentSize4
currentSize5TMP=$currentSize5
currentSize6TMP=$currentSize6
currentSize7TMP=$currentSize7
currentSize8TMP=$currentSize8
currentSize9TMP=$currentSize9

currentSize0=`ls -l| tr -s " "| grep "$fileName0"| cut -d " " -f5`
currentSize1=`ls -l| tr -s " "| grep "$fileName1"| cut -d " " -f5`
currentSize2=`ls -l| tr -s " "| grep "$fileName2"| cut -d " " -f5`
currentSize3=`ls -l| tr -s " "| grep "$fileName3"| cut -d " " -f5`
currentSize4=`ls -l| tr -s " "| grep "$fileName4"| cut -d " " -f5`
currentSize5=`ls -l| tr -s " "| grep "$fileName5"| cut -d " " -f5`
currentSize6=`ls -l| tr -s " "| grep "$fileName6"| cut -d " " -f5`
currentSize7=`ls -l| tr -s " "| grep "$fileName7"| cut -d " " -f5`
currentSize8=`ls -l| tr -s " "| grep "$fileName8"| cut -d " " -f5`
currentSize9=`ls -l| tr -s " "| grep "$fileName9"| cut -d " " -f5`
fi
done

if [ $process != "nessuno" ]
then
echo "Tra $secondsProcesskill secondi chiudo il programma $process"
sleep $secondsProcesskill
pkill $process
fi
if [ $shutdown = "si" ]
then
echo "Tra $secondsShutdown secondi spengo il sistema" 
fi
;;
esac
```

---

### Post by Mortesins93 on 2010-09-02
I didn't translate because I think it is not relevant, but if you want, I can.
By the way, the script is very long because I couldn't manage to put all the different situations in one loop. Do you know a way??
Thanks

---

### Post by KeyserSoze93 on 2010-09-03
> **Mortesins93 said:**
> I didn't translate because I think it is not relevant, but if you want, I can.
By the way, the script is very long because I couldn't manage to put all the different situations in one loop. Do you know a way??
Thanks

A few notes:

First, you must use == to test equality. Also, it is recommended to encase variables in quotes in tests.

Why? Because if they equal an empty string, the shell won't be able to understand the expression after it has expanded them.

Example:

```

if [ $a = "blah" ]

```

becomes

```

if [ "$a" == "blah" ]

```

Likewise for your "while" loop.

You can also do shell arithmetic by using this convention, which may be slightly faster:

```

a=$[a + 4]

```

You could try changing the syntax of the ifs and see if you're still in trouble.

---

### Post by Mortesins93 on 2010-09-04
Thank you, but I don't think it works from this script:
#! /bin/bash
a="blah"
if [ "$a" == "blah" ]
then
echo "it works"
else
echo "no"
fi

I get this:

axel@axel-laptop:~/Scripts/Junk$ sh provaFOR
[: 8: blah: unexpected operator
no

As you can see I still get the "unexpected operator", and if I don't put the "fi" I get this message "provaFOR: 8: Syntax error: end of file unexpected (expecting "fi")"
By the way, I had already tried the double equal sign because I thought it was like javascript but it didn't work. So what is the problem?

---

### Post by AlphaLexman on 2010-09-04
Change:
> **Mortesins93 said:**
> if [ "$a" == "blah" ]
to:
```
if [[ "$a" == "blah" ]]
```

---

### Post by Mortesins93 on 2010-09-05
doesn't work

---

### Post by AlphaLexman on 2010-09-06
Re-post your latest script...  I didn't find ANY double equal signs ( == ) in your original code.

Edit: Also, remove the 'space' in the sha-bang between the #! and the /bin/bash to get:
```
#!/bin/bash
```

---

### Post by Mortesins93 on 2010-09-07
I haven't changed a thing on my original script, I just made another simple script to test out your suggestions and here it is:
```
#!/bin/bash
a="blah"
if [[ "$a" == "blah" ]]
then
echo "it works"
else
echo "no"
fi
```

but it doesn't work because I get this answer:

axel@axel-laptop:~/Scripts/Junk$ sh prova
prova: 8: [[: not found
no
axel@axel-laptop:~/Scripts/Junk$ 

when I should get "it works".
So why doesn't this script work??

---

### Post by Mortesins93 on 2010-09-07
So I tried this instead:

```
#!/bin/bash
a="blah"
if [ "$a" = "blah" ]
then
echo "it works"
else
echo "no"
fi
```

and I get this:

axel@axel-laptop:~/Scripts/Junk$ sh prova2
it works
axel@axel-laptop:~/Scripts/Junk$ 

and it works so I guess removing the space from "#! /bin/bash" was the solution to my problem. Thank you.

---

