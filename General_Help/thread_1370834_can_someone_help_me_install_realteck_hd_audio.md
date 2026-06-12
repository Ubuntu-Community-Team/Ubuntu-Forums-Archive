---
title: "can someone help me install realteck hd audio"
date: 2010-01-02
forum: General Help
---

### Post by Vanorge on 2010-01-02
hi I am very new to linux . 
i have exhausted all other measures in order to try and figure out how to install programs. i have managed to install my graffix card since yesterday..LOL. thats about it. if someone could write out step by step how to install this driver that would be great. 

the file im trying to install is : realtek-linux-audiopack-5.13 ive gotten as far as extract here. i then double click and can see an install file/folder (shell script (application/x-shellscript) when i double click it i get an option to run in terminal or display or cancel or run. i run in terminal. terminal starts going and at the bottom says done but no restart and i have no idea where or if it's installed. i have tested also by going to sites with sounds and nothing. any help would be appreciated.

maaaaaaan linux is very hard. anyways tx.

---

### Post by 3rdalbum on 2010-01-02
Usually you don't need to install drivers for audio. Humour me - go to the terminal and type 'alsamixer', and make sure that the 'pcm', 'master' and 'front' channels are turned up almost to full.

Linux isn't hard, it's just you're not used to it and you're trying to use it like it was Windows.

---

### Post by Vanorge on 2010-01-02
vanorge@Ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
vanorge@Ubuntu:~$


i think im just going to have to read a book on linux or take a class. ive been googeling and asking in different forums how to do that simplest ****... and nothing is getting done. oh well. back to windows. honestly linux has been nothing but frustration.
p.s. im not here to humor you *******

---

### Post by 3rdalbum on 2010-01-02
No, you are here to get help for a problem. Sometimes the default state of Ubuntu sets the sound channels to mute, which is what I wanted to check on before I started dealing with installing drivers.

Most computers can run Ubuntu out-of-the-box, and I strongly advise running Ubuntu on compatible hardware rather than install a bunch of drivers to get it going.

If you still want help with this, then PM me. I'm no expert on sound problems though - I've never had them on my computers.

---

### Post by Leppie on 2010-01-02
i have a realtek hd card as well and am using the kernel modules.

what is the output of the command "lsmod" (without the quotes)?

Edit: did you modify your account to allow for use of your audio card? Go to System>Administration>Users and Groups, unlock the applet by clicking the key icon at the buttom of the applet and enter your password, click your account then click the properties button, go to User Privileges, make sure that the options "Use audio devices" and "Use video devices" are selected. As you are already there, just check all permissions listed ;)

---

### Post by Vanorge on 2010-01-02
vanorge@Ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
iptable_filter          3872  0 
snd_seq_dummy           3460  0 
snd_hda_codec          87584  0 
snd_seq_oss            33440  0 
ip_tables              21200  1 iptable_filter
snd_usb_audio         102976  1 
x_tables               25832  1 ip_tables
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_ctxfi              99016  0 
snd_seq_midi            8192  0 
usblp                  15136  0 
lp                     11908  0 
parport                40528  2 ppdev,lp
snd_pcm                93160  4 snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_ctxfi
snd_usb_lib            19648  1 snd_usb_audio
snd_hwdep               9352  2 snd_hda_codec,snd_usb_audio
snd_rawmidi            27360  2 snd_seq_midi,snd_usb_lib
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  14 snd_hda_codec,snd_seq_oss,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_ctxfi,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  1 snd_pcm
psmouse                57124  0 
serio_raw               6596  0 
fglrx                2234552  37 
usbhid                 43968  0 
ohci1394               33780  0 
usb_storage            65984  0 
r8169                  38884  0 
mii                     6368  1 r8169
ieee1394              100896  1 ohci1394
floppy                 65192  0 
intel_agp              32816  0 
vanorge@Ubuntu:~$

---

### Post by Leppie on 2010-01-02
> **Vanorge said:**
> vanorge@Ubuntu:~$ lsmod
Module                  Size  Used by
snd_hda_codec          87584  0 

this is the kernel realtek module, check your permissions ;)

---

### Post by Vanorge on 2010-01-02
im a grown man. who do i need to ask for permission? LOL

honestly though tx for the help but how in the hell do i do that? and what would be the next logical move. 

I've been building desktops for a little bit. i have some nice pc's here in my home. im not fed up with windows at all. but i heard that this linux was great, it doesn't seem realy user friendly though?

see i've asked questions and you know what brother im not going to get asnwers. im getting led to more questions lol


ls -l right?

