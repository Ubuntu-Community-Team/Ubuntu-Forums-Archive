---
title: "PSP Mount and Permissions problems"
date: 2006-04-10
forum: General Help
---

### Post by disabled_20220313 on 2006-04-10
Hi all.

I am trying to get a friends PSP to mount on his computer.

The computer is set up so his dad is the main-sudo user, and the rest of the family are normal users.

Now when the PSP is plugged in it is not automatically mounted.

If I am in my friends login I can mount it by "su"-ing to his dads account, and then "sudo nautilus".  By going to "Computer" and double clicking Sony PSP it mounts to /media/usbdisk

Unfortunatly the device is then only readable by root. 

Any sugestions on how I can get users to be able to mount and view the devices properly?

Also have another problem with copying CD's. The audio CD will mount do the desktop but when "Copy CD..." is clicked the dialog box that opens just says "There is no avilable media". Any chance of some help with that too? 

Regards

---

### Post by thunderduck3141 on 2006-04-10
try using sudo <mount command>
this will give u temporary root privs, and the password u enter is your own
ask u sys admin to put u in the sudos folder if u r'nt
hope that helps

---

### Post by thunderduck3141 on 2006-04-10
and for the cds
make sure u mounted the correct drive, and try reinsterting the disk, ten try again
peace

---

### Post by disabled_20220313 on 2006-04-11
Hi,

Thanks for the suggestions. But adding the user to the sudoers file would comprimise the security and priviledges the father wanted. Is there a more targetted solution you can think of.

The CD is mounted, and visible on the desktop. I think it is something wrong with the burning application ubuntu is using.

---

### Post by thunderduck3141 on 2006-04-12
for the burning, try using k3b or graveman(i LOVE graveman)
as for the whole security thing u have two options
1. hack root (ooooh thats a bad thing to do..... shame on me)
2. ask the father to change the permissions on the /media folder
there is very little risk in this if you dont have to worry about people that can physically access the computer

hope that helps

---

