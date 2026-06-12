---
title: "Need help in creating bash script for controlling laptop fan speed."
date: 2011-01-18
forum: General Help
---

### Post by dartttt on 2011-01-18
I got a new Dell Inspiron 15R yesterday and installed Ubuntu 10.10. Everything works right out of the box except that the fan is always on even if the temp is as low as 30 Celsius.

I found a way to control fan speed through some commands and installing a package i8kutils. Now I want to create a bash script that uses Zenity so that it can be shared with other users having similar problems. Unfortunately I am not a programmer and I have no idea what to do. Any help will be appreciated.

The script will do the following things in order:

1. Check that the packages lm-sensors, sensors-applet  and i8kutils are installed or not. If not allow the user to install by running apt-get install command.

2. Telling the user to add the applet to the gnome panel so that user can control the fan speed as per the temperature. (will require a logout or panel kill so that user can find applet in list)

3. Once the above two steps are done we need to load i8k module in kernel running following command: sudo modprobe i8k force=1

4. Now if user wants, he can check various statuses. Command: i8kctl. This returns values in terminal like this: 1.0 (null) xxxxxx 50 -1 0 -1 0 -1 -1 in the following order:
      
        1. i8k format version
        2. bios version
        3. machine id
        4. cpu temperature
        5. left fan status
        6. right fan speed
        7. left fan status
        8. right fan speed
        9. ac power status
       10. fn buttons status

5. Now, user can change fan speed using following command: i8kctl fan R L (where R is right fan and L is left fan) with modes:

      0  turn the fan off
      1  set low speed
      2  set high speed
      -  don't change the state of this fan

6. Thats it. Some output like "Your fan speed has been set to 1 (low speed). To change the fan speed, run the script again"

i8kutils can also be run in a daemon mode that automatically controls speed of fan on predefined temperature thresholds. But I don't know how to do this. If anyone can create a script for this also, it will be helpful.

Links:
[http://askubuntu.com/questions/22049/how-to-control-fan-speed-in-dell-inspiron-5010-15r](http://askubuntu.com/questions/22049/how-to-control-fan-speed-in-dell-inspiron-5010-15r)
[http://linux.die.net/man/1/i8kctl](http://linux.die.net/man/1/i8kctl)

---

### Post by lykeion on 2011-01-18
> **dartttt said:**
> Now I want to create a bash script that uses Zenity so that it can be shared with other users having similar problems.

Actually you've just done that, although not as a script but with this post. You could even make a new thread "HOWTO: control laptop fan speed with i8kutils" and write this info in a step-by-step fashion. That way you'll share it with lot more users, because more people will follow a guide than download a script.

If you want to learn bash scripting & zenity this is some pages you could read:
[https://help.ubuntu.com/community/Beginners/BashScripting#Scripting](https://help.ubuntu.com/community/Beginners/BashScripting#Scripting)
[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

---

