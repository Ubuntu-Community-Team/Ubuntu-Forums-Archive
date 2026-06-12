---
title: "synaptic &amp; software sources shuts down computer"
date: 2011-04-25
forum: General Help
---

### Post by doogiekd on 2011-04-25
hi friends, 

today i started getting this on my laptop:

when starting synaptic package manager or software sources from system administration, neither app do launches and the computer shuts down.

i have been using ubuntu on this toshiba laptop for about three years now.

any suggestions?

thanks, 

k.

---

### Post by KegHead on 2011-04-25
Hi!

This is interesting!

Can you update via terminal?

sudo apt-get update

sudo apt-get upgrade -f

Advise

KegHead

---

### Post by doogiekd on 2011-04-25
hi, 

i tried your suggestion:

sudo apt-get update

sudo apt-get upgrade -f

my laptop still shuts down when selecting synaptic package manager from the menu.

synaptic appears briefly, but before it loads the menu items, the laptop shuts down.

very strange, i've been running ubuntu on this laptop for several years and its worked perfectly. no other performance issues are noted.

k.

---

### Post by KegHead on 2011-04-25
Hi!

Were you able to upgrade via the terminal?

Are you using a mouse or pad?

KegHead

---

### Post by doogiekd on 2011-04-25
yes, 

sudo apt-get update

sudo apt-get upgrade -f

worked, but it did not solve the problem.

using a usb mouse attached with the laptop's mouse pad disabled.

---

### Post by KegHead on 2011-04-25
Hi!

I wonder if you have a short in your mouse cable or at it's connection at the mobo.

Any chance you could try another mouse?

KegHead

---

### Post by doogiekd on 2011-04-25
the mouse is wireless usb.

i did unplug the wireless usb mouse and enabled the onboard mouse pad and rebooted.

still, the laptop shuts down seconds after selecting synaptic from the administration menu.

---

### Post by KegHead on 2011-04-25
Hi!

Could you enable the mouse pad and advise?

Thanks! [COLOR="Red"](is your kernel up to date?)[/COLOR]

KegHead

---

### Post by matt_symes on 2011-04-25
Hi

That is very odd. I'm very intreged. 

Not trying to hijack the thread, but do you get any messages when you type synaptic or software-center in the terminal ?

Kind regards

---

### Post by KegHead on 2011-04-25
Hi!

It sounds like it's a kernel problem.

try in terminal;

sudo apt-get update

sudo apt-get install linux-image

Restart

Advise.

KegHead

---

### Post by doogiekd on 2011-04-25
with the onboard mousepad enabled, the problem still continues.

kernel version: 2.6.35-28-generic

no messages are seen when starting synaptic  - except for "starting without administrative privlages" message when starting synaptic from termianl.

synaptic does not shut down the laptop when starting as a regular user. it does shut down the laptop when gksudo synaptic is used.

---

### Post by matt_symes on 2011-04-25
Hi

Try Keghead's advice. Also can you boot to an older kernel and does it still happen ?

Kind regards

---

