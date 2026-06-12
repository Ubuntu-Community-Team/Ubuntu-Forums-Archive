---
title: "Increasing the value of HorizHysteresis and VertHysteresis"
date: 2012-05-02
forum: General Help
---

### Post by DaveDeviant on 2012-05-02
Experienced some problems with my touchpad on an HP G62 as you see here [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/992330](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/992330). 
Last reply is from a guy who's working at the new "“xserver-xorg-input-synaptics" package. He told me > Chow Loong Jin (hyperair) wrote 11 hours ago:
Try increasing the value of HorizHysteresis and VertHysteresis using synclient.

Now, how to edit those values using synclient?

Thanks,
Dave


[B][I][COLOR="Red"]EDIT: found - [http://linux.die.net/man/1/synclient](http://linux.die.net/man/1/synclient)
commands are: synclient HorizHysteresis=VALUE ; synclient VertHysteresis=VALUE[/COLOR][/I][/B]

---

### Post by DaveDeviant on 2012-05-02
For all the guys who got this issue follow this commands:

1. Open terminal and run this command
synclient HorizHysteresis=72 (you can add whatever value you want to test the behavior of your touchpad, for me 72 is fine)
synclient VertHysteresis=72 (you can add whatever value you want to test the behavior of your touchpad, for me 72 is fine)

2. Create a file by typing this into terminal:
gksudo gedit /etc/X11/xorg.conf
(this will create a xorg.conf file in etc/X11)

3. Edit the file by adding:
Section "InputClass"
    Identifier "touchpad catchall"
    Driver "synaptics"
    MatchIsTouchpad "on"
    Option "HorizHysteresis" "72"
    Option "VertHysteresis" "72"
EndSection

4. Save the file, restart Ubuntu and DONE.

Till they dont update the &#8220;xserver-xorg-input-synaptics&#8221; package I found this the only good method to get rid of this annoying issue.

---

