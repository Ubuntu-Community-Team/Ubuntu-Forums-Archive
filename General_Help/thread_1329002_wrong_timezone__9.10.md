---
title: "wrong timezone  9.10"
date: 2009-11-17
forum: General Help
---

### Post by sharkforce on 2009-11-17
hokay, so i just installed ubuntu 9.10 i had 9.04 previously (unrelated).  the timezone appears to be set to eastern us  i dont know how that happened but anyways  i am in PST time and need to change this :3.   i tried searching through the forums but haven't found anything that helped.

edit: oh and is there something i can download to make the wifi toggle button work for my laptop ?  its a compaq **cq60-215dx**

---

### Post by DeMus on 2009-11-17
> **sharkforce said:**
> hokay, so i just installed ubuntu 9.10 i had 9.04 previously (unrelated).  the timezone appears to be set to eastern us  i dont know how that happened but anyways  i am in PST time and need to change this :3.   i tried searching through the forums but haven't found anything that helped.

edit: oh and is there something i can download to make the wifi toggle button work for my laptop ?  its a compaq **cq60-215dx**

Reboot your PC and enter the BIOS by probably usinf either the DEl or F10 key on your keyboard.
Make sure the time is set correct there.
Then save the changes and exit the BIOS, boot into Ubuntu.
In menu System -> Administration you find Time and Date. When the time is not set right, unlock the window, use your password when asked and correct the time.

---

### Post by sharkforce on 2009-11-17
when i set the time the touch pad stops working, and i need to alt tab to get it to respond again, weird.. and when i restart the time setting doesnt save after manually setting it to 10 pm (the current time),  it goes back to 1 am the next day ~3 hrs ahead.
edit: and i did fix the time in the bios.   it seems to really like eastern US time zone... help?

---

### Post by lotuseclat79 on 2009-11-17
Hi sharkforce,

Here's the skinny on why you have have EST asserting.  What follows is part of a script I run to assert Eastern time when I boot up via the Live CD: 
# setup local timezone
rm /etc/localtime
# setup for EDT and EST (+4 EDT; +5 EST)
ln -s /usr/share/zoneinfo/EST5EDT /etc/localtime
# setup for only EST (+5 EST)
#ln -s /usr/share/zoneinfo/EST /etc/localtime
rm /etc/timezone
echo "US/Eastern" > /etc/timezone
export TZ="/usr/share/zoneinfo/America/New_York"

Your setup, given you are using PST now and will want it to automatically correct when PDT occurs is: Note: issue the command $ sudo -i to correct your installation as root:
# setup local timezone
rm /etc/localtime
# setup for PDT and PST (+7 EDT; +8 EST)
ln -s /usr/share/zoneinfo/PST8PDT /etc/localtime
# setup for only PST (+5 EST)
#ln -s /usr/share/zoneinfo/PST /etc/localtime
rm /etc/timezone
echo "US/Western" > /etc/timezone
export TZ="/usr/share/zoneinfo/America/Los_Angeles"
exit (to exit the root account)

That should correct your situation (given you have Karmic installed).

-- Tom

---

### Post by scouser73 on 2009-11-17
Try [[COLOR="Red"]**Ubuntu Time Management**[/COLOR]]("https://help.ubuntu.com/community/UbuntuTime")

---

### Post by MikeyDL on 2010-03-15
> **DeMus said:**
> Reboot your PC and enter the BIOS by probably usinf either the DEl or F10 key on your keyboard.
Make sure the time is set correct there.
Then save the changes and exit the BIOS, boot into Ubuntu.
In menu System -> Administration you find Time and Date. When the time is not set right, unlock the window, use your password when asked and correct the time.

Thanks on this info!  Finally got my time corrected.  

The Ubuntu time management link is outdated the ability to set your system time has been taken out of the right click menu.  Looks like you have to go into the Administration windows now.

---

