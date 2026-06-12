---
title: "Wacomcpl not loading"
date: 2009-07-20
forum: General Help
---

### Post by Sawer on 2009-07-20
I can't  get wacomcpl to load. I have changed the fdi to one I know works, installed the wacom tools and rebooted. wacomcpl should show up. I don't have the use of my stylus either.
Here is  what I get from the cml
wacomcpl: using TCLLIBPATH="[list  /usr/lib ]"
Error in startup script: Get: Unknown parameter 'SBottomX8'
    while executing
"exec xsetwacom get $dev SBottomX$i "
    (procedure "createScreenList" line 7)
    invoked from within
"createScreenList $dev"
    (procedure "createDeviceList" line 37)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 8)
    invoked from within
"createControls"
    (file "/usr/bin/wacomcpl-exec" line 1860)
scott@E-machine:~$

Hope this  helps not being much of a geek I'm not able to  make sense of this.
Thanks

---

