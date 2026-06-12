---
title: "Some info on netstat output."
date: 2010-04-11
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2010-04-11
So I am trying to figure out the output of netstat and need some of your helpful info, I'm really beginning my Linux journey but i am curious about a lot of things:-


netstat -paln

```

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      -               
tcp        0      0 192.168.1.2:56819       207.46.125.35:1863      ESTABLISHED 2705/pidgin     
udp        0      0 0.0.0.0:33633           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp        0      0 192.168.1.2:137         0.0.0.0:*                           -               
udp        0      0 0.0.0.0:137             0.0.0.0:*                           -               
udp        0      0 192.168.1.2:138         0.0.0.0:*                           -               
udp        0      0 0.0.0.0:138             0.0.0.0:*                           -               
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     5125     -                   /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     4873     -                   /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     8506     2512/gnome-keyring- /tmp/keyring-M4dM4k/socket
unix  2      [ ACC ]     STREAM     LISTENING     8706     -                   /tmp/ssh-oTaoSD2527/agent.2527
unix  2      [ ACC ]     STREAM     LISTENING     8841     2527/gnome-session  /tmp/.ICE-unix/2527
unix  2      [ ACC ]     STREAM     LISTENING     2869     -                   @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     8719     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  2      [ ACC ]     STREAM     LISTENING     5088     -                   @/var/run/hald/dbus-V07boij9be
unix  2      [ ACC ]     STREAM     LISTENING     8789     2576/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     8792     2576/pulseaudio     /home/axeface1111/.pulse/2da97c75a9a242d832f0110d4b48da0e-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     8862     2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  2      [ ACC ]     STREAM     LISTENING     9105     2527/gnome-session  /tmp/orbit-axeface1111/linc-9df-0-3e67bc7c9e8b2
unix  2      [ ACC ]     STREAM     LISTENING     9218     2594/gnome-settings /tmp/orbit-axeface1111/linc-a22-0-73f6e783debdc
unix  2      [ ACC ]     STREAM     LISTENING     9230     2512/gnome-keyring- /tmp/orbit-axeface1111/linc-9d0-0-55dd5070e39aa
unix  2      [ ACC ]     STREAM     LISTENING     9234     2512/gnome-keyring- /tmp/keyring-M4dM4k/socket.ssh
unix  2      [ ACC ]     STREAM     LISTENING     9236     2512/gnome-keyring- /tmp/keyring-M4dM4k/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     9361     2600/seahorse-daemo /tmp/orbit-axeface1111/linc-a28-0-71a13f153514c
unix  2      [ ACC ]     STREAM     LISTENING     9478     2631/notify-osd     /tmp/orbit-axeface1111/linc-a47-0-2561793593e3
unix  2      [ ACC ]     STREAM     LISTENING     6939     -                   @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     9681     2698/gnome-panel    /tmp/orbit-axeface1111/linc-a8a-0-4763b370c3ed1
unix  2      [ ACC ]     STREAM     LISTENING     10261    2733/gnome-screensa /tmp/orbit-axeface1111/linc-a9c-0-6cfb8e0e7de05
unix  2      [ ACC ]     STREAM     LISTENING     10298    2699/nautilus       /tmp/orbit-axeface1111/linc-a8b-0-38235d008a96c
unix  2      [ ACC ]     STREAM     LISTENING     10392    2725/gnome-power-ma /tmp/orbit-axeface1111/linc-aa5-0-828ce52cf4d5
unix  2      [ ACC ]     STREAM     LISTENING     10401    2723/nm-applet      /tmp/orbit-axeface1111/linc-aa3-0-c415278cfc18
unix  2      [ ACC ]     STREAM     LISTENING     6762     -                   /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     10521    2745/bonobo-activat /tmp/orbit-axeface1111/linc-ab9-0-3ddedec3656e5
unix  2      [ ACC ]     STREAM     LISTENING     10711    2756/gnome-dictiona /tmp/orbit-axeface1111/linc-ac4-0-16faf28fa20b4
unix  2      [ ACC ]     STREAM     LISTENING     10715    2757/trashapplet    /tmp/orbit-axeface1111/linc-ac5-0-6f961fdfa2377
unix  2      [ ACC ]     STREAM     LISTENING     10731    2759/multiload-appl /tmp/orbit-axeface1111/linc-ac7-0-3c838ccda5b6c
unix  2      [ ]         DGRAM                    2939     -                   @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     10758    2761/indicator-appl /tmp/orbit-axeface1111/linc-ac9-0-7c2c987dafc5a
unix  2      [ ACC ]     STREAM     LISTENING     10795    2697/compiz.real    /tmp/orbit-axeface1111/linc-a89-0-1e9fdac3a218
unix  2      [ ACC ]     STREAM     LISTENING     5492     -                   /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     7700     -                   @/tmp/gdm-session-uFoFfUHd
unix  2      [ ACC ]     STREAM     LISTENING     6940     -                   /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     12486    2812/indicator-sess /tmp/orbit-axeface1111/linc-afc-0-88e4553ccad2
unix  2      [ ACC ]     STREAM     LISTENING     12594    2814/gtk-window-dec /tmp/orbit-axeface1111/linc-afe-0-7ad1c4f740a2e
unix  2      [ ACC ]     STREAM     LISTENING     12859    2846/gnome-terminal /tmp/orbit-axeface1111/linc-b1e-0-16f9265b49dcb
unix  2      [ ACC ]     STREAM     LISTENING     12943    2849/awn            /tmp/orbit-axeface1111/linc-b21-0-4cd95f6390af6
unix  2      [ ACC ]     STREAM     LISTENING     13034    2856/python         /tmp/orbit-axeface1111/linc-b28-0-20573f74308a2
unix  2      [ ]         DGRAM                    5584     -                   @/org/freedesktop/hal/udev_event
unix  2      [ ACC ]     STREAM     LISTENING     7525     -                   @/tmp/gdm-greeter-zWJymzro
unix  2      [ ACC ]     STREAM     LISTENING     5174     -                   @/var/run/hald/dbus-QzltbE5QCD
unix  14     [ ]         DGRAM                    5085     -                   /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     6760     -                   /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     8840     2527/gnome-session  @/tmp/.ICE-unix/2527
unix  3      [ ]         STREAM     CONNECTED     54340    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     54339    2759/multiload-appl 
unix  3      [ ]         STREAM     CONNECTED     13091    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     13090    2856/python         
unix  3      [ ]         STREAM     CONNECTED     13039    -                   
unix  3      [ ]         STREAM     CONNECTED     13038    2846/gnome-terminal 
unix  3      [ ]         STREAM     CONNECTED     13037    2856/python         /tmp/orbit-axeface1111/linc-b28-0-20573f74308a2
unix  3      [ ]         STREAM     CONNECTED     13036    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     13033    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     13032    2856/python         
unix  3      [ ]         STREAM     CONNECTED     13027    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     13026    2856/python         
unix  3      [ ]         STREAM     CONNECTED     13024    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13023    2856/python         
unix  3      [ ]         STREAM     CONNECTED     13003    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     13002    2852/Separator      
unix  3      [ ]         STREAM     CONNECTED     12999    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     12998    2852/Separator      
unix  3      [ ]         STREAM     CONNECTED     12992    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12991    2852/Separator      
unix  3      [ ]         STREAM     CONNECTED     12946    2849/awn            /tmp/orbit-axeface1111/linc-b21-0-4cd95f6390af6
unix  3      [ ]         STREAM     CONNECTED     12945    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     12942    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     12941    2849/awn            
unix  3      [ ]         STREAM     CONNECTED     12924    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     12923    2849/awn            
unix  3      [ ]         STREAM     CONNECTED     12888    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12887    2849/awn            
unix  3      [ ]         STREAM     CONNECTED     12865    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     12864    2846/gnome-terminal 
unix  3      [ ]         STREAM     CONNECTED     12862    2846/gnome-terminal /tmp/orbit-axeface1111/linc-b1e-0-16f9265b49dcb
unix  3      [ ]         STREAM     CONNECTED     12861    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     12858    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     12857    2846/gnome-terminal 
unix  3      [ ]         STREAM     CONNECTED     12852    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     12851    2846/gnome-terminal 
unix  3      [ ]         STREAM     CONNECTED     12850    2527/gnome-session  @/tmp/.ICE-unix/2527
unix  3      [ ]         STREAM     CONNECTED     12849    2846/gnome-terminal 
unix  3      [ ]         STREAM     CONNECTED     12847    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12846    2846/gnome-terminal 
unix  3      [ ]         STREAM     CONNECTED     12724    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     12723    2723/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     12720    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     12719    2837/gvfsd-metadata 
unix  3      [ ]         STREAM     CONNECTED     12597    2814/gtk-window-dec /tmp/orbit-axeface1111/linc-afe-0-7ad1c4f740a2e
unix  3      [ ]         STREAM     CONNECTED     12596    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     12593    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     12592    2814/gtk-window-dec 
unix  3      [ ]         STREAM     CONNECTED     12585    2819/gvfsd-burn     @/dbus-vfs-daemon/socket-u9UWyP0e
unix  3      [ ]         STREAM     CONNECTED     12584    2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     12586    2819/gvfsd-burn     @/dbus-vfs-daemon/socket-f92NcQxb
unix  3      [ ]         STREAM     CONNECTED     12583    2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     12575    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     12574    2819/gvfsd-burn     
unix  3      [ ]         STREAM     CONNECTED     12551    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     12550    2814/gtk-window-dec 
unix  3      [ ]         STREAM     CONNECTED     12544    2698/gnome-panel    /tmp/orbit-axeface1111/linc-a8a-0-4763b370c3ed1
unix  3      [ ]         STREAM     CONNECTED     12543    2759/multiload-appl 
unix  3      [ ]         STREAM     CONNECTED     12496    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12495    2814/gtk-window-dec 
unix  3      [ ]         STREAM     CONNECTED     12491    -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12490    2812/indicator-sess 
unix  3      [ ]         STREAM     CONNECTED     12489    2812/indicator-sess /tmp/orbit-axeface1111/linc-afc-0-88e4553ccad2
unix  3      [ ]         STREAM     CONNECTED     12488    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     12485    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     12484    2812/indicator-sess 
unix  3      [ ]         STREAM     CONNECTED     12472    -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12471    2810/indicator-user 
unix  3      [ ]         STREAM     CONNECTED     12464    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     12460    2812/indicator-sess 
unix  3      [ ]         STREAM     CONNECTED     12455    2698/gnome-panel    /tmp/orbit-axeface1111/linc-a8a-0-4763b370c3ed1
unix  3      [ ]         STREAM     CONNECTED     12454    2757/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     12463    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     12453    2808/indicator-stat 
unix  3      [ ]         STREAM     CONNECTED     12462    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     12452    2810/indicator-user 
unix  3      [ ]         STREAM     CONNECTED     12430    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     12429    2761/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     12389    2576/pulseaudio     /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     12388    2761/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     12387    2527/gnome-session  @/tmp/.ICE-unix/2527
unix  3      [ ]         STREAM     CONNECTED     12386    2705/pidgin         
unix  3      [ ]         STREAM     CONNECTED     12373    2527/gnome-session  @/tmp/.ICE-unix/2527
unix  3      [ ]         STREAM     CONNECTED     12372    2761/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     12376    2698/gnome-panel    /tmp/orbit-axeface1111/linc-a8a-0-4763b370c3ed1
unix  3      [ ]         STREAM     CONNECTED     12371    2761/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     12369    2698/gnome-panel    /tmp/orbit-axeface1111/linc-a8a-0-4763b370c3ed1
unix  3      [ ]         STREAM     CONNECTED     12368    2756/gnome-dictiona 
unix  3      [ ]         STREAM     CONNECTED     12360    2756/gnome-dictiona /tmp/orbit-axeface1111/linc-ac4-0-16faf28fa20b4
unix  3      [ ]         STREAM     CONNECTED     12359    2698/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     12363    2761/indicator-appl /tmp/orbit-axeface1111/linc-ac9-0-7c2c987dafc5a
unix  3      [ ]         STREAM     CONNECTED     12358    2698/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     12362    2757/trashapplet    /tmp/orbit-axeface1111/linc-ac5-0-6f961fdfa2377
unix  3      [ ]         STREAM     CONNECTED     12357    2698/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     12361    2759/multiload-appl /tmp/orbit-axeface1111/linc-ac7-0-3c838ccda5b6c
unix  3      [ ]         STREAM     CONNECTED     12356    2698/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     12345    2743/gvfsd-trash    @/dbus-vfs-daemon/socket-VhEZ0Lgb
unix  3      [ ]         STREAM     CONNECTED     12340    2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     12346    2743/gvfsd-trash    @/dbus-vfs-daemon/socket-92bbgvDz
unix  3      [ ]         STREAM     CONNECTED     12339    2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     12338    -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12337    2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     10798    2697/compiz.real    /tmp/orbit-axeface1111/linc-a89-0-1e9fdac3a218
unix  3      [ ]         STREAM     CONNECTED     10797    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10794    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     10793    2697/compiz.real    
unix  3      [ ]         STREAM     CONNECTED     10785    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10784    2697/compiz.real    
unix  3      [ ]         STREAM     CONNECTED     10783    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10782    2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     10781    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10780    2756/gnome-dictiona 
unix  3      [ ]         STREAM     CONNECTED     10778    2743/gvfsd-trash    @/dbus-vfs-daemon/socket-gX1CWU6h
unix  3      [ ]         STREAM     CONNECTED     10777    2757/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     10779    2743/gvfsd-trash    @/dbus-vfs-daemon/socket-EcVkrQ8w
unix  3      [ ]         STREAM     CONNECTED     10776    2757/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     10775    2761/indicator-appl /tmp/orbit-axeface1111/linc-ac9-0-7c2c987dafc5a
unix  3      [ ]         STREAM     CONNECTED     10774    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10773    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     10772    2761/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     10770    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10769    2761/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     10764    2743/gvfsd-trash    @/dbus-vfs-daemon/socket-EcUq3k3g
unix  3      [ ]         STREAM     CONNECTED     10763    2757/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     10765    2743/gvfsd-trash    @/dbus-vfs-daemon/socket-2m5zIsFg
unix  3      [ ]         STREAM     CONNECTED     10762    2757/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     10766    2761/indicator-appl /tmp/orbit-axeface1111/linc-ac9-0-7c2c987dafc5a
unix  3      [ ]         STREAM     CONNECTED     10761    2745/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     10760    2745/bonobo-activat /tmp/orbit-axeface1111/linc-ab9-0-3ddedec3656e5
unix  3      [ ]         STREAM     CONNECTED     10757    2761/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     10754    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10753    2757/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     10752    2759/multiload-appl /tmp/orbit-axeface1111/linc-ac7-0-3c838ccda5b6c
unix  3      [ ]         STREAM     CONNECTED     10751    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10750    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     10749    2759/multiload-appl 
unix  3      [ ]         STREAM     CONNECTED     10747    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10746    2759/multiload-appl 
unix  3      [ ]         STREAM     CONNECTED     10744    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10743    2757/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     10742    2757/trashapplet    /tmp/orbit-axeface1111/linc-ac5-0-6f961fdfa2377
unix  3      [ ]         STREAM     CONNECTED     10741    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10740    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     10739    2757/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     10738    2756/gnome-dictiona /tmp/orbit-axeface1111/linc-ac4-0-16faf28fa20b4
unix  3      [ ]         STREAM     CONNECTED     10737    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10736    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     10735    2756/gnome-dictiona 
unix  3      [ ]         STREAM     CONNECTED     10745    2759/multiload-appl /tmp/orbit-axeface1111/linc-ac7-0-3c838ccda5b6c
unix  3      [ ]         STREAM     CONNECTED     10734    2745/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     10733    2745/bonobo-activat /tmp/orbit-axeface1111/linc-ab9-0-3ddedec3656e5
unix  3      [ ]         STREAM     CONNECTED     10730    2759/multiload-appl 
unix  3      [ ]         STREAM     CONNECTED     10725    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10724    2757/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     10721    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10720    2756/gnome-dictiona 
unix  3      [ ]         STREAM     CONNECTED     10723    2757/trashapplet    /tmp/orbit-axeface1111/linc-ac5-0-6f961fdfa2377
unix  3      [ ]         STREAM     CONNECTED     10718    2745/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     10717    2745/bonobo-activat /tmp/orbit-axeface1111/linc-ab9-0-3ddedec3656e5
unix  3      [ ]         STREAM     CONNECTED     10714    2757/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     10719    2756/gnome-dictiona /tmp/orbit-axeface1111/linc-ac4-0-16faf28fa20b4
unix  3      [ ]         STREAM     CONNECTED     10713    2745/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     10703    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10702    2761/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     10701    2745/bonobo-activat /tmp/orbit-axeface1111/linc-ab9-0-3ddedec3656e5
unix  3      [ ]         STREAM     CONNECTED     10700    2756/gnome-dictiona 
unix  3      [ ]         STREAM     CONNECTED     10696    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10695    2757/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     10692    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10691    2756/gnome-dictiona 
unix  3      [ ]         STREAM     CONNECTED     10688    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10687    2759/multiload-appl 
unix  3      [ ]         STREAM     CONNECTED     10640    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10639    2705/pidgin         
unix  3      [ ]         STREAM     CONNECTED     10530    2698/gnome-panel    /tmp/orbit-axeface1111/linc-a8a-0-4763b370c3ed1
unix  3      [ ]         STREAM     CONNECTED     10529    2745/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     10528    2745/bonobo-activat /tmp/orbit-axeface1111/linc-ab9-0-3ddedec3656e5
unix  3      [ ]         STREAM     CONNECTED     10527    2698/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     10524    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10523    2745/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     10512    2743/gvfsd-trash    @/dbus-vfs-daemon/socket-PhU4skg3
unix  3      [ ]         STREAM     CONNECTED     10511    2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     10513    2743/gvfsd-trash    @/dbus-vfs-daemon/socket-K2LywShV
unix  3      [ ]         STREAM     CONNECTED     10510    2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     10502    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10501    2743/gvfsd-trash    
unix  3      [ ]         STREAM     CONNECTED     10499    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10498    2717/gnome-volume-c 
unix  3      [ ]         STREAM     CONNECTED     10461    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10460    2743/gvfsd-trash    
unix  3      [ ]         STREAM     CONNECTED     10440    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10439    2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     10429    -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10428    2705/pidgin         
unix  3      [ ]         STREAM     CONNECTED     10417    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10416    2737/gvfs-gphoto2-v 
unix  3      [ ]         STREAM     CONNECTED     10409    -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10408    2723/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     10407    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10406    2721/gdu-notificati 
unix  3      [ ]         STREAM     CONNECTED     10404    2723/nm-applet      /tmp/orbit-axeface1111/linc-aa3-0-c415278cfc18
unix  3      [ ]         STREAM     CONNECTED     10403    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10400    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     10399    2723/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     10395    2725/gnome-power-ma /tmp/orbit-axeface1111/linc-aa5-0-828ce52cf4d5
unix  3      [ ]         STREAM     CONNECTED     10394    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10391    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     10390    2725/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     10385    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10384    2701/gvfs-gdu-volum 
unix  3      [ ]         STREAM     CONNECTED     10382    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10381    2723/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     10380    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10379    2725/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     10374    -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10373    -                   
unix  3      [ ]         STREAM     CONNECTED     10371    2576/pulseaudio     /home/axeface1111/.pulse/2da97c75a9a242d832f0110d4b48da0e-runtime/native
unix  3      [ ]         STREAM     CONNECTED     10370    2717/gnome-volume-c 
unix  3      [ ]         STREAM     CONNECTED     10372    -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10365    2725/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     10359    -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10357    2721/gdu-notificati 
unix  3      [ ]         STREAM     CONNECTED     10355    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10354    2721/gdu-notificati 
unix  3      [ ]         STREAM     CONNECTED     10353    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10352    2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     10350    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10349    2725/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     10327    -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10319    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10318    2723/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     10309    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10308    2717/gnome-volume-c 
unix  3      [ ]         STREAM     CONNECTED     10301    2699/nautilus       /tmp/orbit-axeface1111/linc-a8b-0-38235d008a96c
unix  3      [ ]         STREAM     CONNECTED     10300    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10297    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     10294    2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     10281    2720/polkit-gnome-a 
unix  3      [ ]         STREAM     CONNECTED     10279    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10278    2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     10276    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10275    2721/gdu-notificati 
unix  3      [ ]         STREAM     CONNECTED     10266    -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10265    2733/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     10264    2733/gnome-screensa /tmp/orbit-axeface1111/linc-a9c-0-6cfb8e0e7de05
unix  3      [ ]         STREAM     CONNECTED     10263    2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10260    2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     10259    2733/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     10169    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10168    2717/gnome-volume-c 
unix  3      [ ]         STREAM     CONNECTED     10165    2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     10164    2733/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     10130    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10118    2720/polkit-gnome-a 
unix  3      [ ]         STREAM     CONNECTED     10045    -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10044    2733/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     9933     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9932     2705/pidgin         
unix  3      [ ]         STREAM     CONNECTED     9898     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9897     2705/pidgin         
unix  3      [ ]         STREAM     CONNECTED     9764     2527/gnome-session  @/tmp/.ICE-unix/2527
unix  3      [ ]         STREAM     CONNECTED     9763     2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     9760     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9759     -                   
unix  3      [ ]         STREAM     CONNECTED     9755     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9753     -                   
unix  3      [ ]         STREAM     CONNECTED     9744     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9743     2699/nautilus       
unix  3      [ ]         STREAM     CONNECTED     9740     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9739     2701/gvfs-gdu-volum 
unix  3      [ ]         STREAM     CONNECTED     9734     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9732     2701/gvfs-gdu-volum 
unix  3      [ ]         STREAM     CONNECTED     9727     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9726     2698/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     9694     2527/gnome-session  @/tmp/.ICE-unix/2527
unix  3      [ ]         STREAM     CONNECTED     9693     2698/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     9692     2576/pulseaudio     /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     9691     2698/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     9689     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9688     2698/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     9686     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9685     2698/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     9684     2698/gnome-panel    /tmp/orbit-axeface1111/linc-a8a-0-4763b370c3ed1
unix  3      [ ]         STREAM     CONNECTED     9683     2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     9680     2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     9679     2698/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     9677     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9676     2698/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     9672     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9671     2698/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     9668     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9667     2697/compiz.real    
unix  3      [ ]         STREAM     CONNECTED     9636     2527/gnome-session  @/tmp/.ICE-unix/2527
unix  3      [ ]         STREAM     CONNECTED     9635     2697/compiz.real    
unix  3      [ ]         STREAM     CONNECTED     9487     2576/pulseaudio     /home/axeface1111/.pulse/2da97c75a9a242d832f0110d4b48da0e-runtime/native
unix  3      [ ]         STREAM     CONNECTED     9486     2594/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     9481     2631/notify-osd     /tmp/orbit-axeface1111/linc-a47-0-2561793593e3
unix  3      [ ]         STREAM     CONNECTED     9480     2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     9477     2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     9476     2631/notify-osd     
unix  3      [ ]         STREAM     CONNECTED     9471     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9470     2631/notify-osd     
unix  3      [ ]         STREAM     CONNECTED     9468     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9467     2631/notify-osd     
unix  3      [ ]         STREAM     CONNECTED     9459     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9458     2594/gnome-settings 
unix  2      [ ]         DGRAM                    9365     2600/seahorse-daemo 
unix  3      [ ]         STREAM     CONNECTED     9364     2600/seahorse-daemo /tmp/orbit-axeface1111/linc-a28-0-71a13f153514c
unix  3      [ ]         STREAM     CONNECTED     9363     2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     9360     2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     9359     2600/seahorse-daemo 
unix  3      [ ]         STREAM     CONNECTED     9356     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9355     2600/seahorse-daemo 
unix  3      [ ]         STREAM     CONNECTED     9354     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9353     2600/seahorse-daemo 
unix  3      [ ]         STREAM     CONNECTED     9347     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9346     2608/gvfs-fuse-daem 
unix  3      [ ]         STREAM     CONNECTED     9330     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9329     2608/gvfs-fuse-daem 
unix  3      [ ]         STREAM     CONNECTED     9285     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9283     2602/gvfsd          
unix  3      [ ]         STREAM     CONNECTED     9277     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9276     2600/seahorse-daemo 
unix  3      [ ]         STREAM     CONNECTED     9233     2512/gnome-keyring- /tmp/orbit-axeface1111/linc-9d0-0-55dd5070e39aa
unix  3      [ ]         STREAM     CONNECTED     9232     2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     9229     2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     9228     2512/gnome-keyring- 
unix  3      [ ]         STREAM     CONNECTED     9225     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9224     2600/seahorse-daemo 
unix  3      [ ]         STREAM     CONNECTED     9221     2594/gnome-settings /tmp/orbit-axeface1111/linc-a22-0-73f6e783debdc
unix  3      [ ]         STREAM     CONNECTED     9220     2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     9217     2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     9216     2594/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     9212     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9211     2512/gnome-keyring- 
unix  3      [ ]         STREAM     CONNECTED     9175     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     9174     2594/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     9143     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9142     2594/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     9108     2527/gnome-session  /tmp/orbit-axeface1111/linc-9df-0-3e67bc7c9e8b2
unix  3      [ ]         STREAM     CONNECTED     9107     2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     9104     2591/gconfd-2       /tmp/orbit-axeface1111/linc-a1f-0-3fe7b63a9af0a
unix  3      [ ]         STREAM     CONNECTED     9103     2527/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     9099     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9098     2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     8866     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     8864     2591/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     8852     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8851     2527/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     8822     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     8821     2527/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     8819     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8818     2527/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     8806     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8805     2576/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     8795     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8794     2576/pulseaudio     
unix  2      [ ]         DGRAM                    8786     2576/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     8750     2571/dbus-daemon    @/tmp/dbus-xFgKsTYNZR
unix  3      [ ]         STREAM     CONNECTED     8749     2576/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     8741     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8740     2576/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     8723     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8722     2572/dbus-launch    
unix  3      [ ]         STREAM     CONNECTED     8721     2571/dbus-daemon    
unix  3      [ ]         STREAM     CONNECTED     8720     2571/dbus-daemon    
unix  3      [ ]         STREAM     CONNECTED     8709     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8708     2572/dbus-launch    
unix  3      [ ]         STREAM     CONNECTED     8511     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8510     -                   
unix  2      [ ]         DGRAM                    8498     -                   
unix  3      [ ]         STREAM     CONNECTED     8154     -                   @/tmp/gdm-session-uFoFfUHd
unix  3      [ ]         STREAM     CONNECTED     8152     -                   
unix  3      [ ]         STREAM     CONNECTED     7748     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7747     -                   
unix  3      [ ]         STREAM     CONNECTED     7744     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7742     -                   
unix  3      [ ]         STREAM     CONNECTED     7699     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7698     -                   
unix  3      [ ]         STREAM     CONNECTED     7668     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7667     -                   
unix  2      [ ]         DGRAM                    7645     -                   
unix  3      [ ]         STREAM     CONNECTED     7527     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7526     -                   
unix  3      [ ]         STREAM     CONNECTED     7476     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7440     -                   
unix  3      [ ]         STREAM     CONNECTED     7439     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7438     -                   
unix  3      [ ]         STREAM     CONNECTED     6972     -                   /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     6971     -                   
unix  2      [ ]         DGRAM                    6874     -                   
unix  3      [ ]         STREAM     CONNECTED     6871     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6870     -                   
unix  3      [ ]         STREAM     CONNECTED     6843     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6842     -                   
unix  3      [ ]         STREAM     CONNECTED     6765     -                   
unix  3      [ ]         STREAM     CONNECTED     6764     -                   
unix  3      [ ]         STREAM     CONNECTED     6162     -                   @/var/run/hald/dbus-V07boij9be
unix  3      [ ]         STREAM     CONNECTED     6161     -                   
unix  3      [ ]         STREAM     CONNECTED     6145     -                   /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     6144     -                   
unix  3      [ ]         STREAM     CONNECTED     6139     -                   @/var/run/hald/dbus-V07boij9be
unix  3      [ ]         STREAM     CONNECTED     6133     -                   
unix  3      [ ]         STREAM     CONNECTED     6137     -                   @/var/run/hald/dbus-V07boij9be
unix  3      [ ]         STREAM     CONNECTED     6099     -                   
unix  3      [ ]         STREAM     CONNECTED     6095     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6094     -                   
unix  2      [ ]         DGRAM                    5503     -                   
unix  2      [ ]         DGRAM                    5496     -                   
unix  2      [ ]         DGRAM                    5382     -                   
unix  3      [ ]         STREAM     CONNECTED     5313     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5311     -                   
unix  2      [ ]         DGRAM                    5310     -                   
unix  3      [ ]         STREAM     CONNECTED     5191     -                   @/var/run/hald/dbus-QzltbE5QCD
unix  3      [ ]         STREAM     CONNECTED     5190     -                   
unix  2      [ ]         DGRAM                    5170     -                   
unix  3      [ ]         STREAM     CONNECTED     5164     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5163     -                   
unix  3      [ ]         STREAM     CONNECTED     5160     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5159     -                   
unix  3      [ ]         STREAM     CONNECTED     5140     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5139     -                   
unix  3      [ ]         STREAM     CONNECTED     5135     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5132     -                   
unix  2      [ ]         DGRAM                    5129     -                   
unix  3      [ ]         STREAM     CONNECTED     5134     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5127     -                   
unix  3      [ ]         STREAM     CONNECTED     5122     -                   
unix  3      [ ]         STREAM     CONNECTED     5121     -                   
unix  2      [ ]         DGRAM                    5119     -                   
unix  3      [ ]         STREAM     CONNECTED     5133     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5103     -                   
unix  3      [ ]         STREAM     CONNECTED     5090     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5089     -                   
unix  3      [ ]         STREAM     CONNECTED     4884     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4883     -                   
unix  3      [ ]         STREAM     CONNECTED     4878     -                   
unix  3      [ ]         STREAM     CONNECTED     4877     -                   
unix  3      [ ]         DGRAM                    2973     -                   
unix  3      [ ]         DGRAM                    2972     -                   
unix  3      [ ]         STREAM     CONNECTED     2937     -                   @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     2933     -                   
unix  3      [ ]         STREAM     CONNECTED     2880     -                   @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     2877     -   
```


