---
title: "netstat"
date: 2012-01-25
forum: General Help
---

### Post by loosescrew on 2012-01-25
I dont know a thing about netstat but it seems to me that i have a problem.All ports seem to be active.Can anyone tell me if this is right ? Thanks




```
joe@joe-laptop:~$ netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        1      0 joe-laptop.netgea:43876 l9.ycs.vip.a4e.yaho:www CLOSE_WAIT 
tcp        0      0 joe-laptop.netgea:52571 feijoa.canonical.co:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:52578 feijoa.canonical.co:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:52577 feijoa.canonical.co:www TIME_WAIT  
tcp        0      0 joe-laptop.netgea:52576 feijoa.canonical.co:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:40188 a96-6-123-99.deploy:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:43901 a96-6-123-98.deploy:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:52574 feijoa.canonical.co:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:52572 feijoa.canonical.co:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:52573 feijoa.canonical.co:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:52575 feijoa.canonical.co:www ESTABLISHED
tcp        1      0 joe-laptop.netgea:43875 l9.ycs.vip.a4e.yaho:www CLOSE_WAIT 
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  8      [ ]         DGRAM                    5932     /dev/log
unix  2      [ ]         DGRAM                    2741     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    2933     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    6194     @/org/freedesktop/hal/udev_event
unix  2      [ ]         DGRAM                    7140     /var/run/wpa_supplicant/wlan0
unix  3      [ ]         STREAM     CONNECTED     124968   
unix  3      [ ]         STREAM     CONNECTED     124967   
unix  3      [ ]         STREAM     CONNECTED     124955   @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     124954   
unix  3      [ ]         STREAM     CONNECTED     124953   /tmp/orbit-joe/linc-586c-0-297ed368d17d
unix  3      [ ]         STREAM     CONNECTED     124952   
unix  3      [ ]         STREAM     CONNECTED     124949   /tmp/orbit-joe/linc-2e47-0-675c2fc213dfe
unix  3      [ ]         STREAM     CONNECTED     124948   
unix  3      [ ]         STREAM     CONNECTED     124944   @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     124943   
unix  3      [ ]         STREAM     CONNECTED     124941   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     124940   
unix  3      [ ]         STREAM     CONNECTED     124846   /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     124845   
unix  3      [ ]         STREAM     CONNECTED     124827   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     124826   
unix  3      [ ]         STREAM     CONNECTED     124823   
unix  3      [ ]         STREAM     CONNECTED     124822   
unix  3      [ ]         STREAM     CONNECTED     124818   /tmp/orbit-joe/linc-584d-0-64dfa7b93149
unix  3      [ ]         STREAM     CONNECTED     124817   
unix  3      [ ]         STREAM     CONNECTED     124814   /tmp/orbit-joe/linc-2e47-0-675c2fc213dfe
unix  3      [ ]         STREAM     CONNECTED     124813   
unix  3      [ ]         STREAM     CONNECTED     124811   @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     124810   
unix  3      [ ]         STREAM     CONNECTED     124806   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     124805   
unix  3      [ ]         STREAM     CONNECTED     112398   @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     112397   
unix  3      [ ]         STREAM     CONNECTED     112395   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     112394   
unix  3      [ ]         STREAM     CONNECTED     112386   @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     112385   
unix  3      [ ]         STREAM     CONNECTED     112382   @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     112381   
unix  3      [ ]         STREAM     CONNECTED     112379   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     112378   
unix  3      [ ]         STREAM     CONNECTED     63111    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     63110    
unix  3      [ ]         STREAM     CONNECTED     63102    @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     63101    
unix  3      [ ]         STREAM     CONNECTED     63099    @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     63098    
unix  3      [ ]         STREAM     CONNECTED     63097    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     63096    
unix  3      [ ]         STREAM     CONNECTED     63021    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     63020    
unix  3      [ ]         STREAM     CONNECTED     63018    /tmp/orbit-joe/linc-2ee7-0-501d5d91ee5ad
unix  3      [ ]         STREAM     CONNECTED     63017    
unix  3      [ ]         STREAM     CONNECTED     63014    /tmp/orbit-joe/linc-2e47-0-675c2fc213dfe
unix  3      [ ]         STREAM     CONNECTED     63013    
unix  3      [ ]         STREAM     CONNECTED     63008    @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     63007    
unix  3      [ ]         STREAM     CONNECTED     62219    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     62218    
unix  3      [ ]         STREAM     CONNECTED     62217    /tmp/orbit-joe/linc-2e5f-0-5989f7789b5a6
unix  3      [ ]         STREAM     CONNECTED     62216    
unix  3      [ ]         STREAM     CONNECTED     62213    /tmp/orbit-joe/linc-2e47-0-675c2fc213dfe
unix  3      [ ]         STREAM     CONNECTED     62212    
unix  3      [ ]         STREAM     CONNECTED     62205    @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     62204    
unix  3      [ ]         STREAM     CONNECTED     62164    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     62163    
unix  3      [ ]         STREAM     CONNECTED     62036    @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     62035    
unix  3      [ ]         STREAM     CONNECTED     62031    @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     62030    
unix  3      [ ]         STREAM     CONNECTED     61988    @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     61986    
unix  3      [ ]         STREAM     CONNECTED     61977    /tmp/orbit-joe/linc-2e45-0-2abb9b1330181
unix  3      [ ]         STREAM     CONNECTED     61976    
unix  3      [ ]         STREAM     CONNECTED     61973    /tmp/orbit-joe/linc-2e47-0-675c2fc213dfe
unix  3      [ ]         STREAM     CONNECTED     61972    
unix  3      [ ]         STREAM     CONNECTED     61969    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     61968    
unix  3      [ ]         STREAM     CONNECTED     61780    @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     61779    
unix  3      [ ]         STREAM     CONNECTED     61766    @/tmp/dbus-rhsVrbrkvK
unix  3      [ ]         STREAM     CONNECTED     61765    
unix  3      [ ]         STREAM     CONNECTED     61763    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     61762    
unix  3      [ ]         STREAM     CONNECTED     55178    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     55177    
unix  3      [ ]         STREAM     CONNECTED     55173    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     55172    
unix  3      [ ]         STREAM     CONNECTED     55171    
unix  3      [ ]         STREAM     CONNECTED     55170    
unix  3      [ ]         STREAM     CONNECTED     55157    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     55156    
unix  3      [ ]         STREAM     CONNECTED     54267    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     54266    
unix  3      [ ]         STREAM     CONNECTED     54257    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     54256    
unix  3      [ ]         STREAM     CONNECTED     54113    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     54112    
unix  3      [ ]         STREAM     CONNECTED     54119    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     54111    
unix  3      [ ]         STREAM     CONNECTED     54098    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     54097    
unix  2      [ ]         DGRAM                    35234    
unix  2      [ ]         DGRAM                    7806     
unix  2      [ ]         DGRAM                    7284     
unix  3      [ ]         STREAM     CONNECTED     7225     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7224     
unix  3      [ ]         STREAM     CONNECTED     7125     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7124     
unix  3      [ ]         STREAM     CONNECTED     7035     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7034     
unix  3      [ ]         STREAM     CONNECTED     7029     
unix  3      [ ]         STREAM     CONNECTED     7028     
unix  2      [ ]         DGRAM                    7026     
unix  2      [ ]         DGRAM                    6826     
unix  3      [ ]         STREAM     CONNECTED     6825     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     6824     
unix  3      [ ]         STREAM     CONNECTED     6817     @/var/run/hald/dbus-9C6v6TVwJX
unix  3      [ ]         STREAM     CONNECTED     6814     
unix  3      [ ]         STREAM     CONNECTED     6816     @/var/run/hald/dbus-9C6v6TVwJX
unix  3      [ ]         STREAM     CONNECTED     6794     
unix  3      [ ]         STREAM     CONNECTED     6792     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6791     
unix  3      [ ]         STREAM     CONNECTED     6815     @/var/run/hald/dbus-9C6v6TVwJX
unix  3      [ ]         STREAM     CONNECTED     6781     
unix  3      [ ]         STREAM     CONNECTED     6779     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6778     
unix  3      [ ]         STREAM     CONNECTED     6651     @/var/run/hald/dbus-9C6v6TVwJX
unix  3      [ ]         STREAM     CONNECTED     6585     
unix  3      [ ]         STREAM     CONNECTED     6635     @/var/run/hald/dbus-9C6v6TVwJX
unix  3      [ ]         STREAM     CONNECTED     6315     
unix  3      [ ]         STREAM     CONNECTED     6184     @/var/run/hald/dbus-pOPFyC4TC6
unix  3      [ ]         STREAM     CONNECTED     6183     
unix  3      [ ]         STREAM     CONNECTED     6157     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6156     
unix  3      [ ]         STREAM     CONNECTED     6143     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6142     
unix  3      [ ]         STREAM     CONNECTED     6096     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6095     
unix  3      [ ]         STREAM     CONNECTED     6030     
unix  3      [ ]         STREAM     CONNECTED     6029     
unix  2      [ ]         DGRAM                    5986     
joe@joe-laptop:~$ 
```

