---
title: "Ubuntu handling USBs"
date: 2010-09-12
forum: General Help
---

### Post by ken poy on 2010-09-12
hi,  i am running Ubuntu 9.10 and am confused about USB devices.  i have 3 sandisk sticks.  i install 2 of them and they are auto detected as USB.  the 3rd is not recognized.
now i have been following   [http://www.linuxquestions.org/questi...-drive-221505/]("http://www.linuxquestions.org/questions/linux-hardware-18/howto-mount-usb-pen-drive-221505/")
and can mount the USB as a CD-ROM.  it suggests changing FSTAB to add a USB entry.
i tried this FSTAB is read only so did the CHMOD u=rwx /etc/fstab and fstab remained read only.  so how do i change fstab??  i cannot rename and save another copy. how do the 2 auto detected sticks get mounted??  they show as a USB on the desktop.  i sure am confused so any help would be appreciated.    thanks ken

---

### Post by s.fox on 2010-09-12
Hello,

I would manually Mount it as USB.  Information on how to do so can be found [here]("https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting").  If you have any problems please post back :)

-Silver Fox

---

### Post by ken poy on 2010-09-14
Hello,  i tried the above suggestion and it worked.  amazing what happens when you know what you are doing.    many thanks   ken

---

