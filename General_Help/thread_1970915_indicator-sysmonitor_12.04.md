---
title: "indicator-sysmonitor 12.04"
date: 2012-05-01
forum: General Help
---

### Post by marty331 on 2012-05-01
If you are like me you enjoy the indicator-sysmonitor display.  It has not been ported to 12.04 yet, however it still works as is!  I have it running on 12.04 64bit but it should work on 32bit also.



Open the link for the sysmon script from my git(I did not create this script nor do I take any credit, I am merely sharing it for others to enjoy):
[https://raw.github.com/marty331/ubuntupostinstall/master/sysmon](https://raw.github.com/marty331/ubuntupostinstall/master/sysmon)
Copy and past this into a text file and name it sysmon.  Open terminal and create a scrips folder and save this file there:
cd
mkdir scripts

Download the indicator from:
[https://launchpad.net/indicator-sysmonitor](https://launchpad.net/indicator-sysmonitor)
Install indicator-sysmonitor_0.3.9~oneiric0_all.deb with Software Center or gdebi


Install dstat:
sudo apt-get install dstat

Start indicator-sysmonitor, click on Preferences.  Click -Use this command and paste:  $HOME/scripts/sysmon
Click Run on Startup and Save.

Enjoy!

---

### Post by d4m1r on 2012-05-05
Thanks for this!! I got it working on 12.04 just like I had it on 11.10 :mrgreen:

However, I've manually editing the script you linked to and will post it below. I think my version is much more professional looking and clean. Also, make sure you grant read/write/execute permissions to "other" once you put the file in home/scripts or other wise sysmon will only display "(no output)".

```
#!/bin/bash

#settings:
netspeed=true
ram=true
cpu=true

#-------------------------------------------------------


#---------------- initialize ---------------------------
rm /tmp/.sysmon > /dev/null 2>&1
dstat --net --mem --cpu --output=/tmp/.sysmon 1 1 > /dev/null 2>&1

#----------- up/down speed -----------------------------
if [ $netspeed = true ]; then

upspeed=$(echo $(cat /tmp/.sysmon | tail -1 | cut -d ',' -f2)/1024 | bc)

upkbmb=$(if [ $upspeed -gt 1024 ]; then 
        up1=$(echo $(cat /tmp/.sysmon | tail -1 | cut -d ',' -f2)/1024/1024 | bc -l)
        echo $up1 | head -c 4
    else 
        echo $upspeed | head -c 3
    fi)

downspeed=$(echo $(cat /tmp/.sysmon | tail -1 | cut -d ',' -f1)/1024 | bc)

downkbmb=$(if [ $downspeed -gt 1024 ]; then 
        down1=$(echo $(cat /tmp/.sysmon | tail -1 | cut -d ',' -f1)/1024/1024 | bc -l)
        echo $down1 | head -c 4
    else 
        echo $downspeed | head -c 3
    fi)
#---------------- up/down speed unit --------------------
downunit=$(if [ $downspeed -gt 1024 ]; then echo "MB/s"; else echo "KB/s"; fi)
upunit=$(if [ $upspeed -gt 1024 ]; then echo "MB/s"; else echo "KB/s"; fi)

fi



#------------------- CPU % used -------------------------
if [ $cpu = true ]; then

cpufree=$(cat /tmp/.sysmon | tail -1 | cut -d ',' -f9)
cpuused=$(echo 100-$cpufree | bc | sed -e 's/\..*//')

fi



#------------------- RAM % used --------------------------
if [ $ram = true ]; then

memused=$(free -m | grep buffers/cache | tr -s ' ' | cut -d' ' -f 3)
memfree=$(free -m | grep buffers/cache | tr -s ' ' | cut -d' ' -f 4)
memtotal=$(echo $memused+$memfree | bc -l)

memusedpercent=$(echo 100-100*$memfree/$memtotal | bc)

fi


#------------------ The Indicator Sysmonitor actual output -
echo $(if [ $cpu = true ]; then echo CPU: $cpuused% \|; fi) $(if [ $ram = true ]; then echo RAM: $memusedpercent% \|; fi) $(if [ $netspeed = true ]; then echo &#8595; $downkbmb $downunit &#8593; $upkbmb $upunit; fi)
```

---

### Post by kushdilip on 2012-07-04
Very nice script. I want to use it as an alternative to netspeed panel applet existing in earlier versions of ubuntu, so I removed the ram and memory usage part and kept only netspeed part. 

But the refresh rate of download and upload speed displayed using this script is very slow, more than 2 sec. 
I not an expert in bash scripting so can anyone modify it to increase the refresh rate to show almost real time network activity.

Thanks in advance. :)

---

### Post by kushdilip on 2012-07-04
Anyways I got it worked little faster. I replaced the text 'self.update.interval' inside the function 'sleep' with value 0.1 in file /usr/bin/indicator-sysmonitor which is a python script.
use following command in terminal and replace as above.

sudo gedit /usr/bin/indicator-sysmonitor

save and close the file and start indicator-sysmonitor. Use the above custom bash script.

It's refreshing faster than earlier. :)

---

### Post by AllGamer on 2012-07-14
Thanks everyone for the updated script and tips :)

it might be nicer if you submit the changes to the source library on PPA 
after all that's what Linux is all about ;)

---

### Post by kushdilip on 2012-07-14
> **AllGamer said:**
> Thanks everyone for the updated script and tips :)

it might be nicer if you submit the changes to the source library on PPA 
after all that's what Linux is all about ;)
I actually informed about the changes made in the script on the PPA. I don't know much about how to submit changes to the source library. I'll try to learn it. 
Thanks for your valuable suggestion. :)

---

### Post by d4m1r on 2012-07-14
> **AllGamer said:**
> Thanks everyone for the updated script and tips :)

it might be nicer if you submit the changes to the source library on PPA 
after all that's what Linux is all about ;)


Your welcome :D Customizing an existing script is easy for me but that's about there it stops. I don't have any experience submitting code, updating PPAs, or the like :(

---

### Post by TheGrave on 2012-08-04
Didn't quite get what extra features this script introduces. Care to brief us?

By the way is sysmonitor reporting only the current user cpu/mem usages in your boxes? In mine it does which is quite annoying as I'm running a lot of processes with sudo and get false indication of what is going on.

---

### Post by d4m1r on 2012-08-05
> **TheGrave said:**
> Didn't quite get what extra features this script introduces. Care to brief us?

By the way is sysmonitor reporting only the current user cpu/mem usages in your boxes? In mine it does which is quite annoying as I'm running a lot of processes with sudo and get false indication of what is going on.


1) I think my version just looks much better visually.

2) Yes, it should be reporting TOTAL system resource usage, not just based on your user and mine is working correctly in that sense...

---

### Post by TheGrave on 2012-08-05
Gave it a try but throws a few errors and I don't get any visual output from the applet:

indicator-sysmonitor.conf: line 33: [: -gt: unary operator expected
indicator-sysmonitor.conf: line 35: [: -gt: unary operator expected
indicator-sysmonitor.conf: line 36: [: -gt: unary operator expected

What could be causing the non-visualization of total system resources? Running indicator-sysmonitor 0.4.1~unreleased on Ubuntu Precise with kernel 3.2.0-26.

---