### Post by KegHead on 2011-04-25
jim@jim:~$ sudo apt-get update
[sudo] password for jim: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197 B]                          
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,097 B]                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg [198 B]                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release [39.8 kB]                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources [862 kB]                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources [4,104 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources [4,381 kB]           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources [155 kB]          
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages [1,550 kB]        
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages [8,986 B]   
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages [6,023 kB]    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages [183 kB]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 13.2 MB in 17s (735 kB/s)                                              
Reading package lists... Done
jim@jim:~$ sudo apt-get install linux-image -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
jim@jim:~$

---

### Post by doogiekd on 2011-04-25
hi. tried:

sudo apt-get update

sudo apt-get install linux-image

rebooted - and the problem continues.

also note that the hard drive is only 40% used so i'm sure its not a  hdd problem.

---

### Post by KegHead on 2011-04-25
Hi!

It could be a hardware issue.

Do a google search by your model number.

There may be a wire loose between your mobo and screen.

Signing off for the night.

KegHead

---

### Post by KegHead on 2011-04-25
oops!

I forgot:

If you have a Dell, there is chatter over the net that there is a bios update.

Good Night!

KegHead

---

### Post by doogiekd on 2011-04-26
well, 

i searched as suggested above. the bios for this toshiba laptop is the current version.

i think you are right though that this is a kernel problem.

is there a way to completdely remove the kernel and then reinstall it in terminal?

---

### Post by KegHead on 2011-04-26
Hi!

The only safe way I know is post # 13.

I have experimented with newer kernels, but I faced other problems.

Best to be safe with post #13.

The only other thing I can think of is a lose wire/short between the mobo and screen.

KegHead

---

### Post by doogiekd on 2011-04-26
its so strange, the laptop works fine - i can surf, openoffice, gimp, ect... except it shuts down when i start synaptic.

maybe it was a bad update or something.

---

### Post by pqwoerituytrueiwoq on 2011-04-26
to install updates
[FONT=Courier New]sudo apt-get upgrade[/FONT]
if you just want the kernel update
[FONT=Courier New]sudo apt-get install linux-headers-2.6.32-31 linux-headers-2.6.32-31-generic linux-image-2.6.32-31[/FONT]

does the screen go blank and everything power off or does it go though the normal shutdown process (just wondering)

---

### Post by doogiekd on 2011-04-26
it goes thru the normal shutdown process.

i'm at a loss - so i made waffles.

---

### Post by matt_symes on 2011-04-26
Hi

> i'm at a loss - so i made waffles.

Waffles are good at a time like this :P

Have you checked your log files ? They might have some clue as to what is triggering this strange behaviour.

Kind regards

---

### Post by doogiekd on 2011-04-26
here is the last minute of the syslog file before i started synaptc and the laptop shut down:


Apr 26 18:17:00 mars init: plymouth-stop pre-start process (1386) terminated with status 1
Apr 26 18:17:00 mars gdm-session-worker[1393]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 26 18:17:00 mars rtkit-daemon[1401]: Successfully called chroot.
Apr 26 18:17:00 mars rtkit-daemon[1401]: Successfully dropped privileges.
Apr 26 18:17:00 mars rtkit-daemon[1401]: Successfully limited resources.
Apr 26 18:17:00 mars rtkit-daemon[1401]: Running.
Apr 26 18:17:00 mars rtkit-daemon[1401]: Watchdog thread running.
Apr 26 18:17:00 mars rtkit-daemon[1401]: Canary thread running.
Apr 26 18:17:00 mars polkitd[1407]: started daemon version 0.96 using authority implementation `local' version `0.96'
Apr 26 18:17:00 mars rtkit-daemon[1401]: Successfully made thread 1398 of process 1398 (n/a) owned by '112' high priority at nice level -11.
Apr 26 18:17:00 mars rtkit-daemon[1401]: Supervising 1 threads of 1 processes of 1 users.
Apr 26 18:17:00 mars rtkit-daemon[1401]: Successfully made thread 1424 of process 1398 (n/a) owned by '112' RT at priority 5.
Apr 26 18:17:00 mars rtkit-daemon[1401]: Supervising 2 threads of 1 processes of 1 users.
Apr 26 18:17:00 mars rtkit-daemon[1401]: Successfully made thread 1425 of process 1398 (n/a) owned by '112' RT at priority 5.
Apr 26 18:17:00 mars rtkit-daemon[1401]: Supervising 3 threads of 1 processes of 1 users.
Apr 26 18:17:00 mars anacron[1465]: Anacron 2.3 started on 2011-04-26
Apr 26 18:17:00 mars anacron[1465]: Normal exit (0 jobs run)
Apr 26 18:17:01 mars gdm-simple-greeter[1390]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Apr 26 18:17:01 mars CRON[1476]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 26 18:17:01 mars gdm-simple-greeter[1390]: WARNING: Unable to lookup user name administ: Success
Apr 26 18:17:01 mars kernel: [   23.681976] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 136.
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c: snd_pcm_dump():
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c: Soft volume PCM
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c: Control: PCM Playback Volume
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c: min_dB: -51
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c: max_dB: 0
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c: resolution: 256
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c: Its setup is:
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   stream       : CAPTURE
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   access       : MMAP_INTERLEAVED
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   format       : S16_LE
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   subformat    : STD
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   channels     : 2
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   rate         : 44100
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   exact rate   : 44100 (44100/1)
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   msbits       : 16
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   buffer_size  : 88192
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   period_size  : 44096
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   period_time  : 999909
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   tstamp_mode  : ENABLE
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   period_step  : 1
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   avail_min    : 87310
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   period_event : 0
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   start_threshold  : -1
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   stop_threshold   : 1444937728
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   silence_threshold: 0
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   silence_size : 0
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   boundary     : 1444937728
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c: Its setup is:
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   stream       : CAPTURE
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   access       : MMAP_INTERLEAVED
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   format       : S16_LE
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   subformat    : STD
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   channels     : 2
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   rate         : 44100
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   exact rate   : 44100 (44100/1)
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   msbits       : 16
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   buffer_size  : 88192
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   period_size  : 44096
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   period_time  : 999909
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   tstamp_mode  : ENABLE
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   period_step  : 1
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   avail_min    : 87310
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   period_event : 0
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   start_threshold  : -1
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   stop_threshold   : 1444937728
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   silence_threshold: 0
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   silence_size : 0
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   boundary     : 1444937728
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   appl_ptr     : 87448
Apr 26 18:17:02 mars pulseaudio[1398]: alsa-util.c:   hw_ptr       : 87448
Apr 26 18:17:06 mars gdm-session-worker[1393]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 26 18:17:10 mars NetworkManager[999]: <error> [1303867030.645213] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Apr 26 18:17:10 mars NetworkManager[999]: <error> [1303867030.669710] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Apr 26 18:17:11 mars kernel: [   33.433143] Skipping EDID probe due to cached edid
Apr 26 18:17:11 mars kernel: [   33.453064] Skipping EDID probe due to cached edid
Apr 26 18:17:11 mars kernel: [   33.473057] Skipping EDID probe due to cached edid
Apr 26 18:17:11 mars kernel: [   33.489135] Skipping EDID probe due to cached edid
Apr 26 18:17:11 mars rtkit-daemon[1401]: Successfully made thread 1632 of process 1632 (n/a) owned by '1000' high priority at nice level -11.
Apr 26 18:17:11 mars rtkit-daemon[1401]: Supervising 4 threads of 2 processes of 2 users.
Apr 26 18:17:11 mars gnome-session[1553]: WARNING: Could not launch application 'hplip-systray.desktop': Unable to start application: Failed to execute child process "hp-systray" (No such file or directory)
Apr 26 18:17:11 mars rtkit-daemon[1401]: Successfully made thread 1644 of process 1632 (n/a) owned by '1000' RT at priority 5.
Apr 26 18:17:11 mars rtkit-daemon[1401]: Supervising 5 threads of 2 processes of 2 users.
Apr 26 18:17:11 mars rtkit-daemon[1401]: Successfully made thread 1655 of process 1632 (n/a) owned by '1000' RT at priority 5.
Apr 26 18:17:11 mars rtkit-daemon[1401]: Supervising 6 threads of 2 processes of 2 users.
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0) starting connection 'Auto melvin'
Apr 26 18:17:12 mars NetworkManager[999]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 26 18:17:12 mars NetworkManager[999]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0/wireless): access point 'Auto melvin' has security, but secrets are required.
Apr 26 18:17:12 mars NetworkManager[999]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 26 18:17:12 mars rtkit-daemon[1401]: Successfully made thread 1676 of process 1676 (n/a) owned by '1000' high priority at nice level -11.
Apr 26 18:17:12 mars rtkit-daemon[1401]: Supervising 7 threads of 3 processes of 2 users.
Apr 26 18:17:12 mars pulseaudio[1676]: pid.c: Daemon already running.
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 26 18:17:12 mars NetworkManager[999]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 26 18:17:12 mars NetworkManager[999]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0/wireless): connection 'Auto melvin' has security, and secrets exist.  No new secrets needed.
Apr 26 18:17:12 mars NetworkManager[999]: <info> Config: added 'ssid' value 'melvin'
Apr 26 18:17:12 mars NetworkManager[999]: <info> Config: added 'scan_ssid' value '1'
Apr 26 18:17:12 mars NetworkManager[999]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 26 18:17:12 mars NetworkManager[999]: <info> Config: added 'psk' value '<omitted>'
Apr 26 18:17:12 mars NetworkManager[999]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 26 18:17:12 mars NetworkManager[999]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 26 18:17:12 mars NetworkManager[999]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 26 18:17:12 mars NetworkManager[999]: <info> Config: set interface ap_scan to 1
Apr 26 18:17:12 mars NetworkManager[999]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Apr 26 18:17:12 mars kernel: [   34.848067] Skipping EDID probe due to cached edid
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 8 is less than avail 136.
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c: snd_pcm_dump():
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c: Soft volume PCM
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c: Control: PCM Playback Volume
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c: min_dB: -51
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c: max_dB: 0
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c: resolution: 256
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c: Its setup is:
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   stream       : CAPTURE
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   access       : MMAP_INTERLEAVED
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   format       : S16_LE
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   subformat    : STD
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   channels     : 2
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   rate         : 44100
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   exact rate   : 44100 (44100/1)
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   msbits       : 16
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   buffer_size  : 88192
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   period_size  : 44096
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   period_time  : 999909
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   tstamp_mode  : ENABLE
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   period_step  : 1
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   avail_min    : 87310
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   period_event : 0
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   start_threshold  : -1
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   stop_threshold   : 1444937728
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   silence_threshold: 0
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   silence_size : 0
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   boundary     : 1444937728
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c: Its setup is:
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   stream       : CAPTURE
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   access       : MMAP_INTERLEAVED
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   format       : S16_LE
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   subformat    : STD
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   channels     : 2
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   rate         : 44100
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   exact rate   : 44100 (44100/1)
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   msbits       : 16
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   buffer_size  : 88192
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   period_size  : 44096
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   period_time  : 999909
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   tstamp_mode  : ENABLE
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   period_step  : 1
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   avail_min    : 87310
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   period_event : 0
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   start_threshold  : -1
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   stop_threshold   : 1444937728
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   silence_threshold: 0
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   silence_size : 0
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   boundary     : 1444937728
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   appl_ptr     : 87448
Apr 26 18:17:13 mars pulseaudio[1632]: alsa-util.c:   hw_ptr       : 87448
Apr 26 18:17:14 mars blueman-mechanism: Starting blueman-mechanism 
Apr 26 18:17:14 mars wpa_supplicant[1278]: Trying to associate with 00:1d:7e:65:2a:5b (SSID='melvin' freq=2447 MHz)
Apr 26 18:17:14 mars NetworkManager[999]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 26 18:17:14 mars kernel: [   36.542560] wlan0: authenticate with 00:1d:7e:65:2a:5b (try 1)
Apr 26 18:17:14 mars kernel: [   36.544392] wlan0: authenticated
Apr 26 18:17:14 mars kernel: [   36.544425] wlan0: associate with 00:1d:7e:65:2a:5b (try 1)
Apr 26 18:17:14 mars kernel: [   36.547525] wlan0: RX AssocResp from 00:1d:7e:65:2a:5b (capab=0x411 status=0 aid=1)
Apr 26 18:17:14 mars kernel: [   36.547530] wlan0: associated
Apr 26 18:17:14 mars blueman-mechanism: reload 0 0 
Apr 26 18:17:14 mars wpa_supplicant[1278]: Associated with 00:1d:7e:65:2a:5b
Apr 26 18:17:14 mars kernel: [   36.576464] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 26 18:17:14 mars NetworkManager[999]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr 26 18:17:14 mars NetworkManager[999]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr 26 18:17:14 mars NetworkManager[999]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr 26 18:17:14 mars wpa_supplicant[1278]: WPA: Key negotiation completed with 00:1d:7e:65:2a:5b [PTK=TKIP GTK=TKIP]
Apr 26 18:17:14 mars wpa_supplicant[1278]: CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:65:2a:5b completed (auth) [id=0 id_str=]
Apr 26 18:17:14 mars NetworkManager[999]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Apr 26 18:17:14 mars NetworkManager[999]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'melvin'.
Apr 26 18:17:14 mars NetworkManager[999]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 26 18:17:14 mars NetworkManager[999]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 26 18:17:14 mars NetworkManager[999]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Apr 26 18:17:14 mars NetworkManager[999]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 26 18:17:14 mars NetworkManager[999]: <info> dhclient started with pid 1795
Apr 26 18:17:14 mars NetworkManager[999]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 26 18:17:14 mars dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 26 18:17:14 mars dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 26 18:17:14 mars dhclient: All rights reserved.
Apr 26 18:17:14 mars dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 26 18:17:14 mars dhclient: 
Apr 26 18:17:14 mars NetworkManager[999]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 26 18:17:14 mars dhclient: Listening on LPF/wlan0/00:13:e8:a1:35:61
Apr 26 18:17:14 mars dhclient: Sending on   LPF/wlan0/00:13:e8:a1:35:61
Apr 26 18:17:14 mars dhclient: Sending on   Socket/fallback
Apr 26 18:17:14 mars dhclient: DHCPREQUEST of 192.168.1.107 on wlan0 to 255.255.255.255 port 67
Apr 26 18:17:14 mars dhclient: DHCPACK of 192.168.1.107 from 192.168.1.1
Apr 26 18:17:14 mars NetworkManager[999]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr 26 18:17:14 mars NetworkManager[999]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 26 18:17:14 mars NetworkManager[999]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 26 18:17:14 mars NetworkManager[999]: <info>   address 192.168.1.107
Apr 26 18:17:14 mars NetworkManager[999]: <info>   prefix 24 (255.255.255.0)
Apr 26 18:17:14 mars NetworkManager[999]: <info>   gateway 192.168.1.1
Apr 26 18:17:14 mars NetworkManager[999]: <info>   hostname 'mars'
Apr 26 18:17:14 mars NetworkManager[999]: <info>   nameserver '68.87.69.150'
Apr 26 18:17:14 mars NetworkManager[999]: <info>   nameserver '68.87.85.102'
Apr 26 18:17:14 mars NetworkManager[999]: <info>   domain name 'hsd1.wa.comcast.net.'
Apr 26 18:17:14 mars NetworkManager[999]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 26 18:17:14 mars NetworkManager[999]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 26 18:17:14 mars NetworkManager[999]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Apr 26 18:17:14 mars avahi-daemon[958]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.107.
Apr 26 18:17:14 mars avahi-daemon[958]: New relevant interface wlan0.IPv4 for mDNS.
Apr 26 18:17:14 mars avahi-daemon[958]: Registering new address record for 192.168.1.107 on wlan0.IPv4.
Apr 26 18:17:14 mars dhclient: bound to 192.168.1.107 -- renewal in 34620 seconds.
Apr 26 18:17:15 mars NetworkManager[999]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Apr 26 18:17:15 mars NetworkManager[999]: <info> Policy set 'Auto melvin' (wlan0) as default for IPv4 routing and DNS.
Apr 26 18:17:15 mars NetworkManager[999]: <info> Activation (wlan0) successful, device activated.
Apr 26 18:17:15 mars NetworkManager[999]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 26 18:17:15 mars avahi-daemon[958]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::213:e8ff:fea1:3561.
Apr 26 18:17:15 mars avahi-daemon[958]: New relevant interface wlan0.IPv6 for mDNS.
Apr 26 18:17:15 mars avahi-daemon[958]: Registering new address record for fe80::213:e8ff:fea1:3561 on wlan0.*.
Apr 26 18:17:16 mars kernel: [   38.973058] Skipping EDID probe due to cached edid
Apr 26 18:17:16 mars kernel: [   38.997069] Skipping EDID probe due to cached edid
Apr 26 18:17:17 mars ntpdate[1878]: adjust time server 91.189.94.4 offset 0.163604 sec
Apr 26 18:17:24 mars kernel: [   47.048044] wlan0: no IPv6 routers present
Apr 26 18:17:26 mars gnome-session[1553]: WARNING: Could not launch application 'gnome-user-share.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-user-share/gnome-user-share" (No such file or directory)
Apr 26 18:17:44 mars blueman-mechanism: Exiting

