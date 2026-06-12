---
title: "OSS4 sound problems"
date: 2009-08-20
forum: General Help
---

### Post by razorboy5 on 2009-08-20
Hi

my ubuntu was working fine for a long time until recently when for whatever reason my ubuntu crashed on bootup

i rebooted my machine however sound is no longer working

when i try to open it reads "No volume control GStreamer plugins and/or devices found."

and when i try to test the OSS4 sink it reads "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback."

so i'm trying to do this

sudo soundoff
sudo ossdetect -v
sudo soundon

however it's proving more difficult that imagined

[COLOR=RoyalBlue]daniel@Daniel-Gateway:~$ sudo soundoff
OSS not loaded.
daniel@Daniel-Gateway:~$ sudo ossdetect -v
Detected Intel High Definition Audio (ICH8)
USB support available in the system, adding USB driver
Detected Generic USB audio/MIDI device (BETA)
daniel@Daniel-Gateway:~$ sudo soundon
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.[/COLOR]

so assuming this means delete the file named starting from /usr/lib/oss i try to do so but i need permission so i start
[COLOR=RoyalBlue]daniel@Daniel-Gateway:~$ gksudo -u root nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6675): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root
--> file:///usr
--> file:///usr/lib
--> file:///
--> file:///usr/lib/oss

(nauti[/COLOR][COLOR=RoyalBlue]lus:6675): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 5 elements at quit time (keys above)

(nautilus:6675): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 5 elements at quit time[/COLOR]

then finally when i try soundon again it reads
[COLOR=RoyalBlue]
daniel@Daniel-Gateway:~$ sudo soundon
FATAL: Module osscore not found.
Loading the osscore module failed

[COLOR=Black]any ideas how to fix this problem?[/COLOR]
[/COLOR]

---

### Post by razorboy5 on 2009-08-20
[COLOR=RoyalBlue]daniel@Daniel-Gateway:~$ aplay -l
aplay: device_list:217: no soundcards found...[/COLOR]

[COLOR=Black]maybe this has to do with the update i installed today... cuz it's the first time i rebooted since i did the update this morning

[/COLOR]

---

