---
title: "Unable to activate drivers and mount hard disk"
date: 2009-10-18
forum: General Help
---

### Post by jollins69 on 2009-10-18
Hi,
i posted a problem i had a while back and got some good responses back and i can say thanks for that.
i now have a unusual problem and want to refrain from a reinstall once again.

i have just recently reinstalled ubuntu 9.04 and all was going well. i fixed the sound once again and was in the process of installing my apps. 

While aquiring codecs for my dvd's i realised i need to activate my graphics driver.
i was unable to however with the message 
"You are not authorized to perform this action."
i checked if i had the privilages to do this and i do. one small thing though, if i didnt have them then the computer wouldnt let me have them as when i went to select yes it never saved.

i am also unable to mount the second partition on my hard disk. "has a duff windows installation on it".

i might add (not sure if its normal or not) that a large majority fo folder deny me permission and i have to chmod it before i can add/remove items.

anything i can use to furthur my knowlede of linux would be greatful....

i dont want to have to go back to windows :( stupid hp....

---

### Post by jollins69 on 2009-10-18
was able to fix the drive not mounting properly by typing

sudo mount /dev/sda1 /media/tempdisk -o force

now mounts and im able to surf the file structure of my old windows partition. so i can back up and kill ;)

still having problems with the driver though. :/

---

### Post by mike555 on 2009-10-18
so you can't just go to "System , Administration , Hardware Drivers " and activate your graphic driver??

---

### Post by jollins69 on 2009-10-18
yea im pretty sure i said i tried that. iv been looking around for a while now and its a little more complicated than that.

I tried installing it manually and now it doesn't work at all. seems its incompatable... tried deleteing the driver directory, auto repairing from recovery console and repairing the config file with the failsafe. no joy... 

sucks. nothing is going right for me.....

---

### Post by mike555 on 2009-10-18
You might try "envy" it should uninstall old drivers and install new ones for you........

 sorry , it's called " EnvyNG " now.....

---

### Post by jollins69 on 2009-10-19
ok i have an update. 

this is for anyone who has gone through this before.

i had a duff graphics driver installed on my computer and of course this meant that i couldnt log in.

i was forced to uninstall xorg from my system

sudo apt-get autoremove xorg

this half fixed the probelm as i was able to get into the login screen but unable to get to my desktop.

i reinstalled gnome by typing

sudo apt-get install gnome.

This restored my comp to its natural glory.

as for the graphics, i tried envyng and it failed again and i had to go through the same process once again. 
It seems like there is a permissions issue and the computer isnt able to access the driver properly therefore causing big problems.
its stable for the minute and im gonna back up and clean the hard disk. backup docs and start fresh. im gonna do it next week so if anyone has any sugestions before then id be very greatfull as a reinstall is last resort

hope this helps poeple in need

---

