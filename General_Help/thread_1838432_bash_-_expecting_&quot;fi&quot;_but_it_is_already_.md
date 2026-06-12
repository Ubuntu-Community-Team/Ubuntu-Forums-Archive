---
title: "bash - expecting &quot;fi&quot; but it is already there"
date: 2011-09-03
forum: General Help
---

### Post by SeaKing on 2011-09-03
I've wrote a little bash script to ease the installation of programs which are not part of the standard installation of ubuntu:

```

#! /bin/bash
#installing ubuntu-restricted-extras vlc, SUN Java, handbrake, bumblebee (hybrid graphics management tool), skype, pidgin, Thunderbird 
echo ""
echo ""
echo "Willkommen bei der Installationsroutine fuer das Asus X5MSN"
echo "------------------------------------------------------------"
echo ""
if [ "$(whoami)" != "root" ]; 
then 
    echo "Das Script muss mit root-Rechten ausgefuehrt werden!"
    echo "Nutze: 'sudo ./script.sh'"
    echo ""
else
echo "Installation der Ubuntu-Restricted-Extras ..."
apt-get -y install ubuntu-restricted-extras
echo "done"
sleep 5
echo "Installation des VLC-Players ..."
echo "--------------------------------"
apt-get -y install vlc vlc-data  
echo "done"
sleep 5
echo "Hinzufuegen der PPA: Paketquellen fuer SUN JAVA, Handbrake und bumblebee ..."
echo "---------------------------------------------------------------------------"
add-apt-repository ppa:ferramroberto/java 
add-apt-repository ppa:stebbins/handbrake-releases
add-apt-repository ppa:mj-casalogic/bumblebee
cp /etc/apt/sources.list /etc/apt/sources.list.bak 
sh -c 'echo "deb http://archive.canonical.com/ubuntu natty partner" >> /etc/apt/sources.list' 
sh -c 'echo "deb-src http://archive.canonical.com/ubuntu natty partner" >> /etc/apt/sources.list' 
apt-get update
echo "done"
sleep 5
echo "Installation von SUN JAVA Runetime Enviroment..."
echo "------------------------------------------------"
apt-get -y install sun-java6-jre sun-java6-plugin sun-java6-fonts
echo "done"
sleep 5
echo "Sun Java als Standard-JAVA festlegen"
echo "------------------------------------"
update-alternatives --config java
sleep 5
echo "Installation von Handbrake ..."
echo "------------------------------"
apt-get -y install handbrake
echo "done"
sleep 5
echo "Installation und Konfiguration von bumblebee (fuer Hybrid Graphics INTEL/nVidia) ..."
echo "-----------------------------------------------------------------------------------"
apt-get -y install bumblebee
echo "done"
sleep 5
echo "Installation von Thunderbird mit de-language-pack"
echo "-------------------------------------------------"
apt-get -y install thunderbird thunderbird-locale-de
echo "done"
sleep 5
echo "Installation von Skype (Colsed Source) ..."
echo "------------------------------------------"
apt-get -y install skype
echo "done"
sleep 5
echo "Installation von Pidgin ..."
echo "---------------------------"
apt-get -y install pidgin
echo "done"
fi 
exit 0

```The problem is that I get this message: 

(line where you can find "fi"): Syntax error: end of file unexpected (expecting "fi").

Where's the mistake?

---

### Post by apmcd47 on 2011-09-03
I'm not sure but I dont like the semicolon at the end of the if statement (after the square brackets). Try removing that and see what happens.

Failing that comment out all the lins in the else clause and uncomment them one by one. But I think it's something to do with the semicolon.

Andrew

---

### Post by Drenriza on 2011-09-03
> **apmcd47 said:**
> I'm not sure but I dont like the semicolon at the end of the if statement (after the square brackets). Try removing that and see what happens.

Failing that comment out all the lins in the else clause and uncomment them one by one. But I think it's something to do with the semicolon.

Andrew

By comparing the script to one of my own, i would also try to remove the semi-colon.

---

### Post by SeaKing on 2011-09-04
I removed the semicolon but nothing chnaged. If I replace all the code between else and fi by the simple line *echo "You are root!"* the if condition works fine.

---

### Post by TeoBigusGeekus on 2011-09-04
Try adding a semicolon after each command between else and fi.

---

### Post by SeaKing on 2011-09-04
No effect, same error report like without the semicolon after each command

---

### Post by zero2xiii on 2011-09-04
Try using a function. All those sleep calls might cause issues, or if one of the apt-get requests fails, the if will fail:

