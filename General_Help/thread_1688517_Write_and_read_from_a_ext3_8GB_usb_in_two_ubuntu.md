---
title: "Write and read from a ext3 8GB usb in two ubuntu ?"
date: 2011-02-15
forum: General Help
---

### Post by whitewolf573 on 2011-02-15
I have a netbook with Ubuntu 10.10 installed in it,and a Pc with also ubuntu 10.10 in it , but x86_64.

I want to copy some iso files and data from my user home directory on the netbook , to the user home directory of the other pc , using a 8 GB usb formated in ext3 with gparted in my pc.

One iso is a windows 7 one to burn then with K3b , as i need to have windows installed in that box. Also of another iso that i have to burn too (windows 7 recovery disk) , and 3 anti-virus :( trials for windows.

As the usb is owned by the root (or more properly the mounting point,no?), and i can't use my user to copy data to it i usually do :

Usually , what i use is "sudo nautilus" then go to the place where is the data , copy it , and paste it then in the usb. Then in the other pc i do a chgrp and chown to the iso or file.

But , perhaps this is not the better approach. I have investigated a bit , and i think that i have found a better way , but i have some dudes.

The method is change the owner,group and permissions of the mounting point:

```

cd /media
ls
umount /dev/sdb1
sudo mkdir usb
sudo chown -Rv mulder usb
sudo chgrp -Rv mulder usb
sudo chmod -Rv 766 usb

```In the netbook the user is 'fox' so i would use 'fox' instead of 'mulder'.

Then when i insert the usb , the directory where is mount , is usb_ , i understand that i shouldn't umount the usb, and do the chown,chgrp and chmod in the actual mounting point of the usb.

Other dudes i have are:

If i do this steps in both computers, with each user,in the netbook i can copy the iso to the usb (as fox can write to the mount point of the usb ), but can the other user in the pc 'mulder' read the iso , so be copied to /home/mulder, and then be able to burn it in k3b with success ?

I suppose that having 766 , it should be able to read it , but would have the own of the file ?

How important is not to only be able to read it , but also own it ? 

I suppose if the user ID is the same , wouldn't be any problem ,as each ubuntu would supose that the file is owned by their user. 

Perhaps the user name change,but if the ID is the same , the user is the same for ubuntu , not any different, no ?

Thanks for the help :)

---

### Post by TeoBigusGeekus on 2011-02-15
Try this
```
sudo chmod 777 /media/mountpointofusb
```
Credits go to Coffeecat of course.

---

### Post by whitewolf573 on 2011-02-15
This is a possible option , i suppose , and as all can read write and execute all files , should not be any problem. But with 766 neither (although execute). But the owner , if is different , i could have problems ?

---

### Post by TeoBigusGeekus on 2011-02-15
I don't think so. 
Doing it on both pcs will make the usb r/w/e for every user regardless of ownership.

---

### Post by whitewolf573 on 2011-02-15
Ok , i will try what happens with the recovery iso that is 145 mb , and if k3b complains or something (i don't think so , if it can read the iso.)

Edit:

When i do ```
sudo chmod -R 777 
```, if i go to the properties of the directory (double click in the usb) , in permissions, the permisions of the directories are stabissed to create and erase files , but the permisions of the files (access to file) are just -- for owner,group and other.

If i create a file in the usb , is created with only read to group and other , and write / read to owner.No execute to anyone.

Isn't this a bit strange ?

AH, if i insert the usb in the netbook , the usb has still their permissions, the same like in the pc , but with fox instead of mulder. So when doing chmod -R 777 usb the permissions of the usb filesystem is what is changed, not the mounting point , i understand.

---

### Post by whitewolf573 on 2011-02-16
Resuming ...

So , to be able to get access with a non root user to the usb i have to go to where is mounted and do this:

```

sudo chown -Rv 'user' usb
sudo chgrp -RV 'user-group' usb
sudo chmod -Rv 777 usb.

```And i should be able to write the isos to the usb, and later read them.(copiying to the user's home).


Not worrying if in the permissions tab of properties the access to file section shows a -- , no ?

chmod should give permissions to all , files and directories.

If i do a 

Although when i create a file in the usb , i can but the permissions of other and group are only read , not write and read, and , no one can execute the file (well , was a file edited in gedit with no .sh or like , only plain text, so perhaps is ok , the thing ob being no executable. But shouldn't all be able to read and modify the file , and read / write in the directory ?

Edit:

i have created a directory in /media , and did 'chown -Rv mulder usb_' and 'chgrp -Rv mulder usb_'. Then i created two files , one plain txt , and one .sh.

both files are read and write for 'mulder' and only read for group and other. the .sh is no executable for any user.If i do then a chmod -Rv 766 usb , the files created are changed to read & write for the group and other, but the new files i create are still read only for both group and other. Why ?

---

