---
title: "howto - remove bluebirds"
date: 2012-10-01
forum: General Help
---

### Post by freedomAboveAll on 2012-10-01
This is a follow-up / update on removing the BlueBirds adware from an LG DVDRAM GH22LS50 using Ubuntu 12.04.1.  

This thread addressed this issue for earlier Ubuntu but is closed: 
[http://ubuntuforums.org/showthread.php?t=1205921&page=2](http://ubuntuforums.org/showthread.php?t=1205921&page=2)

The only solution I could find was the wine solution -  
Install wine and run the firmware update as root.

Steps:

1. get your model number of cdrom by running $  lshw > my_computer_hardware_output.txt
2. Go to LG site and download the firmware update [http://www.lg.com/us/support-product/lg-GH22NS50](http://www.lg.com/us/support-product/lg-GH22NS50)
3. install wine  $ sudo apt-get install wine
then ...
```

$ su
root@ $   wine GH22LS50_TL03.exe
Open the CD-Rom tray.
Press the Update option.

```


Hope this helps someone.

---