Change:
```
if [ "$(whoami)" != "root" ]; 
then 
    echo "Das Script muss mit root-Rechten ausgefuehrt werden!"
    echo "Nutze: 'sudo ./script.sh'"
    echo ""
else
echo "Installation der Ubuntu-Restricted-Extras ..."
apt-get -y install ubuntu-restricted-extras
echo "done"
sleep 5
echo "Installation des VLC-Players ..."
echo "--------------------------------"
apt-get -y install vlc vlc-data  
echo "done"
sleep 5
echo "Hinzufuegen der PPA: Paketquellen fuer SUN JAVA, Handbrake und bumblebee ..."
echo "---------------------------------------------------------------------------"
add-apt-repository ppa:ferramroberto/java 
add-apt-repository ppa:stebbins/handbrake-releases
add-apt-repository ppa:mj-casalogic/bumblebee
cp /etc/apt/sources.list /etc/apt/sources.list.bak 
sh -c 'echo "deb http://archive.canonical.com/ubuntu natty partner" >> /etc/apt/sources.list' 
sh -c 'echo "deb-src http://archive.canonical.com/ubuntu natty partner" >> /etc/apt/sources.list' 
apt-get update
echo "done"
sleep 5
echo "Installation von SUN JAVA Runetime Enviroment..."
echo "------------------------------------------------"
apt-get -y install sun-java6-jre sun-java6-plugin sun-java6-fonts
echo "done"
sleep 5
echo "Sun Java als Standard-JAVA festlegen"
echo "------------------------------------"
update-alternatives --config java
sleep 5
echo "Installation von Handbrake ..."
echo "------------------------------"
apt-get -y install handbrake
echo "done"
sleep 5
echo "Installation und Konfiguration von bumblebee (fuer Hybrid Graphics INTEL/nVidia) ..."
echo "-----------------------------------------------------------------------------------"
apt-get -y install bumblebee
echo "done"
sleep 5
echo "Installation von Thunderbird mit de-language-pack"
echo "-------------------------------------------------"
apt-get -y install thunderbird thunderbird-locale-de
echo "done"
sleep 5
echo "Installation von Skype (Colsed Source) ..."
echo "------------------------------------------"
apt-get -y install skype
echo "done"
sleep 5
echo "Installation von Pidgin ..."
echo "---------------------------"
apt-get -y install pidgin
echo "done"
fi 
exit 0
```

TO:
```

function install_procedure(){

echo "Installation der Ubuntu-Restricted-Extras ..."
apt-get -y install ubuntu-restricted-extras
echo "done"
sleep 5
echo "Installation des VLC-Players ..."
echo "--------------------------------"
apt-get -y install vlc vlc-data  
echo "done"
sleep 5
echo "Hinzufuegen der PPA: Paketquellen fuer SUN JAVA, Handbrake und bumblebee ..."
echo "---------------------------------------------------------------------------"
add-apt-repository ppa:ferramroberto/java 
add-apt-repository ppa:stebbins/handbrake-releases
add-apt-repository ppa:mj-casalogic/bumblebee
cp /etc/apt/sources.list /etc/apt/sources.list.bak 
sh -c 'echo "deb http://archive.canonical.com/ubuntu natty partner" >> /etc/apt/sources.list' 
sh -c 'echo "deb-src http://archive.canonical.com/ubuntu natty partner" >> /etc/apt/sources.list' 
apt-get update
echo "done"
sleep 5
echo "Installation von SUN JAVA Runetime Enviroment..."
echo "------------------------------------------------"
apt-get -y install sun-java6-jre sun-java6-plugin sun-java6-fonts
echo "done"
sleep 5
echo "Sun Java als Standard-JAVA festlegen"
echo "------------------------------------"
update-alternatives --config java
sleep 5
echo "Installation von Handbrake ..."
echo "------------------------------"
apt-get -y install handbrake
echo "done"
sleep 5
echo "Installation und Konfiguration von bumblebee (fuer Hybrid Graphics INTEL/nVidia) ..."
echo "-----------------------------------------------------------------------------------"
apt-get -y install bumblebee
echo "done"
sleep 5
echo "Installation von Thunderbird mit de-language-pack"
echo "-------------------------------------------------"
apt-get -y install thunderbird thunderbird-locale-de
echo "done"
sleep 5
echo "Installation von Skype (Colsed Source) ..."
echo "------------------------------------------"
apt-get -y install skype
echo "done"
sleep 5
echo "Installation von Pidgin ..."
echo "---------------------------"
apt-get -y install pidgin
echo "done"
}


if [ "$(whoami)" != "root" ] 
then 
    echo "Das Script muss mit root-Rechten ausgefuehrt werden!"
    echo "Nutze: 'sudo ./script.sh'"
    echo ""
else
install_procedure
fi 
exit 0
```


Oh yea, another thing. May be trivial, but its a rule: BASH FILES MUST HAVE ATLEAST A SINGLE EMPTY LINE FOLLOWING THE LAST LINE OF CODE. You have no idea how many times this screwed me over before I started using geany for coding scripts...

