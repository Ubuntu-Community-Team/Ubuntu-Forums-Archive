---
title: "problems installing maya 2009 on ubuntu 64 bit"
date: 2010-01-02
forum: General Help
---

### Post by larrysito on 2010-01-02
hi guys i'm trying to install maya in my pc  AMD phenom 2 quad core 8 gigabites memory ram on ubuntu 64 bit i'm trying to follow this steps .
 in home i created a folder "called maya2009-linux" inside i have the 3 rpm files                                   AWCommon-11.5-19.i686.rpm AWCommon-server-11.5-19.i686.rpm Maya2009_0_64-2009.0-452.x86_64.rpm then i create a second folder in home called "larrysito" inside this folder i have the aw.dat i created on a windows partition 

  then in terminal i start typing this comands 


sudo apt-get install csh  " i made this step sucsessful"

sudo mkdir /var/flexlm    "i made this step successful"

                                 larry@larry-desktop:~$ sudo cp /home/larry/larrysito/aw.dat /var/flexlm   "i made this step succeful"


sudo chown 444 /var/flexlm/aw.dat     "i made this step successful"




NOW THE PROBLEMS BEGAN TRYING TO FOLLOW THE NEXT STEPS OF THIS LINK 
[http://combas3d.com/2009/05/setup-guide-maya-2009-sp1-linux-x64/](http://combas3d.com/2009/05/setup-guide-maya-2009-sp1-linux-x64/)

if [ ! -f  /usr/tmp ]; then sudo mkdir /usr/tmp; fi         mkdir: cannot create directory `/usr/tmp': File exists


 sudo chown 777 /usr/tmp    "i made this step successful i guess i didn't get any error without taking care of the other command "

sudo apt-get install rpm      "i made this command successful no error"

i dowload by my own  autodesk_maya_2009sp1a_linux64.tgz and as i said before i estract already creating in home 2 folders one for my aw.dat called "larrysito" and one for just 3 rpms files called "maya2009-linux"

BUT I THINK THE MOST BIGGEST PROBLEM IS THAT I CAN'T CONVERT OR INSTALL THE FREACKING RPMS FILES IN DEB I WROTTE THIS COMMAND 

                                 sudo rpm -ivh –nodep  AWCommon-11.5-19.i686.rpm AWCommon-server-11.5-19.i686.rpm Maya2009_0_64-2009.0-452.x86_64.rpm
 
AND IN ANSWER I'M GETTING THIS MESSAGE 
rpm: please use alien to install rpm packages on Debian, if you are really sure use --force-debian switch. See README.Debian for more details.


PLEASE SOMEBODY HELP ME I NEED TO INSTALL MAYA ON MY UBUNTU MACHINE I WILL BE SO GREATFUL  AND I'M SORRY FOR MY ENGLISH I'M KNOW IS LIKE WEIRD  BUT PLEASE HEL ME

---

### Post by CharlesA on 2010-01-02
What are you trying to do? Looks like you are trying to change permissions of the /var/tmp directory using chown. That won't work.

You should run this instead.

```
sudo apt-get install alien
sudo alien -i --scripts ~/maya2009-linux/Maya2009_0_64-2009.0-452.x86_64.rpm
```

---

### Post by larrysito on 2010-01-03
charles thank you for answer me but i did what you told me 


sudo apt-get install alien  i did it successful 





sudo alien -i --scripts ~/maya2009-linux/Maya2009_0_64-2009.0-452.x86_64.rpm    here i got this problem error: incorrect format: unknown tag

---

### Post by larrysito on 2010-01-03
please help me

---

### Post by larrysito on 2010-01-03
> **CharlesA said:**
> What are you trying to do? Looks like you are trying to change permissions of the /var/tmp directory using chown. That won't work.

You should run this instead.

```
sudo apt-get install alien
sudo alien -i --scripts ~/maya2009-linux/Maya2009_0_64-2009.0-452.x86_64.rpm
```
i just copy and paste on tirminal if i did wrong please tell me 

sudo alien -i --scripts ~/maya2009-linux/Maya2009_0_64-2009.0-452.x86_64.rpm

because the answer i'm getting is this 


error: incorrect format: unknown tag
    dpkg --no-force-overwrite -i maya2009-0-64_2009.0-453_amd64.deb
Selecting previously deselected package maya2009-0-64.
(Reading database ... 157085 files and directories currently installed.)
Unpacking maya2009-0-64 (from maya2009-0-64_2009.0-453_amd64.deb) ...
Setting up maya2009-0-64 (2009.0-453) ...

---

### Post by larrysito on 2010-01-03
sudo apt-get install alien

cd /home/larry/maya2009-linux

sudo alien -i --scripts ~/maya2009-linux/Maya2009_0_64-2009.0-452.x86_64.rpm
[SIZE=3]**and i got this after 5 minutes **[/SIZE]

error: incorrect format: unknown tag
    dpkg --no-force-overwrite -i maya2009-0-64_2009.0-453_amd64.deb
(Reading database ... 172340 files and directories currently installed.)
Preparing to replace maya2009-0-64 2009.0-453 (using maya2009-0-64_2009.0-453_amd64.deb) ...
/var/lib/dpkg/info/maya2009-0-64.prerm: line 10: test: upgrade: integer expression expected
Unpacking replacement maya2009-0-64 ...
Setting up maya2009-0-64 (2009.0-453) ...

[SIZE=3]**[COLOR=Red]now what's next please someone [/COLOR]**[/SIZE]

---

### Post by CharlesA on 2010-01-03
Should be installed.

---

### Post by larrysito on 2010-01-03
> **CharlesA said:**
> Should be installed.
oh my GOSH IS INSTALLED AND I BRING IT JUST B TYING "MAYA"IN TERMINAL but now could you tell why the software is working kind of weird i got this .

file -f -new;
// untitled // 
commandPort -securityWarning -name commandportDefault;
// Error: Image conversion (to IFF) failed // 
// Error: Image conversion (to IFF) failed // 
// Error: Image conversion (to IFF) failed // 
// Error: Image conversion (to IFF) failed // 
// Error: Image conversion (to IFF) failed // 
// Error: Image conversion (to IFF) failed // 
// Error: Image conversion (to IFF) failed // 
// Error: Image conversion (to IFF) failed // 
// Error: Image conversion (to IFF) failed // 
// Error: Image conversion (to IFF) failed // 
// Error: Image conversion (to IFF) failed // 
// Error: Image conversion (to IFF) failed // 
// mental ray for Maya 10.0 
// mental ray for Maya: using startup file /usr/autodesk/maya2009-x64/mentalray/maya.rayrc
// mental ray for Maya: setup
// mental ray for Maya: initialize
// mental ray for Maya: using 1 license
// mental ray for Maya: register extensions
// mental ray Node Factory: loaded
// mental ray for Maya: successfully registered
// mental ray for Maya: loading startup file: /usr/autodesk/maya2009-x64/mentalray/maya.rayrc
// parsing /usr/autodesk/maya2009-x64/mentalray/include/AdskShaderSDKWrappers.mi
// generating Maya nodes...
// parsing /usr/autodesk/maya2009-x64/mentalray/include/architectural.mi
// loading /usr/autodesk/maya2009-x64/mentalray/lib/architectural.so
// generating Maya nodes...
// parsing /usr/autodesk/maya2009-x64/mentalray/include/base.mi
// loading /usr/autodesk/maya2009-x64/mentalray/lib/base.so
// generating Maya nodes...
// parsing /usr/autodesk/maya2009-x64/mentalray/include/contour.mi
// loading /usr/autodesk/maya2009-x64/mentalray/lib/contour.so
// generating Maya nodes...
// parsing /usr/autodesk/maya2009-x64/mentalray/include/paint.mi
// loading /usr/autodesk/maya2009-x64/mentalray/lib/paint.so
// generating Maya nodes...
// parsing /usr/autodesk/maya2009-x64/mentalray/include/physics.mi
// loading /usr/autodesk/maya2009-x64/mentalray/lib/physics.so
// generating Maya nodes...
// parsing /usr/autodesk/maya2009-x64/mentalray/include/production.mi
// loading /usr/autodesk/maya2009-x64/mentalray/lib/production.so
// generating Maya nodes...
// parsing /usr/autodesk/maya2009-x64/mentalray/include/subsurface.mi
// loading /usr/autodesk/maya2009-x64/mentalray/lib/subsurface.so
// generating Maya nodes...
// parsing /usr/autodesk/maya2009-x64/mentalray/include/surfaceSampler.mi
// loading /usr/autodesk/maya2009-x64/mentalray/lib/surfaceSampler.so
// generating Maya nodes...
updateRendererUI;

---

### Post by larrysito on 2010-01-03
it looks pretty aweson and i can manipulate all the tools but with some kind of pain is not like very flexible or smoth the manipulaton of the software

---

### Post by larrysito on 2010-01-03
[SIZE=7]it works [SIZE=6]is so[/SIZE] freacking fast now i have maya on my ubuntu machine [/SIZE]:P [SIZE=7][COLOR=Red]thank you GOD now is time to work and make money  yesssss  [/COLOR][/SIZE]:)    [SIZE=6][COLOR=Blue]***i promise i will make a video tutorial about maya installation on ubuntu 64 bit***[/COLOR][/SIZE]

---

### Post by synapsys on 2010-01-18
ouch.... my eyes

---

### Post by larrysito on 2010-01-19
i already install maya on ubuntu 9.10 but i'm having this problem Fatal Error: Failed creating directory: /usr/tmp

 the maya is loading but the menus and the keys buttoms are not working the steps i made was 
[SIZE=7][B]
installing crack [/B][/SIZE]

                                 [COLOR=#000000][SIZE=2]**1.-     sudo mkdir /var/flexlm**[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]**2.-     cd /home/larry/obama**[/SIZE][/COLOR]
 

 [SIZE=2]**3.-     sudo cp aw.dat /var/flexlm/**[/SIZE]
 


                                 [SIZE=7]**Installing maya **[/SIZE] 
 [SIZE=2]**1.- sudo apt-get install csh**[/SIZE]
 [SIZE=2]**2.- sudo apt-get install alien**[/SIZE]
 [SIZE=2]**3.- sudo alien -i --scripts ~/maya2009-linux/Maya2009_0_64-2009.0-452.x86_64.rpm**[/SIZE]
 


[SIZE=6]**[COLOR=Blue]please help [/COLOR]**[/SIZE]

---

### Post by larrysito on 2010-01-19
[SIZE=5][B][COLOR=Red]I FOLLOW THIS STEPS[/COLOR]
[/B][/SIZE]                           

                                 [COLOR=#000000][SIZE=5]**INSTALLING CRACK**[/SIZE][/COLOR]
 

 

 [COLOR=#000000][SIZE=2]**1.-     sudo mkdir /var/flexlm**[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]**2.-     cd /home/larry/obama**[/SIZE][/COLOR]
 

 [SIZE=2]**3.-     sudo cp aw.dat /var/flexlm/**[/SIZE]
 

 

 

 

 [SIZE=7]**Installing maya **[/SIZE] 
 [SIZE=2]**1.- sudo apt-get install csh**[/SIZE]
 [SIZE=2]**2.- sudo apt-get install alien**[/SIZE]
 [SIZE=2]**3.- sudo alien -i --scripts ~/maya2009-linux/Maya2009_0_64-2009.0-452.x86_64.rpm**[/SIZE]
 

[SIZE=3][COLOR=Red]MAYA IS LOADING BUT THAN SO MANY KEYS  AND COMBINATIONS ARE NOT WORKING AND I HAVE THIS MESSAGE IN "TERMINAL" [/COLOR][/SIZE][SIZE=3]

Error: default temp directory /usr/tmp does not have write permissions.
*** Fatal Error: Failed creating directory: /usr/tmp
[/SIZE]

---

### Post by larrysito on 2010-01-19
[COLOR=#000000][SIZE=2]**[SIZE=5]INSTALLING CRACK [/SIZE]**[/SIZE][/COLOR] 
 

 

 [COLOR=#000000][SIZE=2]**1.-     sudo mkdir /var/flexlm**[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]**2.-     cd /home/larry/obama**[/SIZE][/COLOR]
 

 [SIZE=2]**3.-     sudo cp aw.dat /var/flexlm/**[/SIZE]
 

 

 

 

 [SIZE=7]**Installing maya **[/SIZE] 
 [SIZE=2]**1.- sudo apt-get install csh**[/SIZE]
 [SIZE=2]**2.- sudo apt-get install alien**[/SIZE]
 [SIZE=2]**3.- sudo alien -i --scripts ~/maya2009-linux/Maya2009_0_64-2009.0-452.x86_64.rpm**[/SIZE]


[SIZE=2]**[COLOR=Red]I CAN NOT USE TUMBLE TOOL OR ANY COMBINATION WITH [SIZE=3]"ALT"[/SIZE][/COLOR]**[/SIZE]


[SIZE=2][B]IN TERMINAL I HAVE THIS MESSAGE 
[/B][/SIZE]


larry@larry-desktop:~$ maya
Error: default temp directory /usr/tmp does not have write permissions.
*** Fatal Error: Failed creating directory: /usr/tmp


[COLOR=Blue]PLEASE SOMEONE HELP ME[/COLOR]  :(

---

### Post by bodhi.zazen on 2010-01-19
I merged your threads.

Please :

1. Do not start multiple threads on the same topic.

2. Please use the default font size and colors.

---

### Post by larrysito on 2010-01-19
do you know what is the problem in the installation ?

---

### Post by DarthScape on 2010-01-20
Gratz on the install, and thanks for the instructions all. But dude, calm down, he's an admin.

---

### Post by cariboo on 2010-01-20
It looks like you are using a pirated version of the program you are trying to install, we don't support illegal activities on the forums, This thread is closed.

---