if so this is what i get:

vanorge@Ubuntu:~$ ls -l
total 44
drwxr-xr-x 3 vanorge vanorge 4096 2010-01-02 13:13 Desktop
drwxr-xr-x 2 vanorge vanorge 4096 2010-01-02 03:08 Documents
drwxr-xr-x 2 vanorge vanorge 4096 2010-01-02 13:09 download
drwxr-xr-x 3 vanorge vanorge 4096 2010-01-02 15:05 Downloads
-rw-r--r-- 1 vanorge vanorge  167 2010-01-02 03:06 examples.desktop
drwxr-xr-x 2 vanorge vanorge 4096 2010-01-02 03:08 Music
drwxr-xr-x 3 vanorge vanorge 4096 2010-01-02 05:09 Pictures
drwxr-xr-x 2 vanorge vanorge 4096 2010-01-02 03:08 Public
drwxr-xr-x 2 vanorge vanorge 4096 2010-01-02 14:51 temp
drwxr-xr-x 2 vanorge vanorge 4096 2010-01-02 03:08 Templates
drwxr-xr-x 2 vanorge vanorge 4096 2010-01-02 03:08 Videos
vanorge@Ubuntu:~$


and did all of this : did you modify your account to allow for use of your audio card? Go to System>Administration>Users and Groups, unlock the applet by clicking the key icon at the buttom of the applet and enter your password, click your account then click the properties button, go to User Privileges, make sure that the options "Use audio devices" and "Use video devices" are selected. As you are already there, just check all permissions listed :wink:

what you suggested. and still no sound.

hey thanks for the trying im just going to give up. and for anyone thats new like me and is having issues with linux ,,, as you know just trying it out.. . RUUUUUUUUUUUUUUUUUUUUUUUUUUUN!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
windows is just way better. i mean come on now how hard can it be to install a driver!!!!!!!!!!!!!!!!!!!!!! do i have to take some computer science courses to install a driver?????????????? **** that

---

### Post by Leppie on 2010-01-02
I edited post #5, but here it is:
Go to System>Administration>Users and Groups, unlock the applet by clicking the key icon at the buttom of the applet and enter your password, click your account then click the properties button, go to User Privileges, make sure that the options "Use audio devices" and "Use video devices" are selected. As you are already there, just check all permissions listed

---

### Post by Leppie on 2010-01-02
> **Vanorge said:**
> what you suggested. and still no sound.

hey thanks for the try im just going to give up. and for anyone thats new like and is having issues with linux ,,, as you know just trying it out.. . RUUUUUUUUUUUUUUUUUUUUUUUUUUUN!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
windows is just way better. i mean come on now how hard can it be to install a driver!!!!!!!!!!!!!!!!!!!!!! do i have to take some computer science courses to install a driver?????????????? **** that
to be honest, i don't think windows is better. i've had so many issues with drivers, even for those so-called designed-for-windows products.

after setting the permissions, did you try to run alsa-mixer again? are you sure the mixer levels are not 0?

---

### Post by Vanorge on 2010-01-02
vanorge@Ubuntu:~$ also -mixer
No command 'also' found, did you mean:
 Command 'als' from package 'atool' (universe)
 Command 'aldo' from package 'aldo' (universe)
 Command 'alsa' from package 'alsa-base' (main)
also: command not found


vanorge@Ubuntu:~$ alsa-mixer
No command 'alsa-mixer' found, did you mean:
 Command 'alsamixer' from package 'alsa-utils' (main)
alsa-mixer: command not found
vanorge@Ubuntu:~$ 

yea see ive had no issues with drivers in windows .. and i can install them!!! thats a big plus.

my system is an
ip 35 pro
e8600 @ 4.5 water cooled
4870 x2
4gigs dominator
this system screams on XP, vista, and windows 7 which i havem all installed. have never had any issues with drivers. i have it connected to lcd 32 tv with z5500 logitech surround sound.  and man it's nice. thats just one of the two in my home office. this OS is weak. 

tx again tho im out

---

### Post by Leppie on 2010-01-02
the command is actually "alsamixer" (without the quotes)

---

### Post by 3rdalbum on 2010-01-02
We already tried alsamixer earlier on.

Venorge, there's any number of odd things that can go wrong with any operating system. Just like my problem with installing Paint.NET on Windows. Usually on Linux, you start up your computer and sound will Just Work. Windows is not easier, it's just that you ONLY know Windows. As for "how hard can it be to install a driver" - well, one of the posters earlier in the thread was saying that you already have a driver for your card - it was preinstalled with the system.

---