what exactly are 'Active UNIX domain sockets'? how do they differ from traditional TCP connections and why are they listed with a networking tool? ie, why does netstat show them?

also, what's the difference between 0.0.0.0 and localhost?

Thank you.

---

### Post by nischalinn on 2010-04-11
Refer to the manual page of netstat from google.

Active Unix Domain Socket is used for communication over a local network. It's a way for processes to communicate with each other without using  an IP or other network protocol.

---

### Post by efflandt on 2010-04-11
0.0.0.0 is "any" IP

localhost is 127.0.0.1 (an internal loopback IP on the same computer)

X uses domain sockets to communicate among X programs and the display.  You can even run X programs remotely.  For example if you have **ForwardX11 yes** in your ~/.ssh/config, you can ssh to another PC, run an X program there, and have it display in X on your local computer.

---

### Post by NiGhtMarEs0nWax on 2010-04-11
> **nischalinn said:**
> 
Active Unix Domain Socket is used for communication over a local network. It's a way for processes to communicate with each other without using  an IP or other network protocol.

according to [wiki]("http://en.wikipedia.org/wiki/Unix_domain_socket") they refer to local connections only, does that mean in terms of security i don't have to worry about them? i mean, they are not actual network processes, so they cannot be exploited in that sense?

thanks

---

### Post by NiGhtMarEs0nWax on 2010-04-11
> **efflandt said:**
> 0.0.0.0 is "any" IP


in context, what does it mean when such an address is in the local & foreign address fields?

also, if 0.0.0.0 means any address does, 255.255.255.0 in a sense have a /24 bit mask, meaning IPs from that particular subnet? (sorry if the terminology is wrong)

---

### Post by NiGhtMarEs0nWax on 2010-04-13
bump, the manual page is useful to explain what the options do, but they don't really help me in the way of concepts.

Thank you.

---

