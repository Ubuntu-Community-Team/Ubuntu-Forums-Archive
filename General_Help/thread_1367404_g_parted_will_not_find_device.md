---
title: "g parted will not find device"
date: 2009-12-29
forum: General Help
---

### Post by spiky001 on 2009-12-29
Hi i have just had a hard drive go down, So i put a spare drive in which is found in bios ok, on the load screen it,s there, windows sort of loads up but when i but unbuntu discs in g parted wont find disc any ideas. I have loaded just from cd not changing hard drive go to g partd in preferences still no device found, i have tried 3 different cd all the same

---

### Post by HappyFeet on 2009-12-29
Not sure this is a solution, but are you doing
```
sudo su
```
then
```
gparted
```?

---

### Post by MooPi on 2009-12-29
Your disk may be spent and not spinning at all. Which will be bad as data could be lost if not for expensive data recovery service. There is a drop down menu on the right where disks are listed, have you tried this?

---

### Post by spiky001 on 2009-12-29
no but it dont even find a device let alone let me change which might need root plus i,m only running from cd nothing installed yet

---

### Post by spiky001 on 2009-12-29
sorry any help plz

---

### Post by audiomick on 2009-12-29
What are you trying to do with the drive? Install onto it, or make a data partition on it?

---

### Post by spiky001 on 2009-12-29
fresh install not worried what is on drive i swap drive with a spare gparted not recognise it. So booted straight from hd win loaded but still cant get any buntu to load??? dont make sense

---

### Post by audiomick on 2009-12-29
Ok, you're not the first person to have this problem...:)

was the drive ever part of a raid array? If it was, or if your are not sure, boot to the live cd, 
open a terminal and do```

sudo apt-get remove dmraid
```and then start the installation.

If this still doesn't help, get the alternate CD and try installing with that. It has a different partitioning tool, and works better for some people, amongst others me last week...:)

The alternate CD is a text based installer, and looks frightening when you first see it. Don't panic, it isn't hard. Just follow the steps.

---

### Post by spiky001 on 2009-12-29
i have tried 9.04 / 9 10 / kubuntu 9 10 but will try the raid option 1st where do i get alterative cd from?

---

### Post by audiomick on 2009-12-29
If you go to the Ubuntu Download site and select "alternative download options" and then "text installer" and so on you end up here:
[http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors](http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors)

Look for a mirror on this list that is near to you. Go there and click your way through till you find the one you need.

It will be called
"ubuntu-9.10-alternate-amd64.iso " for a 64 bit system, or
"ubuntu-9.10-alternate-i386.iso" for a 32 bit system.      

If you start the download and it says it's going to take hours, bail out and try a different GB mirror. I got an image the other week. The mirror that was geographically closest would have taken two hours, a different one took about 15 minutes.

---

### Post by spiky001 on 2009-12-29
ok  have made some progress hav got original hd to boot from kubnuntu cd now then loaded ubuntu all went well, aid optin didn,t work but thks for help just rying to load spare drive up now just in case thks for help

---

### Post by spiky001 on 2009-12-29
just 2 add some more spare drive wont boot like other did so have put it in as slavecan open drive rad what is on it, would it be ok to format it by right mouse option do u think this will make it more bootable or is there a better way

---

