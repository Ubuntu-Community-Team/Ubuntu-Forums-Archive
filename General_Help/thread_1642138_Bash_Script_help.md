---
title: "Bash Script help"
date: 2010-12-10
forum: General Help
---

### Post by hantechbl on 2010-12-10
I'm trying to make a script and what I get is "line 43 Unexpected end of file no matter what Option I choose. Please help me, I don't know what I am doing wrong.
```
#!/bin/sh
#MineOSManagement APP
#Please notify me if you are modifying the program
#at wolf@lb543.co.cc
#--------------------------------------------------
#Changelog:
#V3 and under: Ridiculously unusable
#v4 Major Release (MineosV1)
#--------------------------------------------------
osver="MineOS V0.7.0"
installdir="/home/server/mc/"
tempdir="/home/server/temp/MC/"
header="echo MineOS V0.7.0"
header2="echo -------------"
clear
echo Initializing...
$header
$header2
echo Select one of the below to continue, Awaiting user Input.
echo     #       Description
echo     0      Update MineOS
echo     1      Install Minecraft
echo     2      Install Hmod
echo     3      Update Minecraft
echo     4      Update Hmod
echo     5      Remove Minecraft/Hmod and all plugins
echo     6      Manage Plugins
echo     7      Execute Minecraft
echo     8      Execute Hmod
read $opt
if [ $opt == 0 ]; then sh /home/server/mos/update.sh
elif [ $opt == 1 ]; then sh /home/server/mos/mci.sh
elif [ $opt == 2 ]; then sh /home/server/mos/hmi.sh
elif [ $opt == 3 ]; then sh /home/server/mos/mcu.sh
elif [ $opt == 4 ]; then sh /home/server/mos/hcu.sh
elif [ $opt == 5 ]; then sh /home/server/mos/rm.sh
elif [ $opt == 6 ]; then sh /home/server/mos/mm.sh
elif [ $opt == 7 ]; then sh /home/server/mos/smc.sh
elif [ $opt == 8 ]; then sh /home/server/mos/shm.sh
else exit
fi
exit
```
It's bash, and also how would I make it so I can run it with a single command like how you run apt-get I copied it to /bin/ and gave it permissions (777) but I have to run mineos.sh to get it to say anything and then it says bad interpreter, How would I fix the sh-bang I think it's called.  Thanks.

---

### Post by hantechbl on 2010-12-11
help please

---

### Post by Spyderkid on 2010-12-11
what is your script about what are you trying to do?

---

### Post by hantechbl on 2010-12-11
Configuration of minecraft, but it doesn't load the files it says: Unexpected end, I don't know why it doesn't load the other components. It is supposed to load the other script, but even then it doesn't do that.

---

### Post by AlphaLexman on 2010-12-11
Try deleting the last line 'exit'. the script should terminate on it's own with status 0.

---

### Post by hantechbl on 2010-12-11
Ok, lemme try.

---

### Post by hantechbl on 2010-12-11
Pasted output: [http://mineos.co.cc/images/](http://mineos.co.cc/images/)

---

### Post by AlphaLexman on 2010-12-11
I would consider re-writing the script to use /bin/bash and the 'case' built-in. It seems more suited to script menu options.

---

### Post by hantechbl on 2010-12-11
Can you give me an example on how to use case?

---

### Post by AlphaLexman on 2010-12-11
This is not a complete script, but a relevant example...
```
#!/bin/bash
read $opt
case $opt in
	0)	sh /home/server/mos/update.sh ;;
	1)	sh /home/server/mos/mci.sh ;;
	2)	sh /home/server/mos/hmi.sh ;;
	3)	sh /home/server/mos/mcu.sh ;;
	4)	sh /home/server/mos/hcu.sh ;;
	5)	sh /home/server/mos/rm.sh ;;
	6)	sh /home/server/mos/mm.sh ;;
	7)	sh /home/server/mos/smc.sh ;;
	8)	sh /home/server/mos/shm.sh ;;
esac
```

---

### Post by hantechbl on 2010-12-11
Thanks.

---

### Post by hantechbl on 2010-12-11
Now it says:
': not a valid identifierd: '
./mineos.sh: line 31 syntax error near unexpected token '$'in\r''
'/mineos.sh: line31: 'case $opt in

---

### Post by AlphaLexman on 2010-12-11
Make sure you change the 'shebang' to:
```
#!/bin/bash
```
The 'sh' shell which points to 'dash' does not have a built-in 'case' statement.

---