---

### Post by Dangertux on 2012-01-25
```

tcp        1      0 joe-laptop.netgea:43876 l9.ycs.vip.a4e.yaho:www CLOSE_WAIT
tcp        0      0 joe-laptop.netgea:52571 feijoa.canonical.co:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:52578 feijoa.canonical.co:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:52577 feijoa.canonical.co:www TIME_WAIT  
tcp        0      0 joe-laptop.netgea:52576 feijoa.canonical.co:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:40188 a96-6-123-99.deploy:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:43901 a96-6-123-98.deploy:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:52574 feijoa.canonical.co:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:52572 feijoa.canonical.co:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:52573 feijoa.canonical.co:www ESTABLISHED
tcp        0      0 joe-laptop.netgea:52575 feijoa.canonical.co:www ESTABLISHED
tcp        1      0 joe-laptop.netgea:43875 l9.ycs.vip.a4e.yaho:www CLOSE_WAIT 

```

These are from your browser, loooks like yahoo, something else that I don't recognize and ubuntuforums lol :-P

The portion below that is for UNIX sockets, which are not the same as ports, though to communicate on a TCP/UDP port a socket must be created, many sockets are used for internal (non internet bound) connections that are necessary.

Your netstat looks fine to me :-)

Hope this helps.

---

### Post by loosescrew on 2012-01-25
Thanks You, Dangertux. I saw that and panicked.Thanks Joe :D

---

