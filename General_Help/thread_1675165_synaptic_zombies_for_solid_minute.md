---
title: "synaptic zombies for solid minute"
date: 2011-01-25
forum: General Help
---

### Post by ToFue on 2011-01-25
Happens whenever I pass a parameter or command through synaptic package manager- window grows gray & lasts for a complete minute before resolving. Occurs immediately after checking a package's box or after typing a single character in the search field.. really annoying & only started happening after the last synaptic update. i'm using 10.10.  On a side note, it seems that 10.10 is riddled with more noticeable annoyance bugs than other version releases seemed to be... at least for the features i tend to use.

---

### Post by ToFue on 2011-01-31
<Bump>

Am I the only one that synaptic is doing this for??  I've got two machines, a laptop & desktop that this minute-long lag problem is a plague for. Can't be just a bad image: one machine's Mythbuntu, the other Ubuntu desktop. Could it be my network, in which ALL my ports are open on the gateway?  This really is becoming a crippling issue and happens with Every checkbox/search input under Synaptic...   apt-get works fine, but I use Synaptic for searching alternatives and stuff.... 

Thanks for any help available! ):P

---

### Post by Krytarik on 2011-02-01
Honestly I haven't heard of such a behaviour of Synaptic until now.

My first step would be to check "~/.xseesion-errors" for related error messages.

---

### Post by ToFue on 2011-02-24
oh wow, Thanks for the reply- here's my stuff in ~/.xsession-errors

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-nHjdRS
SSH_AUTH_SOCK=/tmp/keyring-nHjdRS/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-nHjdRS
SSH_AUTH_SOCK=/tmp/keyring-nHjdRS/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-nHjdRS
SSH_AUTH_SOCK=/tmp/keyring-nHjdRS/ssh

(polkit-gnome-authentication-agent-1:28983): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:28983): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area

** (nm-applet:28989): WARNING **: Invalid connection /system/networking/connections/3: 'NMSettingConnection' / 'id' invalid: 2

** (gnome-settings-daemon:28967): WARNING **: Got less number of items in credentials hash table than expected!
Initializing nautilus-gdu extension
** (nm-applet:28989): DEBUG: foo_client_state_changed_cb
Starting gtk-window-decorator

(nautilus:28986): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: applet now embedded in the notification area
** (nm-applet:28989): DEBUG: foo_client_state_changed_cb
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I/O warning : failed to load external entity "/home/tofue/.compiz/session/1030f4a34439501400129843137893213800000289070026"
** (update-notifier:29290): DEBUG: aptdaemon on bus: 0
** (update-notifier:29290): DEBUG: Skipping reboot required
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

(gnome-terminal:29208): Vte-0.0-WARNING **: Attempt to set invalid NRC map '\u000f'.

(nautilus:28986): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

** (totem-video-thumbnailer:27820): WARNING **: Could not take screenshot: no last video frame

** (totem-video-thumbnailer:27820): WARNING **: Could not take screenshot: no last video frame

** (totem-video-thumbnailer:27820): WARNING **: Could not take screenshot: no last video frame

** (totem-video-thumbnailer:27820): WARNING **: Could not take screenshot: no last video frame

** (totem-video-thumbnailer:27820): WARNING **: Could not take screenshot: no last video frame
totem-video-thumbnailer couldn't get a picture from 'trash:///House.S07E12.720p.HDTV.X264-DIMENSION.mkv'
2011-02-22 23:46:13,281 - softwarecenter.app - INFO - software-center-agent finished with status 1

(nautilus:28986): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:28986): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(evolution-alarm-notify:28982): evolution-alarm-notify-WARNING **: alarm.c:253: Requested removal of nonexistent alarm!
Another synaptic is running. Trying to bring it to the foreground

(nautilus:28986): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:28986): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:28986): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:28986): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:28986): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
/tmp/tmp.WnV5C6voLF: incorrect total size of bitmap (22009 specified; 9640 real)
/tmp/tmp.WnV5C6voLF: skipping 12369 bytes of garbage at 19838
/tmp/tmp.WnV5C6voLF: premature end

(nautilus:28986): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
### My note: the above error occurs 24 more times ###

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

(nautilus:28986): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
### My note: the above error occurs 33 more times ###

