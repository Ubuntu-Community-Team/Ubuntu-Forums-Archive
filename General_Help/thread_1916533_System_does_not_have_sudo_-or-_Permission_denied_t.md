---
title: "System does not have sudo -or- Permission denied to root"
date: 2012-01-28
forum: General Help
---

### Post by manish671 on 2012-01-28
[SIZE=2]I am new to Ubuntu/Linux. I am trying to install Mobile Partner in Ubuntu11.10. Problem is that after installation it runs with root user only.

Following are my observations starting with installation-

1. In terminal after "sudo -i" it will not ask for password and switch over to root
2. Permission denied message if try to install with ./install. Following is copy of terminal command and response.
[I]root@m-System-Product-Name:/home/m/a# ./install
-bash: ./install: [COLOR=Red]Permission denied[/COLOR][/I]
  
3 It will install with "bash install" but will give message that "There is no sudo command in your system" following is copy of command and response in terminal

[I]root@m-System-Product-Name:/home/m/a# bash install
Local path is: /usr/local/Internet_mobile

Installing Internet mobile...usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U user name] [-u user name|#uid] [-g
            groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user name|#uid] [-g groupname|#gid]
            [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user name|#uid] file ...
[COLOR=Red]There is no sudo command in your system,you'd better run the software by root[/COLOR]
Press any key to continue...
[/I]
After pressing the key it will go on Installing but will run with root only. I have tried with "Open As" also but no luck.

Please help.
Regards
[/SIZE]

---

### Post by raja.genupula on 2012-01-28
chmod +x install
./install

do those two things from the terminal . 

let us know what you got .
If you have read me file in it please read that .

All the best:D

---

### Post by manish671 on 2012-01-28
> **raja.genupula said:**
> chmod +x install
./install

do those two things from the terminal . 

let us know what you got .
If you have read me file in it please read that .

All the best:D

Thanks. now I can install using "./install" . but still I need to start it as root. Administrator account is not enough.  The Read me file has nothing special. Thanks again,  hope to find the solution.

---

### Post by raja.genupula on 2012-01-28
why ? while you try to start that app from terminal is it saying you need to be root ?

---

### Post by manish671 on 2012-01-28
[SIZE=2]Thanks for help.
If I am logged in as administrator and I try to run mobile partner from GUI then message will come in terminal that U should run it as root user.

and if I run from terminal, it will give lot of messages and then at last will give "Segmentation fault" then stops

However if I login as root or run from terminal as root then no problems.

As I have written before that even if I try to install the mobile Partner as ROOT (either logged in or from terminal using "sudo -i" or "sudo bash") it will give message that [/SIZE][SIZE=2][I][COLOR=Red]There is no sudo command in your system,you'd better run the software by root.

[COLOR=Black]one thing baffles me that if do sudo it does not ask for password and changes to root straightaway.

Thanks again[/COLOR]
[/COLOR][/I][/SIZE]

---

### Post by raja.genupula on 2012-01-28
ok if you add your user to root group , i mean giving all permissions to your username . I hope it will wok .

---

### Post by manish671 on 2012-01-29
[SIZE=2]I do not want to connect to net as root.[/SIZE][SIZE=2][/SIZE]

Thanks n regards

---

### Post by varunendra on 2012-01-29
> **manish671 said:**
> [SIZE=2]
1. In terminal after "sudo -i" it **will not ask for password** and switch over to root
[/SIZE]
That happens either in a live session, or when you have provided the password just a few minutes ago. As for the rest of the problems, I think becoming 'root' may be the cause, because after sudo -i, you get into root's home and use root's configuration files (to which, a normal user obviously doesn't have access). [COLOR=Red]**EDIT:** Any new files created in this mode will  also be owned by root, and normal users may not have access to it (while  the application may need write permissions to some of the files). [/COLOR]But I can't be sure if that is indeed the cause. [COLOR=Red]
[/COLOR] 
So far, I have installed Mobil-Partner (with sudo <whatever the command was>) on two machines (included in Idea Netconnect), and although it gave me some errors both of the times, it just worked as expected.

In the first installation (on 10.04.3), it didn't create any icon in the menus or on the desktop. But it automatically started on each startup, or whenever I plugged in the modem. I also manually created a launcher on the desktop - which successfully launched the GUI without requiring any password.

However one thing was a bit strange (still is on that system) which I couldn't get time to dig more. That was - after finishing the installation, when I thought the installation failed, I manually entered the configuration data in Network Manager which, until the following restart, detected the modem as a "Mobile Broadband modem". It worked and I even did some browsing as a test. But after a restart, the GUI started launching by itself (even if the modem wasn't plugged in) and the NM stopped detecting it. Wasn't a problem though, since the GUI did what NM was expected to do, as if it just "took-over" the command ;)

In the second installation (on 11.10 - with Unity/Gnome-fallback/CairoDock environments), just about a week ago (again Idea Netconnect), it not only created an icon in the menu (in gnome-fallback and cairo-Dock DEs, didn't try in Unity), but the modem also worked with both NM and Mobil-partner. In fact, the GUI was offering only WCDMA network, while NM was able to detect and offer HSDPA network on the same 3G modem/SIM.

So based on these experiences, I would suggest to uninstall it (while being root of-course) and reinstall with sudo only. IIRC, the readme file also contains the instructions to uninstall it.

---

### Post by manish671 on 2012-01-29
[SIZE=2]Initially I tried to install without root and simply prepending  sudo but I got this error message that no sudo command in system. So I tried with root user but same result .[/SIZE]
 

 [SIZE=2]As for other things I too have same experience with earlier versions with mobile partner but latter with 28.003.28.00.711 version it is much better. It gives option to select the network and message is allowed. Now sometimes Network Manager will show the Stick as modem but most of the time not. This MP can be downloaded from [http://support.videotron.com/_media/....28.00.711.exe](http://support.videotron.com/_media/....28.00.711.exe).  This file includes Mobile Partner for all Linux-Windows-MAC. Remember that if U run this exe file from Windows it will replace the dashboard of modem.[/SIZE]
 

 [SIZE=2]In following thread also I observed that it has the problem of Sudo in System[/SIZE]
  [SIZE=2][http://ubuntuforums.org/showthread.php?t=1916716&highlight=sudo+system](http://ubuntuforums.org/showthread.php?t=1916716&highlight=sudo+system)[/SIZE]
 

 [SIZE=2]I hope someone will come up with some solution.[/SIZE]
 

 [SIZE=2]Thanks.[/SIZE]

---

### Post by varunendra on 2012-01-29
I guess I'll try that in a 11.10 VM (although I don't have any Mobile modem available right now). Will post back with results.

And by the way, please correct the link (looks like you just copy-pasted the text of the trimmed-down link from the other thread).


**_EDIT_:**
The download link is too dodgy for me. Failed 6 times till now (on 20, 20+ MB). Completed the sixth time, but still turned out to be broken (CRC failed). Now am making the last attempt. How large is the file by the way? And what's wrong with the one that comes with the modem itself?

**_EDIT2_:** Failed for the 7th time (@ 37+ MB). Ok, once more..

**_EDIT3_:** Hmm.. completed at 42.5MB, and still CRC failed on 7-zip and "not a valid win32 app..." error on XP VM.
Sorry mate, i'm done with it!

---

### Post by jerrrys on 2012-01-29
Sudo mode set right?

[ATTACH]211636[/ATTACH]

---

### Post by manish671 on 2012-01-29
File size is around 57MB for the link I have given above.

---

### Post by manish671 on 2012-01-29
File size is around 57MB for the link I have given above.

I checked the installation file and found following lines which may be responsible for this

 if [ -z $(/usr/bin/sudo) ]
    then
      echo "There is no sudo command in your system,you'd better run the software by root"
      echo "Press any key to continue..."
      read -n 1

after this I checked in folder /usr/bin and found that sudo, sudoedit and sudoreplay files are there.

I do not know anything aout programming.

waiting for response, Thanks.

---

### Post by manish671 on 2012-01-29
> **jerrrys said:**
> Sudo mode set right?

[ATTACH]211636[/ATTACH]

Yes it is like that.
Thanks

---

### Post by manish671 on 2012-01-30
[SIZE=2]Congratulations friends. Finally with God's grace I could find the solution.
Do as followings
open "install" file in text editor and make some changes in line no 418 

Original line
if [ -z $(/usr/bin/sudo) ]
[/SIZE][SIZE=2]  [/SIZE][SIZE=2]
Change it to
  if [ -z /usr/bin/sudo ]

save the file then reinstall no need to uninstall

Thanks everybody
[/SIZE]

---

### Post by manish671 on 2012-02-05
[SIZE=2]I have noticed that after installing mobilepartner, sudo command does not ask for password. this is because mobilepartner modifies sudoers file with   ALL ALL=(ALL) NOPASSWD:ALL . I just put # in front of this line using sudo visudo then ctrl-x then Y then enter.  After doing this we can start the mobilepartner only using sudo in terminal.  One more disadvantage Ubuntu software center does not recognise this connection.

[/SIZE][FONT=Arial][SIZE=2]After new Ubuntu installation Ubuntu  automatically recognized my UMG1831 3g-USB modem but then in 2-3 hours it went off and  no luck. So I started using mobilepartner. However finally I could connect again using Network Manager[/SIZE][/FONT][SIZE=2]. F[/SIZE][SIZE=2]ollowing [/SIZE][FONT=Arial][SIZE=2]worked for me in just 2 steps

1 change in file [/SIZE][/FONT][FONT=Arial][SIZE=2]**  /etc/usb_modeswitch.conf**[/SIZE][/FONT][SIZE=2] [/SIZE][FONT=Arial][SIZE=2]
[/SIZE][/FONT] [FONT=Arial][SIZE=2]EnableLogging=1 # earlier it was 0[/SIZE][/FONT][SIZE=2]
[/SIZE]  [FONT=Arial][SIZE=2]# Huawei UMG1831 [/SIZE][/FONT][SIZE=2] 
[/SIZE]  [FONT=Arial][SIZE=2]DefaultVendor=  0x12d1 [/SIZE][/FONT][SIZE=2] 
[/SIZE]  [FONT=Arial][SIZE=2]DefaultProduct= 0x1446 [/SIZE][/FONT][SIZE=2] 
[/SIZE]  [FONT=Arial][SIZE=2]TargetVendor=   0x12d1 [/SIZE][/FONT][SIZE=2] 
[/SIZE]  [FONT=Arial][SIZE=2]TargetProduct=  0x1404 [/SIZE][/FONT][SIZE=2] 
[/SIZE]  [FONT=Arial][SIZE=2]MessageContent="5553424312345678000000000000001106  0000000000000000000000000000"

[/SIZE][/FONT][FONT=Arial][SIZE=2]2 [/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=#000000]**sudo usb_modeswitch -c /etc/usb_modeswitch.conf**[/COLOR][/SIZE][/FONT][SIZE=2]
[/SIZE]  [FONT=Arial][SIZE=2]it said many things then bye. Immediately Network manager recognized the modem.[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][SIZE=2]
[/SIZE] [FONT=Arial][SIZE=2]One can find target product and messageContenet from here[/SIZE][/FONT][SIZE=2]
[/SIZE] [FONT=Arial][SIZE=2]a) [http://www.dd-wrt.com/wiki/index.php/3G_/_3.5G](http://www.dd-wrt.com/wiki/index.php/3G_/_3.5G) and[/SIZE][/FONT][SIZE=2]
[/SIZE] [FONT=Arial][SIZE=2]b) [/SIZE][/FONT][SIZE=2]www.**sakis3g**.org/  [/SIZE][FONT=Arial][SIZE=2]download  sakis3g then untar and look in folder  sais3g/dependencies/usb-modeswitch-data/usbmodeswitch.d/   I tried to  work with sakis but during installation it gave message that  dependencies could not be met. [/SIZE][/FONT][SIZE=2]
[/SIZE]
[SIZE=2]
more technical details and discussions u can find here
[/SIZE][SIZE=2]http://ubuntuforums.org/showthread.php?t=1786440&highlight=huawei%2C+modeswitch&page=2

Thanks Everybody.
[/SIZE]

---

