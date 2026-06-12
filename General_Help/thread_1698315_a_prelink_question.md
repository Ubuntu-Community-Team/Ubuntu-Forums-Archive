---
title: "a prelink question"
date: 2011-03-02
forum: General Help
---

### Post by held7over on 2011-03-02
Ubuntu 10.04 & 10.10  

My computers are 32 bit and I am looking to get more speed out of them. I installed prelink, modified it's file ( prelinking=yes ) and I then ran prelink from cron as follows: $ sudo /etc/cron.daily/prelink

After the prelinking finished, I rebooted, and ran "top" in a terminal, but so far,  I haven't seen prelink appear in the list of running processes. I have also tried finding it in:
ps -u <my user>
ps -u root

Do I need to put prelink in my startup manager? Wouldn't that cause it to re-index instead again rather than just being ready for me to launch applications? 

Thanks! :)

---

### Post by held7over on 2011-03-02
I am asking this question because the directions I found via google for setting up prelink, didn't show how updates were going to be handled and the way it was written, it kind of sounded like prelink would be automatically running with each boot.

However, I just found via google, someone giving instructions for automatically calling prelink after an update of the system, however I am wondering if there isn't an error in their command. Here is what they say:

This will allow prelink to be automatically executed directly after updating files so that it will prelink the newly updated files…Type the following in a terminal window…
gksudo gedit /etc/apt/apt.conf
Then add the following to the end, or if the file is empty…
DPkg::Post-Invoke {“echo Running Prelink, please wait…;/etc/cron.daily/prelink”;}

I do not know much about programmin in Linux, but looking at this, isn't echo going to simply print everything between the two " marks, and not execute /etc/cron.daily/prelink ???

Thanks! :)

---

