---
title: "Active UNIX domain sockets"
date: 2010-07-27
forum: General Help
---

### Post by dresortiz on 2010-07-27
After my first installation/ version of Ubuntu 64, I performed a netstat and noticed I did NOT have any Active UNIX domain sockets as I do now. After doing some research, I found this is related to MYSQL and server services which I am in no need of running and nor do I want to run if not needed. So exactly what are these services used for, which app is creating this and why?

Is it possible to remove the app or processes if they are not needed? Killing these connections every time they attempt to establish would be rhetorical.

~$ uname -a
Linux panda 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux


:~$ netstat | more
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  13     [ ]         DGRAM                    4195     /dev/log
unix  2      [ ]         DGRAM                    3064     @/org/kernel/udev/udevd
unix  3      [ ]         STREAM     CONNECTED     29848    @/org/wrapper/NSPlugins/libflashplayer.so/1784-1
unix  3      [ ]         STREAM     CONNECTED     29845    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     29844    
unix  3      [ ]         STREAM     CONNECTED     29841    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     29840    
unix  3      [ ]         STREAM     CONNECTED     29734    
unix  3      [ ]         STREAM     CONNECTED     19845    /home/andy/.pulse/de5655dfee2f9a085a8fb5974bdf5bde-runtime/native
unix  3      [ ]         STREAM     CONNECTED     19844    
unix  3      [ ]         STREAM     CONNECTED     13083    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     13082    
unix  3      [ ]         STREAM     CONNECTED     13036    @/tmp/dbus-tVP9XFDNhr
unix  3      [ ]         STREAM     CONNECTED     13035    
unix  3      [ ]         STREAM     CONNECTED     13015    /var/run/dbus/system_bus_socket

...... and the list goes on


Thanks

Acer Aspire 1410 w/ 4GB

---

### Post by efflandt on 2010-07-27
X uses domain sockets to communicate among itself, and the ones you list all appear to be related to X, display windows, sound, system bus, to tell when you connect things (CD/DVD, usb devices, etc). I looked at mine and cannot see anything that I can identify as being related to MYSQL.

---

