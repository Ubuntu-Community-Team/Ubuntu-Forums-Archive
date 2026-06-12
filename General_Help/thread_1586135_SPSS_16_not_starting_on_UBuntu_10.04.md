---
title: "SPSS 16 not starting on UBuntu 10.04"
date: 2010-10-01
forum: General Help
---

### Post by rhoparkour on 2010-10-01
Hello all!

I am trying to install spss 16 on an hp. I have activated the license and everything but when I run ./spss on the spss bin directory (this is the executable the install instrucyions tell me I should use) I get the following error after a little intro screen:

```

testu@Schwarzschild:~/SPSSIncb/SPSS16/bin$ sh ./spss
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x20656770, pid=2334, tid=2338302832
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_11-b03 mixed mode)
# Problematic frame:
# C  0x20656770
#
# An error report file with more information is saved as hs_err_pid2334.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted

```As you can see, I created an user to test the install (also this user has compiz completely disabled) and installed spss on his home directory. Any ideas on how to fix the problem?

---

### Post by dumi_peti on 2011-01-07
I have the same error message on Ubuntu 10.10. 
I'm so sad to see there's no solution. :(

---

### Post by dumi_peti on 2011-01-07
My installation process stops at 99% when said: "Finalizing vital ....". If I cancel the process with ctrl+c then I try to start SPSS I'm getting the same error message.

---

### Post by ebulga on 2011-02-02
> **dumi_peti said:**
> My installation process stops at 99% when said: "Finalizing vital ....". If I cancel the process with ctrl+c then I try to start SPSS I'm getting the same error message.

same error!

---

### Post by nighttrap on 2011-02-02
I am running SPSS 18 without any problem. Java packages (Open JDK) were already installed on my Ubuntu 10.10 Maverick Meerkat system. I did not specificaly installed them, maybe they came together with my other installation. 

SPSS installation method that I used

1) I used SPSS 18 with crack files which I downloaded from the net

2) First, I installed PlayOnLinux (POL) (a windows application emulator), You can install it with Ubuntu Software Center, or from terminal (that is the method I had chosen for the newest version. 

3) Installation with terminal 
a) wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -
b) sudo wget [http://deb.playonlinux.com/playonlinux_maverick.list](http://deb.playonlinux.com/playonlinux_maverick.list) -O /etc/apt/sources.list.d/playonlinux.list
c) sudo apt-get update
d) sudo apt-get install playonlinux
e) dont forget to install "mesa-utils" from synaptic manager before first run

4) You should be online when first running POL (PlayOnLinux)

5) At first run, it tries to update and install several fonts

6) After installing the fonts, you can quit "update frame)

7) Now go on installing SPSS
a) click "install" and select "new pol or something like that" option at the most below bottom left
b) Create new prefic
c) give name "spss"
d) then mostly say "no" aftercoming screens
(I barely remember these steps, you can find it on the net)

8) Then I copied crack files to both places
a) /home/YOURNAME/.PlayOnLinux/wineprefix/spss/dosdevices/c:/Program Files/SPSSInc/PASWStatistics18
b) /home/YOURNAME/.PlayOnLinux/wineprefix/spss/dosdevices/drive_c:/Program Files/SPSSInc/PASWStatistics18

(make the files seeable when searching "show secret folder" from Appearance menu. I dont know exact English phreases)

9) Start it with "Applications --> Wine --> Programs --> SPSSInc

Hope this helps

Please inform

Good Luck

---

### Post by nighttrap on 2011-02-02
The secod method is installing Windows (XP or 7) with Virtualbox (OSE or PUEL, I had chosen PUEL to utilize USBs) then install SPSS within the virtualized Windows. But, if so, install windows than ubuntu and go back to days with pain. Furthermore, I remembered that SPSS16 is not working on Windows 7

---