(gedit:28509): Gtk-CRITICAL **: IA__gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed

(nautilus:28986): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
### My note: the above error occurs 13,554 more times ###

** (gnome-system-monitor:23171): WARNING **: SELinux was found but is not enabled.

Initializing nautilus-gdu extension

(nautilus:23174): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

(nautilus:23174): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
### My Note: The above error occurs 1,614 times ###

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:23174): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
### My Note: The above error occurs 438 times ###

(nautilus:23174): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Discarding: 1 over 2

(nautilus:23174): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
### My Note: The Following occurs 824 times with several 'Discarding: # over # times' ###

(process:23215): Gtk-CRITICAL **: set_table: assertion `buffer->tag_table == NULL' failed

(nautilus:23174): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
### My Note: The above error occurs 6,766 times ###

(evolution-alarm-notify:28982): evolution-alarm-notify-WARNING **: alarm.c:253: Requested removal of nonexistent alarm!

(nautilus:23174): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

### My Note: The above error occurs 6,377 times ###

Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

(nautilus:23174): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
### My Note: The above error occurs 9,441 times ###

(process:16737): Gtk-CRITICAL **: set_table: assertion `buffer->tag_table == NULL' failed

(nautilus:23174): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
### My Note: The above error occurs 2,314 times ###

** (gnome-system-monitor:16376): WARNING **: SELinux was found but is not enabled.

(nautilus:23174): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
### My Note: The above error occurs 42 times ###


```



I could be reading it wrong, but it appears that gconf &or nautilus has a really bad bug..  should I report via launchpad? 

Also, there's an entry for synaptic, where it attempted a duplicate instance.. could have been me that time.. dunno. My issue with Synaptic gray-ing out seems to be consistent to quires that seem.. at a distance from what's loaded?

EDIT: System monitor doesn't show much of anything except that nautilus increases cpu from %4 to %8 when synaptic grays..

---

### Post by ToFue on 2011-02-24
Progress: when I open sudo synaptic from bash, the zombieness isn't there at all- but when using the link from System>Administration>Synaptic Package Manager,  I get this debilitating issue.

---

### Post by Krytarik on 2011-02-24
First, I don't see any serious error messages in your log, those regarding Nautilus are common and minor, and I also get them, only when running it as root I guess.

Second, you should never use "sudo" to run graphical apps as root, use "gksudo" instead:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Regarding the issue, could it be theme related? Try one of the default installed ones, e.g. Ambiance.

---

### Post by ToFue on 2011-02-24
Thanks for the gksudo reminder :p 

'gksudo synaptic' doesn't seem to gray as often, but still happens. 
as mentioned on other post, 'sudo synaptic' doesn't gray-out at all..

It has also just occurred with nautilus while I invoked <ctrl+f>, as well as when searching through yelp...

I was also looking in the wrong tab in system monitor- cpu maxes out during the entire gray-out durations for all of these programs, but different duration. so could it be something with a gdk or gnome search function? 

also, is there an app that I can tee with to capture the output when this happens?

Thanks for your patience! :)

EDIT: Ambience is my default theme

---

### Post by Krytarik on 2011-02-24
> **ToFue said:**
> 
also, is there an app that I can tee with to capture the output when this happens?

You can run Synaptic or the others from the terminal to see otherwise hidden outputs.

---

### Post by ToFue on 2011-02-24
Also, attatched are screenshots: 

screenshot1.png shows synaptic behavior;

screenshot2.png shows nautilus behavior;
"this" refers to the grayed app, the arrow on the left of cpu meter is the 'normal' cpu load, the other arrow is for sustained peak... also note the duration of cpu max


EDIT: I posted as you posted :p
The gksudo launches that grayed out was from using <Ctrl+F2>

I get no output no output in terminal excecpt for those other warnings mentioned before...  which is why I was asking about a program that would forcefully spit it out in a piped tee ;)

---

### Post by tgalati4 on 2011-02-24
Post the output of:

free

df -h

It could be you are shy on RAM or hard disk space.  Synaptic is a front end for the apt system that checks for dependencies and it takes a while.  You can search the forum for a way to optimize the database cache--by rewriting it so it is quicker to check and frees up synaptic.  I don't have that link handy.

---

### Post by Krytarik on 2011-02-24
The screenshots indicate an error in the handling of your 2 CPUs (2 cores?), at least in my view. You can see that the usage of both CPUs are oscilliating against each other, whereas I would expect an equal high or low usage, or -for energy saving purposes- one high while the other suspends.

---

### Post by ToFue on 2011-02-24
```
tofue@Ectonut:/usr$ free
             total       used       free     shared    buffers     cached
