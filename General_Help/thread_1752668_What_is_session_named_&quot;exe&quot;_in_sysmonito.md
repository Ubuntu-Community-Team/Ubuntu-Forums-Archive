---
title: "What is session named &quot;exe&quot; in sysmonitor?"
date: 2011-05-08
forum: General Help
---

### Post by mrphoenix on 2011-05-08
Hey, I just wondering in the last days always there is an unknown session in my sysmonitor, which name is only "exe" and its always in zombie mode and I can't kill this.
What is this? And why its there?

---

### Post by Karlchen on 2011-05-08
Hello, mrphoenix.
> What is this? And why its there? I have not got the faintest idea. Yet, I have got an idea how *you might find out yourself*:

[LIST]
[*]Inside System Monitor switch to the tab "Processes". From the System Monitor main menu bar select "Edit" => "Preferences". The tab "Processes" will be pre-selected. Fine. Make sure that at minimum the following columns will be displayed in the processes tab by ticking the items in case they have not been ticked yet:
+ process name
+ user
+ status
+ process ID (PID)
+ commandline
When you are done click on the "Close" button.
[*]From the System Monitor main menu bar select "View". Make sure that **(*) All processes** will be displayed including their **[X] Dependencies**.
[*]Inside the "Processes" tab locate the zombie process named "exe" and let us know, please:
+ under which account has it been started?
+ what is the exact commandline?
+ can you determine the parent process?
[/LIST]
Cheers,
Karl

---

### Post by mrphoenix on 2011-05-08
> **Karlchen said:**
> Hello, mrphoenix.
I have not got the faintest idea. Yet, I have got an idea how *you might find out yourself*:

[LIST]
[*]Inside System Monitor switch to the tab "Processes". From the System Monitor main menu bar select "Edit" => "Preferences". The tab "Processes" will be pre-selected. Fine. Make sure that at minimum the following columns will be displayed in the processes tab by ticking the items in case they have not been ticked yet:
+ process name
+ user
+ status
+ process ID (PID)
+ commandline
When you are done click on the "Close" button.
[*]From the System Monitor main menu bar select "View". Make sure that **(*) All processes** will be displayed including their **[X] Dependencies**.
[*]Inside the "Processes" tab locate the zombie process named "exe" and let us know, please:
+ under which account has it been started?
+ what is the exact commandline?
+ can you determine the parent process?
[/LIST]
Cheers,
Karl

Thanks for the answer.
I did all what you want so:

+ under which account has it been started? -> phoenix, which is my only user
+ what is the exact commandline? -> exe -> yes, its all there I can see
+ can you determine the parent process? -> no. how to do it?

---

### Post by Karlchen on 2011-05-08
Hello, mrphoenix.

OK, the username was of interest in order to find out whether "exe" was a system process (run by root e.g.) or a user process. As it is launched under your account it this strongly suggests that it is a user process.

About the complete commandline: it would be helpful if you posted the complete commandline. It might hold details which will help determine what "exe" might be.

Cheers,
Karl

---

### Post by mrphoenix on 2011-05-09
> **Karlchen said:**
> Hello, mrphoenix.

OK, the username was of interest in order to find out whether "exe" was a system process (run by root e.g.) or a user process. As it is launched under your account it this strongly suggests that it is a user process.

About the complete commandline: it would be helpful if you posted the complete commandline. It might hold details which will help determine what "exe" might be.

Cheers,
Karl

