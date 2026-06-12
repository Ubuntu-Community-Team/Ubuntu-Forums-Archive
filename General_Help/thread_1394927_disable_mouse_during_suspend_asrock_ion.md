---
title: "disable mouse during suspend asrock ion"
date: 2010-01-31
forum: General Help
---

### Post by rileyp on 2010-01-31
Hi all
 I have a asrock 330 running mythbuntu karmic 2.31.6.14
I has a cheap usb remote that imitates mce keyboard presses and appears as a belkin usb keyboard in lsusb.
I have enabled usb0 during suspend.........sudo sh -c 'echo "USB0" > /proc/acpi/wakeup'
 and the remote is able to wake the pc.


[FONT=Verdana]However I would like to disable the mouse during suspend so that if it is knocked it will not wake the pc.
Is there a way to do this? 
Many thanks
Rileyp[/FONT]

---

### Post by nunovi on 2010-02-28
Similar problem here. Can anyone help?

---

### Post by rileyp on 2010-03-01
add this code to /etc/rc.local
```
    #set wake via remote
for i in 0 1 2 3 4 5
do
        enabled=`cat /proc/acpi/wakeup | grep "USB$i" | awk {'print $3}'`
        echo "$enabled"
        if [ "$enabled" = "disabled" ]
        then
                echo "USB$i" > /proc/acpi/wakeup
        fi
done
```and bumping your mouse wont boot your pc....

credit for code goes to Arkay of Australian Media Centre Community
[http://www.xpmediacentre.com.au/community/mythtv-combined-front-backend/41944-waking-remote-query.html](http://www.xpmediacentre.com.au/community/mythtv-combined-front-backend/41944-waking-remote-query.html)
cheers rileyp

---

