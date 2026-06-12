---
title: "Weird problem with AC power"
date: 2009-07-18
forum: General Help
---

### Post by Pro$pect on 2009-07-18
If my laptop is plugged in, I can boot up and shut down with no problems, but when I'm running on battery power it gets stuck at both. I have to keep hitting the keyboard to force everything to load through and then it will finally get me to my login screen or power down. I'm running the latest 64bit version of Ubuntu on a HP dv6000...Any ideas?

---

### Post by Blakefreak on 2009-07-18
I have the exact same problem on a dv9925.

---

### Post by zeronothing on 2009-07-18
It might have something to do with laptop-mode. when you laptop runs on battery their is a script to adjust hard drive speed, monitor, and other hardware devices so you can save on batter life. I know their is a configuration file in "/etc/laptop-mode/" where you can edit different settings. you might want to try and look in that direction.

---

### Post by Pro$pect on 2009-07-18
Could this be the .conf file i'm looking for? 
It's under laptop-mode/conf.d/start-stop-programs.conf





#
# Configuration file for Laptop Mode Tools module start-stop-programs.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#

###############################################################################
# Start/Stop Programs settings
# ----------------------------
#
# Laptop mode tools can automatically start and stop programs when entering
# various power modes. Put scripts accepting "start" and "stop" parameters
# in the directories
#    /etc/laptop-mode/batt-stop
#    /etc/laptop-mode/batt-start
#    /etc/laptop-mode/lm-ac-stop
#    /etc/laptop-mode/lm-ac-start
#    /etc/laptop-mode/nolm-ac-stop
#    /etc/laptop-mode/nolm-ac-start
# Laptop mode will call the scripts in a state-"stop" directory with the "stop"
# parameter when entering the state in question, and it will call the same
# scripts with the "start" parameter when leaving the state. Scripts in a
# state-"start" directory are called with the "start" parameter when the
# specified state is entered, and with the "stop" parameter when the specified
# state is left.
#
# Alternatively, if you only want to start/stop services, you can place the
# names of these services in one of the ..._STOP and ..._START config values
# below.
#
#
# IMPORTANT: In versions 1.36 and earlier, these settings were included in the
# main laptop-mode.conf configuration file. If they are still present, they
# overrule the settings in this file. To fix this, simply delete the settings
# from the main config file.
#
###############################################################################


#
# Should laptop mode start and stop programs? 
#
CONTROL_START_STOP=1


#
# Services to start/stop depending on the power state.
#
#
# These services are started/stopped through their init scripts, together with
# the files from the directories mentioned above. Specify the services as a
# space separated list.
#
BATT_STOP=""
BATT_START=""
LM_AC_STOP=""
LM_AC_START=""
NOLM_AC_STOP=""
NOLM_AC_START=""

---

### Post by zeronothing on 2009-07-19
The configuration file for laptop-mode is:

/etc/laptop-mode/laptop-mode.conf


the file laptop-mode.conf is going to have all of the main settings for laptop mode in ubuntu.

---

### Post by Pro$pect on 2009-07-19
I went to that first and edited this line:

#
# Enable laptop mode when on battery power.
#
ENABLE_LAPTOP_MODE_ON_BATTERY=1

I changed it from 1 to 0 restarted and still had the same problem. Nothing else in the config file looks like it can help.

---