---

### Post by doogiekd on 2011-04-26
and the auth.log:

pr 26 18:16:10 mars sudo: administrator : TTY=unknown ; PWD=/home/administrator ; USER=root ; COMMAND=/usr/sbin/synaptic
Apr 26 18:16:12 mars sudo: administrator : TTY=unknown ; PWD=/ ; USER=root ; COMMAND=/sbin/shutdown -h now
Apr 26 18:17:01 mars CRON[1473]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 26 18:17:01 mars CRON[1473]: pam_unix(cron:session): session closed for user root
Apr 26 18:17:06 mars gdm-session-worker[1393]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "administrator"
Apr 26 18:17:10 mars gdm-session-worker[1393]: pam_unix(gdm:session): session opened for user administrator by (uid=0)
Apr 26 18:17:10 mars gdm-session-worker[1393]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 26 18:17:11 mars dbus-daemon: [system] Rejected send message, 1 matched rules; type="method_return", sender=":1.9" (uid=0 pid=1143 comm="/usr/sbin/bluetoothd) interface="(unset)" member="(unset)" error name="(unset)" requested_reply=0 destination=":1.28" (uid=1000 pid=1622 comm="bluetooth-applet))
Apr 26 18:17:11 mars polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.29 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8)
Apr 26 18:17:13 mars dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.36" (uid=1000 pid=1620 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=1004 comm="/usr/sbin/console-kit-daemon))
Apr 26 18:17:15 mars sudo: administrator : no tty present and no askpass program specified ; TTY=unknown ; PWD=/ ; USER=root ; COMMAND=/sbin/shutdown -h now
Apr 26 18:17:50 mars sudo: last message repeated 7 times

---

### Post by matt_symes on 2011-04-26
Hi

> Apr 26 18:17:13 mars dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.36" (uid=1000 pid=1620 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=1004 comm="/usr/sbin/console-kit-daemon))
Apr 26 18:17:15 mars sudo: administrator : no tty present and no askpass program specified ; TTY=unknown ; PWD=/ ; USER=root ; COMMAND=**/sbin/shutdown -h now**
Apr 26 18:17:50 mars sudo: **last message repeated 7 times**

That looks like your problem, i would say. 

Just need to figure out where it's coming from. 

Not tonight though. I'm off to bed. 

Bump this thread and if no-one jumps in tonight we can do some head scratching tomorrow and it i will be able to find the thread easily.

Kin regards

---

### Post by pqwoerituytrueiwoq on 2011-04-27
have you tried installing update from recovery mode or a older kernel?
[FONT=Courier New]sudo apt-get update; sudo apt-get upgrade[/FONT]
(if you are in root terminal/console)
[FONT=Courier New]apt-get update; apt-get upgrade[/FONT]

---

### Post by doogiekd on 2011-04-27
hi. i tried installing update from an older kernel AND the recovery mode.

the problem continues with the same error log messages as above.

maybe this will auto-fix tomorrow when 11.04 is installed...

---