Mem:       3086136    2817524     268612          0      84872    1779012
-/+ buffers/cache:     953640    2132496
Swap:       976556      50804     925752

```
..and..
```

tofue@Ectonut:/usr$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              97G  6.1G   86G   7% /
none                  1.5G  260K  1.5G   1% /dev
none                  1.5G  1.9M  1.5G   1% /dev/shm
none                  1.5G  264K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
/dev/sda2             471M   53M  393M  12% /boot
/dev/sda8             3.0G  1.1G  1.8G  37% /var
/dev/sda6             164G   72G   84G  46% /home

```

EDIT: It's possible that free may have cleared it up! Thanks!  So, would that mean it was a dirty buffer or pointer?

---

### Post by ToFue on 2011-02-24
Oh this is great, guys! Thanks! 
I've been 'free'ed! hehehe

I'll search the forum for apt cache optimization and info apt per recommendation

 the 180 phase is a bit odd, but I always passed it off as some optimization for not 'burning' out a core.. core duo (processor: 0 is identical):
```

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping	: 8
cpu MHz		: 1833.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm dts
bogomips	: 3657.55
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:

``` What could I do to make it more efficient, short of recompiling kernel & possibly binutils, gcc, glibc, etc... unless that's what i gotta do?

---

### Post by Krytarik on 2011-02-24
Although I don't really get how you apparently fixed it, what about the Nautilus search issue and the difference in the behaviour wether you use gksudo/sudo or the menu to run Synaptic?

---

### Post by ToFue on 2011-02-25
they both work as normal now, with & without gksudo- snappy searches. I do a lot of hibernation & don't have swap as large as ram, so I'd suspect that that is where bad buffers & allocations came from.. the problem cleared up after i ran "$ free".. according to info, its a library function that clears buffers & memory, basically garbage collection, that also can invoke from bash.

 I'd assume that the search function in gnome/ubuntu-desktop was sloshing through the muck that must have been living in swap, and somehow recalled at every boot.   The symptoms of the problem (synaptic graying out) first reared after an update restart, but it makes sense that the update was just the catalyst if the new information thought the mucky old info was actually good when a pointer called it, which makes sense why tgalati4 suggested out of memory, and presented the command, "free".  I more suspect swap because of the time it took for the search function to resolve good info from the corrupted, thus increasing cpu to crunch out the errors. *what* corrupting memory/swap info that was exactly, I have no idea..

Do you have any ideas on the cpu phasing?

Thanks a Heap! (pun intended) :guitar:

---

### Post by Krytarik on 2011-02-25
> **ToFue said:**
> 
Do you have any ideas on the cpu phasing?

No, since I'm really not into the multicore/cpu tweaking thing.

I wouldn't be surprised if the issue re-occurs in the near future, unless you only hibernated all along the 3 weeks since your initial post, and the corrupted cache therefore stayed in memory.

---

### Post by ToFue on 2011-02-25
I'm an idiot...  I assumed too much, too quick, juggling too many things at once - it's not cleared up.. the searches got snappy, but I forgot completely about when checkboxing packages- the grayout still occurs. my assumptions in my last post are totally erroneous- though the lib function of 'free' does free up what malloc assigns (according to '$ info free' ), the bash 'free' seems to only *monitor* memory (according to '$ free --help')

 I'm almost back at square one. altering the state of packages' checkbox makes the minute-long grayout happen every time. searching, only sometimes. The nautilus thing seems more like a fluke, where maybe it was that I had about thirty files open in gedit with the folder expanded in nautilus, searching from root... i dunno...  

 I'm gonna leave this alone for a while.

g'night

---

### Post by Krytarik on 2011-02-25
Good morning! I turned back to your initial post: You said the issue started after doing an update. Are you able to track what packages have been updated at that time? The logs are stored in "/var/log/apt".

---

