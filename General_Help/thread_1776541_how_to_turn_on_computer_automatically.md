---
title: "how to turn on computer automatically"
date: 2011-06-06
forum: General Help
---

### Post by starbala2008 on 2011-06-06
Hi,
How to turn on system on particular time? I have to start download process at morning 2'o clock. I can use crontab to schedule my download but how to turn on system automatically?

---

### Post by FormatSeize on 2011-06-06
Go into your BIOS and set the automatic wake up option. I'm sure it's called something else, but the option is definely there. Lemme restart so that I can see what the option is actually called.
 
Mine is called "Auto Power On". The computer is some Dell variant. So you should see something like that. On further thought, though, are you set up to have the system automatically log you in, or do you have to manually log in? The power on feature, in and of itself, can't log you in (I don't think).

---

### Post by starbala2008 on 2011-06-06
In windows we have scheduler in the os itself. Can we make any program in the ubuntu itself to turn on?

---

### Post by starbala2008 on 2011-06-06
> **FormatSeize said:**
> Go into your BIOS and set the automatic wake up option. I'm sure it's called something else, but the option is definely there. Lemme restart so that I can see what the option is actually called.
 
Mine is called "Auto Power On". The computer is some Dell variant. So you should see something like that. On further thought, though, are you set up to have the system automatically log you in, or do you have to manually log in? The power on feature, in and of itself, can't log you in (I don't think).

Thanks for the effort you took to help me:). I am having "power" option in my bios.
And also thanks for remembering about to enable automatic logon.

Do you know any tool which can be used in ubuntu to switch "on" from "off" or "hibernate" mode?

---

### Post by DawieS on 2011-06-08
> **starbala2008 said:**
> Do you know any tool which can be used in Ubuntu to switch "on" from "off" or "hibernate" mode?
It is not possible for any operating system to power on by itself, since it is "dead" when shut down or hibernating. There is no running process that can watch the clock to start at a given time.

Most computers these days support the "Power-On by Alarm" function in the Bios. In my machine, it is found under the heading "Power Management Setup" of the Bios.

To enter the Bios on my machine, I have to press "Delete" during the Post process at boot-time. I can set my computer to power-on at a specific time on a specific day of the month, or "every day".

After your computer has powered on, it should boot directly into Ubuntu (without requiring password authentication). In Ubuntu, you can use the "at" command, in order to schedule the future jobs to start (and stop) at a given future time and date.

You could also make use of a batch file, where each line contains contains the "at" command, along with different future dates, and the application (with parameters) that you want to use.

For more information on the "at" command, type "man at" in a terminal.:grin:

---

### Post by enimeizoo on 2011-06-08
Here is a howto about it. I didn't try it, yet, I kept it in my bookmarks just in case.

[How to ... turn your linux box into an alarm clock by writing your own init script - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1714793")

---

