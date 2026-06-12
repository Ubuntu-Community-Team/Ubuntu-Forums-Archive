---
title: "Fatal Error - Cannot startx"
date: 2010-10-07
forum: General Help
---

### Post by UnterUn on 2010-10-07
Hey there! To cut a log story short i'd been using Ubuntu 10.4 for  nearly 3 months after installing it over Windows 7 from a USB, and it  worked fine untill one day. I tried to install the Intel Fortran  Compiler Trial and the PC crashed. So i did a hard reboot and tried to  log on, and it'd just take back to the log on screen. So i hit  Ctrl-Alt-F1 and dropped into the terminal and logged on, entered:
```
startx
```and got:
```
Fatal server error
Sever is already active for display 0
```Slightly intimmidated i decided to rienstall linux, all my inportant  files were in cloud storage so i wans't to bothered. So 1 hr later i had  the exacut same system i had before. 

Reboot, couldn't log on again. So i did some searching and couldn't  solve the problem so i reinstaled and this time decided not to install  the mandatory updates. It still did not work when logging on.  Rienstalled again, installed a different set of programs to what i  normally used, didn't update still did not work.

Here what i've done so far in my latest atempt (that i can remember):

```
:~$Startx

Fatal server error:
Server is already active for siplay 1
            If this server is no longer running, remove /temp/.X0-lock
            and start again
```Havving tried and failed using *startx -- :1  *before i skipped it and did exacully what it said:
```
:~$sudo rm /temp/.X0-lock
:~$startx

_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeA11COTSServerListeners: server already running

Fatal Server error:
Cannot establish any listening sockets - Make sure an X server isn't already running
```Then tried:
```
:~$sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```Reboted: Then repeated above with same results

Also on previous occations i have reconfigured other areas, of which a cannot remember (not that they worked.

Upon performing:
```
:~$startx -- :1
```I recive a blank, black screen with only the cursor (which can be moved).

Finnally i tried updating from terminal and repeating above. Still did not work

The stange thing is that everything works as long as i don't log off after install. 

So now i'm compleatly stummped, i have no idea what to do now-  my only current corse of action is to use the terminal untill 10.10 comes out and hope that works.

Thanks in advance for any help!



****
EDIT
****
Dropping into the terminal from the logon screen (ctrl-alt-f1) and inputing:
```

sudo apt-get install ubuntu-desktop

```

and then rebooting appears to solve the problem (although it is woefully slow now)

---

