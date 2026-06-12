---
title: "Wireless connection script causes crippling disk usage"
date: 2010-03-08
forum: General Help
---

### Post by coverslide on 2010-03-08
Ok this is probably not the best way to do it, but here is my situation. I have a Kubuntu 9.10 install which i accidentally upgraded to 10.4, which has led to a host of problems, but that's not the focus of this thread. One issue in particular is a script I made before to keep the wireless connected. I use this instead of the network manager because I do lots of administration remotely, and I need something that will connect without requiring the machine to be logged in in case I did something like upgrade the kernel which requires a reboot. Basically, the script, which I will paste below, pings the gateway, and if it does not get a ping, it will run iwconfig, dhclient, and there have been some cases when ndiswrapper would need to be reloaded as well. The router is unsecured because I couldn't get wpa_supplicant working (still on my TODO list), but the AP is hidden i have mac address filtering on it, so it's better than nothing. Anyway, the script had been working fine up until I upgraded, but after that, every time I tried to run the script, I would see the hard disk led flashing nonstop, and if I tried several times, the whole computer would grind to a halt. I installed iotop, and it was confirmed that in each case, there was a line like this:

```

13809 be/4 root       12.58 M/s    0.00 B/s  ?unavailable?  bash /usr/local/sbin/check_network

```

in spite of the fact that the script had finished executing and I had already been dropped back to the shell, and it would last for for 30 seconds to a few minutes, enough of those and everything would get locked up. Yes, I know, this is probably not the best way to accomplish what I was trying to do, but I am a bit of a newb when it comes to linux and hardware, but regardless, I have a concern that my seemingly innocuous script is causing this. 

Anyways, here are my questions:

1) Is there a better alternative to achieve my goal here?

2) What the hell could be causing these massive disk reads? I didn't run this in the background, and even in the case of the ping test being successful and nothing is run except for ping, grep and cut, I still get the same thing.

Here it is in case you are wondering:

```

#! /bin/bash
# 
# Script location:
# /usr/local/sbin/check_network
#

function pingTest
{
  echo Ping Test
  OUT=`ping 192.168.0.1 -c 1 -w 2 | grep received | cut -d' ' -f4`
  if ! [ "$OUT" ] || [ "$OUT" -lt 1 ] ; then
    echo "NO PING"
    return 1
  else
    echo "PING SUCCESS"
    return 0
  fi
}

function wlanTest
{
  echo Reconfiguring Wireless
  WLAN=`sudo iwconfig wlan0 essid Hoffman 2>&1`
  WSTAT=$?
  if [ $WSTAT -ne 0 ] ; then
    echo "WLAN ERROR: $WLAN"
    return 1
  else
    echo "WLAN SUCCESS"
    return 0
  fi
}

function dhcpTest
{
  echo Reconfiguring DHCP
  DHCP=`sudo dhclient wlan0`
  DHSTAT=$?
  if [ $DHSTAT -ne 0 ] ; then
    echo "DHCP ERROR: $DHCP"
    return 1
  else
    echo -e "DHCP SUCCESS \n$DHCP"
    return 0
  fi
}

function modProbe
{
  echo "RECONNENCTING HARDWARE"
  sudo modprobe -r ndiswrapper
  sudo modprobe ndiswrapper
}

function errorMsg
{
  echo "Final Error. Call Richard"
  exit 1
}

function main
{
  pingTest
  if [ $? -ne 0 ] ; then
    wlanTest
    if [ $? -ne 0 ] ; then
      modProbe
      wlanTest
      if [ $? -ne 0 ] ; then
        errorMsg
        exit 1
      fi
    fi
    sleep 2
    pingTest
    if [ $? -ne 0 ] ; then
      dhcpTest
      if [ $? -ne 0 ] ; then
        errorMsg
        exit 1
      fi
    fi
  else
    echo "Ping Test Successful"
    exit 0
  fi

  sleep 2
  pingTest
  if [ $? -ne 0 ] ; then
    errorMsg
  else
    echo "Ping Test Successful"
    exit 0
  fi
}

main


```

---

### Post by cigarman75@aol.com on 2010-03-08
i hope some one out there can help i am an aol user and wanted to install ubuntu as a  dual system but i think i screwed up and am really frustrated becaus i seem to have lost the use of every thing on my computer including skype .picasa ,and all of my photo programs and my photos so what i would like to do is uninstall ubuntu and maybe start over but how do i uninstall ubuntu ? please i need help..........mavin

---

