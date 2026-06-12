---
title: "how to  install virtualboxsdk  ?"
date: 2010-05-07
forum: General Help
---

### Post by luofeiyu on 2010-05-07
i have downloaded VirtualBox 3.1.6 Software Developer Kit (SDK) All platforms (registration required) from the following:
[http://dlc.sun.com/virtualbox/vboxsdkdownload.html](http://dlc.sun.com/virtualbox/vboxsdkdownload.html)
i don't know how to install  it !

pt@pt-laptop:~$ python /home/pt/sdk/installer/vboxapisetup.py  install
Traceback (most recent call last):
  File "/home/pt/sdk/installer/vboxapisetup.py", line 61, in <module>
    main(sys.argv)
  File "/home/pt/sdk/installer/vboxapisetup.py", line 43, in main
    raise Exception("No VBOX_INSTALL_PATH defined, exiting")
Exception: No VBOX_INSTALL_PATH defined, exiting
pt@pt-laptop:~$ python /home/pt/sdk/installer/vboxapisetup.py install  /home/pt/vbox
Traceback (most recent call last):
  File "/home/pt/sdk/installer/vboxapisetup.py", line 61, in <module>
    main(sys.argv)
  File "/home/pt/sdk/installer/vboxapisetup.py", line 43, in main
    raise Exception("No VBOX_INSTALL_PATH defined, exiting")
Exception: No VBOX_INSTALL_PATH defined, exiting
pt@pt-laptop:~$

---

### Post by jbrown96 on 2010-05-07
It looks like you need to install Virtualbox first, then point the python script at that installation path. I'm guessing it's /usr/bin/VirtualBox or maybe just /usr/bin/

---

### Post by dino99 on 2010-05-07
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