[http://kepfeltoltes.hu/110509/K_perny_k_p-Rendszerfigyel__www.kepfeltoltes.hu_.png](http://kepfeltoltes.hu/110509/K_perny_k_p-Rendszerfigyel__www.kepfeltoltes.hu_.png)

---

### Post by renkinjutsu on 2011-05-09
exe (for me) is usually just a flash video.

You can try to find out what program started it by doing this:
```
ps -o ppid,comm | grep exe
```
The above command *should* give you the PID of its parent proccess.

---

### Post by mrphoenix on 2011-05-09
> **renkinjutsu said:**
> exe (for me) is usually just a flash video.

You can try to find out what program started it by doing this:
```
ps -o ppid,comm | grep exe
```
The above command *should* give you the PID of its parent proccess.

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                    
 1709 phoenix   20   0 67156  47m  13m S  2.3  4.7   0:38.17 compiz                                                                                                     
 2140 phoenix   20   0  211m  88m  18m S  1.6  8.8   0:21.42 chrome                                                                                                     
  631 phoenix   20   0  2904 1480 1132 R  1.3  0.1   0:00.31 top                                                                                                        
26961 phoenix   20   0  259m  14m  11m S  1.3  1.4   0:03.89 gnome-terminal                                                                                             
 2030 phoenix   20   0  566m  83m  21m S  0.7  8.4   0:34.50 chrome                                                                                                     
 2256 phoenix   20   0  248m  20m  11m S  0.7  2.0   0:31.47 chrome                                                                                                     
 1728 phoenix   20   0  256m  36m  15m S  0.3  3.7   0:02.69 cairo-dock                                                                                                 
 1804 phoenix   20   0  168m  11m 9736 S  0.3  1.2   0:04.42 netspeed_applet                                                                                            
 1636 phoenix   20   0 25504 2108 1552 S  0.0  0.2   0:00.03 gnome-keyring-d                                                                                            
 1654 phoenix   20   0 27768 7096 5692 S  0.0  0.7   0:00.16 gnome-session                                                                                              
 1688 phoenix   20   0  3640  684  436 S  0.0  0.1   0:00.00 ssh-agent                                                                                                  
 1691 phoenix   20   0  3636  880  596 S  0.0  0.1   0:00.00 dbus-launch                                                                                                
 1692 phoenix   20   0  3444 1568  744 S  0.0  0.2   0:00.25 dbus-daemon                                                                                                
 1695 phoenix   20   0  9544 4784 2464 S  0.0  0.5   0:00.49 gconfd-2                                                                                                   
 1702 phoenix   20   0 91500 9660 7140 S  0.0  0.9   0:00.86 gnome-settings-                                                                                            
 1704 phoenix   20   0  7812 2448 2072 S  0.0  0.2   0:00.02 gvfsd                                                                                                      
 1711 phoenix   20   0 30460 2556 2020 S  0.0  0.2   0:00.00 gvfs-fuse-daemo                                                                                            
 1716 phoenix    9 -11 95932 4468 3196 S  0.0  0.4   0:00.65 pulseaudio                                                                                                 
 1723 phoenix   20   0 23512  10m 8004 S  0.0  1.1   0:00.39 esets_gui                                                                                                  
 1724 phoenix   20   0  250m  16m  11m S  0.0  1.6   0:05.06 gnome-panel                                                                                                
 1726 phoenix   20   0  184m  10m 8108 S  0.0  1.0   0:00.19 nm-applet                                                                                                  
 1727 phoenix   20   0  301m  18m  13m S  0.0  1.9   0:00.96 nautilus                                                                                                   
 1730 phoenix   20   0 20292 6348 5136 S  0.0  0.6   0:00.02 polkit-gnome-au                                                                                            
 1750 phoenix   20   0  8268 3036 2544 S  0.0  0.3   0:00.01 gvfsd-trash                                                                                                
 1754 phoenix   20   0 42232 3628 2836 S  0.0  0.4   0:00.08 gvfs-gdu-volume                                                                                            
 1762 phoenix   20   0     0    0    0 Z  0.0  0.0   0:00.03 exe <defunct>                                                                                              
 1765 phoenix   20   0 18304 2500 2084 S  0.0  0.2   0:00.04 gvfs-afc-volume                                                                                            
 1768 phoenix   20   0  8472 2452 2024 S  0.0  0.2   0:00.01 gvfs-gphoto2-vo                                                                                            
 1769 phoenix   20   0 11008 3096 2492 S  0.0  0.3   0:00.01 gconf-helper                                                                                               
 1777 phoenix   20   0 42428 3724 2864 S  0.0  0.4   0:00.08 bonobo-activati                                                                                            
 1784 phoenix   20   0  8304 2952 2504 S  0.0  0.3   0:00.01 gvfsd-computer                                                                                             
 1802 phoenix   20   0 25644 9852 8036 S  0.0  1.0   0:01.27 multiload-apple                                                                                            
 1803 phoenix   20   0  167m  10m 8380 S  0.0  1.1   0:00.17 drivemount_appl                                                                                            
phoenix@phoenix-desktop:~$ ps -o 1762,comm | grep exe
ERROR: Unknown user-defined format specifier "1762".

---

### Post by Karlchen on 2011-05-12
Hello, mrphoenix.

you have to type the commandline exactly as it was posted ```
ps -o ppid,comm | grep exe
``` You must not substitute **ppid** by a process ID, **ppid** is part of the formatting string which is part of the **-o** option.

Karl

---

### Post by mrphoenix on 2011-05-12
> **Karlchen said:**
> Hello, mrphoenix.

you have to type the commandline exactly as it was posted ```
ps -o ppid,comm | grep exe
``` You must not substitute **ppid** by a process ID, **ppid** is part of the formatting string which is part of the **-o** option.

Karl

Thanks for helping again...

I just writed that command in Terminal because in the format which you mentioned too I didn't get any output answer. When I run the command ps -o ppid,comm | grep exe after I don't get any output, and nothing happened.

---

### Post by Vaphell on 2011-05-12
try ps -**A**o ...

---

### Post by mrphoenix on 2011-05-12
> **Vaphell said:**
> try ps -**A**o ...

phoenix@phoenix-desktop:~$ ps -Ao ppid,comm | grep exe
 1792 exe <defunct>
    1 services.exe
 2811 winedevice.exe
    1 explorer.exe
 2811 plugplay.exe
    1 Uncom.exe

---

### Post by jerome1232 on 2011-05-12
Limited experince here with this particular subject but that's definitly wine running something (possibly just called exe? Or uncom.exe) When I start something up in wine I get a very similiar process list to yours. (exposing my addiction here but that's ok)

The first is with winecfg open and you can guess the second.

```
jeremy@Farewell:~$ ps -Ao ppid,comm | grep exe
 3267 winecfg.exe
    1 services.exe
 3352 winedevice.exe
    1 explorer.exe
jeremy@Farewell:~$ ps -Ao ppid,comm | grep exe
    1 Wow.exe
    1 services.exe
 3994 winedevice.exe
    1 explorer.exe
```

---