---

### Post by fdrake on 2011-09-04
try chancing```

fi

```

with

```

else ;
fi

```

also make sure the 1st line is #!/bin/bash not #! /bin/bash

edit: never mind i niticed you have already an "else" statement. 

bash -v (what version r u using?)
try to run the comman  in dash  (#!/bin/dash)

---

### Post by SeaKing on 2011-09-04
@ zero2xiii

install_routine_asus.sh: 1: Syntax error: "(" unexpected

@ fdrake
install_routine_asus.sh: 14 (else-line): Syntax error: ";" unexpected

---

### Post by zero2xiii on 2011-09-04
Please upload the file so we can view the EXACT line syntax and compare that to the results you are having.

The unexpected ( in line 1, is completely wrong. I guess you didn't read through what I wrote. That is NOT the complete file, only the part you need to change.

---

### Post by sisco311 on 2011-09-04
@OP There isn't any syntax error in the script you posted. Did you post the right portion of the script?

@apmcd47 & Drenrizathe,  the semicolon is not needed, but its not causing any errors.

@TeoBigusGeekus & fdrake, eh, nonsense.

@zero2xiii,

function name() {...} is not POSIX, the POSIX form name() {...} is preferred.

---

### Post by sisco311 on 2011-09-04
> **zero2xiii said:**
> 
Oh yea, another thing. May be trivial, but its a rule: BASH FILES MUST HAVE ATLEAST A SINGLE EMPTY LINE FOLLOWING THE LAST LINE OF CODE. You have no idea how many times this screwed me over before I started using geany for coding scripts...

You mean a newline at the end of the last line, right? ;)

> **zero2xiii said:**
> Please upload the file so we can view the EXACT line syntax and compare that to the results you are having.


+1

---

### Post by SeaKing on 2011-09-04
There's the file in the attachments.

---

### Post by sisco311 on 2011-09-04
The shebang must be: 
```
#!/bin/bash
```
(no space after)

Your file is in DOS format, see:
[http://mywiki.wooledge.org/BashFAQ/052](http://mywiki.wooledge.org/BashFAQ/052)

Otherwise it should work.

---

### Post by SeaKing on 2011-09-04
I used 
```

$ tr -d '\r' < install_routine_asus.sh > install_asus.sh

```with the result :
```

$ file install_asus.sh 
install_asus.sh: Bourne-Again shell script text executable

```but
```
$ sh install_asus.sh 


Willkommen bei der Installationsroutine fuer das Asus X5MSN
------------------------------------------------------------

install_asus.sh: 8: Syntax error: "(" unexpected

```

---

### Post by sisco311 on 2011-09-04
sh is not bash. It's a symlink to dash.

```
bash install_asus.sh
```
or make it executable:
```
chmod +x ./install_asus.sh
```
and run:
```
./install_asus.sh
```

Oh, and  don't use extensions for your scripts. Scripts define new commands that you can run, and commands are generally not given extensions. Also: bash scripts are *not* sh script (so don't use .sh) and the extension will only cause dependencies headaches if the script gets rewritten in another language.

Once again, the syntax **function name {...}** is not POSIX, use the POSIX form:
```
install_procedure (){
...
}
```

---

### Post by SeaKing on 2011-09-04
It works :D. Thanks!

---

### Post by sisco311 on 2011-09-04
No problem! Don't forget to mark this thread as [SOLVED].

---

### Post by zero2xiii on 2011-09-04
> @zero2xiii,

function name() {...} is not POSIX, the POSIX form name() {...} is preferred.


Hay, auhm oka. Hehe I was not aware of that. Have been using "Function name() {....}" in all my scripts with zero errors... But will look into the matter. Thanks for pointing it out though..

---

### Post by sisco311 on 2011-09-04
> **zero2xiii said:**
> Hay, auhm oka. Hehe I was not aware of that. Have been using "Function name() {....}" in all my scripts with zero errors... But will look into the matter. Thanks for pointing it out though..

If you want to learn how to write bash scripts, then start here [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)

---

### Post by TeoBigusGeekus on 2011-09-05
> **sisco311 said:**
> sh is not bash. It's a symlink to dash.

```
bash install_asus.sh
```
or make it executable:
```
chmod +x ./install_asus.sh
```
and run:
```
./install_asus.sh
```

Oh, and  don't use extensions for your scripts. Scripts define new commands that you can run, and commands are generally not given extensions. Also: bash scripts are *not* sh script (so don't use .sh) and the extension will only cause dependencies headaches if the script gets rewritten in another language.

Once again, the syntax **function name {...}** is not POSIX, use the POSIX form:
```
install_procedure (){
...
}
```

Pffffffffffftttt....[-(

Just kiddin'; you're the bash expert :lolflag:

---

