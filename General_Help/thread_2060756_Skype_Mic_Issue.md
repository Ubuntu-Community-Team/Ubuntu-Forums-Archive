---
title: "Skype Mic Issue"
date: 2012-09-20
forum: General Help
---

### Post by hardikbv on 2012-09-20
Dear Colleagues, 

I have issues with Skype since I installed Ubuntu (12.4) before few weeks. 

The Mic is not recognized.  It is perfectly recognized in my Win7 which I run on the same laptop.

I searched through the web and..
1) Downloaded the Pulse audio control, still it is did not work.
2) I deactivated pulse audit by some code mentioned on the skype forums (and eventually uninstalled) the pulse audio control and downloaded ALSA.  It is still not working. ALSA is not recognized in Skype settings. 

I have NVidia as default.  When I uninstalled the Pulse audit player, it showed numerous options of Nvidia though none of them are working :( Now I have re installed Pulse audit volumn controller.  

The speakers work perfect but the only problem is with mic.  Please help.

Thanks in advance.

Hardik

---

### Post by papibe on 2012-09-20
Hi hardikbv.

Does the mic work with a more basic program like 'Sound Recorder' for example?

Regards.

---

### Post by hardikbv on 2012-09-20
Hi Papibe,

How to check that? 

Hardik

---

### Post by papibe on 2012-09-20
Open 'Sound Recorder', record your voice, and then playback the file to see if it is working.

Let us know how it goes.
Regards.

---

### Post by hardikbv on 2012-09-20
Hello Papibe,

I tried doing it on 'Sound Recorder' but it is not working.  I am getting humming sound but my sound is getting recorded. 

Please Help.

Thanks. 

Hardik

---

### Post by hardikbv on 2012-09-20
Typo error above. 
 I am getting humming sound but my sound is NOT getting recorded.

---

### Post by papibe on 2012-09-20
Open a terminal and run:
```
alsamixer
```

There, make sure the mic is not muted and then try again to record your voice.

Regards.

---

### Post by hardikbv on 2012-09-21
I tried doing that you suggested.  I disabled the 'auto mute'.  The humming sound has changed but recording is still not happening.  

BTW : Now when I try to open Pulse Audio Manager I get 'Fatal Error...' now. 

Please help.

---

### Post by carranty on 2012-09-21
Open up sound preferences by clicking the speaker icon in the upper right corner of the screen, then click the input tab.  What do you see? There should be a Microphone option in the 'record sound from' box, can you alter the input volume, or is it ghosted out?

---

### Post by hardikbv on 2012-09-21
Dear Carranty,

The 'Record sound from' box is empty and 'The input volume' is ghosted out.  I am unable to make any changes in that.

---

### Post by carranty on 2012-09-21
> **hardikbv said:**
> Dear Carranty,

The 'Record sound from' box is empty and 'The input volume' is ghosted out.  I am unable to make any changes in that.

There's the problem.  In 10.04 you could fix this just by clicking on the 'hardware' tab and choosing the appropriate profile. However I can't find any such option in 12.04.....

I've attached a screenshot of the tab I'm talking about in 10.04. On my system my speakers worked but my mic didn't, it turned out I needed to select 'Analog Surround + Input' in my profile, previously the 'Analog Surround' profile (without the + input) had been selected. Does anyone  know how to get this option in 12.04?

---

### Post by carranty on 2012-09-21
OK, I've found how you can do the equivalent of the above from the command line.  First though I need you to type 

pactl list cards

into a terminal and print the results to this thread.  It may be quite long, I just need everything after the line starting with card #0.  This will tell us whether your sound card is being recognised as an output as well as input device, and list the available profiles. If the profile we are after is in the list, we should then be able to select it using the set-card-profile command.

---

### Post by hardikbv on 2012-09-21
Following comes Carranty :(

hardik@hardik-HP-Pavilion-tx1000-Notebook-PC:~$ pactl list cards 
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

---

### Post by carranty on 2012-09-21
> **hardikbv said:**
> Following comes Carranty :(

hardik@hardik-HP-Pavilion-tx1000-Notebook-PC:~$ pactl list cards 
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

I guess this is because of 2) in your original post. I'm afraid I don't know anything about configuring alsa outside of the alsa-mixer gui (you have checked that none of the options under the capture (F4) tab are muted in alsamixer right?).  Maybe someone who knows more can give you better help than me.  Alternatively, it might be an idea to purge and reinstall pulse audio.

---

### Post by hardikbv on 2012-09-21
Yes carranty, all the bars are at the top :( (except the ones with MM. I hope they are not the problem creators)

So, who is pitching in to help me.. Please, please...

---

### Post by carranty on 2012-09-21
Ok, so on my home computer I use gnome-shell rather than unity (still ubuntu 12,04) and in this I do get the hardware tab in the sound preferences box.  I suggest you install gnome-shell (sudo apt-get install gnome-shell)

and then log in to classic.  From here go into sound preferences and configure your mic. 

I'm not certain but I think sound preferences is just a gui of pulseaudio, so this may not work, but it can't do any harm (you can go back to unity simply by logging out and back in again).

---

### Post by hardikbv on 2012-09-22
Hi Carranty,

I installed gnome shell by suggested code.  It is fully installed.  

Now, how do I go into classic? When I load there are only four options, ubuntu 12.4, ubuntu 12.4 (recovery mode), older linux and Win7.  

When I select older linux, it only shows different ubuntus.  I tried one of them but it is leading me to the same current ubuntu version and the same sound preferences.  

Is this because I have started by Ubuntu journey with 12.4? Let me know the way forward.

---

### Post by carranty on 2012-09-22
> **hardikbv said:**
> Hi Carranty,

I installed gnome shell by suggested code.  It is fully installed.  

Now, how do I go into classic? When I load there are only four options, ubuntu 12.4, ubuntu 12.4 (recovery mode), older linux and Win7.  

When I select older linux, it only shows different ubuntus.  I tried one of them but it is leading me to the same current ubuntu version and the same sound preferences.  

Is this because I have started by Ubuntu journey with 12.4? Let me know the way forward.

To use classic (I can't remember exactly what its called - I'm on my work PC now but I think its called gnome CLASSIC) just boot up as usual, but when you get to the login screen don't input your password right away. Instead click the icon next to your username (I think its a paw) and from the resulting list choose gnome classic.  Then just click on the speaker icon > Sound Preferences, click the hardware tab and, hopefully, from there you can choose an appropriate profile.

---

### Post by hardikbv on 2012-09-22
Hi Carranty,

No luck.  The Hardware and Inputs both are blacked out here also. 

Please help. 

[IMG]Screenshot from 2012-09-22 17:49:24.png[/IMG]

---

### Post by hardikbv on 2012-09-23
Any help for me?

---

### Post by hardikbv on 2012-09-25
Hello Friends,

I tried removing and re installing Pulse Control manager and Alsa Mixer.  But problem remains the same :(

After this install and reinstall, whenever I try and click on the Pulse Contorller it shows 'Fatal Error : OK'.  It doesn't open.  Any further help for my mic functioning, please.. 

Its a real pain to restart and go to Win7 to talk on skype.

Hardik

---

### Post by dougmoffatt on 2012-09-25
I have the same problem.  With sound recorder if I shout into the built in microphone I do get a recording but it is useless.  There is no input device in the sound settings.

---

### Post by hardikbv on 2012-09-27
Dear papibe, carranty and fellow colleagues,

Any help for me and dougmoffatt? 

Urgently needed.. 

Thanks

---

### Post by hardikbv on 2012-09-27
Hello.. 

New update.  I went to terminal and typed 'pulseaudio'.  This has activated the option of microphone in the sound settings.  Thoough, when I try to record something on sound recorder, the problem remains the same. 

PS : In sound recorder earlier there were 4/5 options for input, now there is only one 'Mater'

What does this mean?

---

### Post by hardikbv on 2012-09-29
Any help on this guys? 

Ubuntu experience is really turning nightmare when I have to go to my Win7 again and again to talk on Skype :(

---

### Post by dpharo on 2012-09-29
Try this: right click the volume control in the top command bar. At the bottom of that window is a selection called "sound settings".  There are four tabs, output, input, sound effects and applications. Click on input, if you have an external microphone plugged in there it will be displayed. Select the desired microphone and make sure input volume is not muted or down low.

I hope this helps.:)

---

### Post by hardikbv on 2012-09-29
Thanks for the help dpharo.

It does not work.  I have tried it earlier (refer previous posts) and just tried it now.

---

### Post by hardikbv on 2012-10-14
Colleagues, 

Should I consider that this community does not have any solution for this?

Hardik

---

### Post by papibe on 2012-10-14
Could you post the result of this command?
```
groups
```
Regards.

---

### Post by hardikbv on 2012-10-16
hardik adm cdrom sudo dip plugdev lpadmin sambashare

---

### Post by papibe on 2012-10-16
Thanks.

Add yourself to the audio group:
```
sudo usermod -a -G audio yourusername 
```
Then restart your machine. After that try again the next command:
```
pactl list cards
```
Post your results.

Regards.

---

### Post by hardikbv on 2012-10-17
This is what comes after restarting the computer 

Connection failure: Connection refused
pa_context_connect() failed: Connection refused

Before restarting following comes when I enter the code 
usermod: user 'yourusername' does not exist

---

### Post by papibe on 2012-10-17
Replace 'yourusername' with your actual Ubuntu's username.

Regards.

---

### Post by hardikbv on 2012-10-17
Sorry for silly question, papibe.

How do I get to know my username? It seems I have forgot it.

Is this the same which appears on the terminal? (i.e. hardik@hardik-HP-Pavilion-tx1000-Notebook-PC:~$)

---

### Post by papibe on 2012-10-17
Yes, so it is probably 'hardik'.

You can double check by running:
```
echo $USER
```
Regards.

---

### Post by hardikbv on 2012-10-18
hardik@hardik-HP-Pavilion-tx1000-Notebook-PC:~$ pactl list cards 
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

This comes :( I have run the first command more than 3 times :(

---

### Post by hardikbv on 2012-10-27
Dear Papibe,

Some updates :

-- I upgraded to 12.10 
-- The problem has remained the same. 
I tried above command after upgrade. 
Following is the outcome.

hardik@hardik-HP-Pavilion-tx1000-Notebook-PC:~$ pactl list cards 
Connection failure: Connection refused
pa_context_connect() failed: Connection refused
hardik@hardik-HP-Pavilion-tx1000-Notebook-PC:~$ 

Please suggest the way forward.

Hardik

---

### Post by papibe on 2012-10-27
Could you post the result of these commands?
```
lspci -nnk | grep -iA2 audio

arecord -l
```
Regards.

---

### Post by hardikbv on 2012-10-29
Response of the first command 

00:10.1 Audio device [0403]: NVIDIA Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
	Subsystem: Hewlett-Packard Company Device [103c:30bf]
	Kernel driver in use: snd_hda_intel

Response to second command 

**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861-VD Analog [ALC861-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by papibe on 2012-10-29
Thanks. That looks OK.

Is this a laptop or a desktop?
In case is a desktop, what kind of microphone are you using?

Could you post the result of this command?
```
lsmod | grep -i snd_hda_intel
```
Regards.

---

### Post by hardikbv on 2012-10-30
Hi.

It is laptop.  I am using creative HS 150 microphones.  (Note : My inbuilt speakers are not working for almost a year now)

My current microphone set works perfect in Windows 7.

Result : 

snd_hda_intel          32515  0 
snd_hda_codec         111547  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_pcm                80163  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd                    61991  10 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm

---

### Post by papibe on 2012-10-30
Let's check if pulseaudio is running. Could you post the result of these commands?
```
ps aux | grep pulseaudio

sudo service pulseaudio status
```
Then, could you paste the content of these files?
```
/etc/pulse/client.conf

/etc/default/pulseaudio
```
Regards.

---

### Post by hardikbv on 2012-10-31
Results :

First command 

hardik    3015  0.0  0.0   4392   820 pts/0    S+   13:31   0:00 grep --color=auto pulseaudio

Second command 

pulseaudio stop/waiting

Third Command 

bash: /etc/pulse/client.conf: Permission denied

Forth Command 

bash: /etc/default/pulseaudio: Permission denied

---

### Post by papibe on 2012-10-31
Thanks.

We got something!: 'pulseaudio' is not running.

Let's try to reinstall it.

First, uninstall it:
```
sudo apt-get purge pulseaudio
```
Then install it again:
```
sudo apt-get update
sudo apt-get install pulseaudio
```
If that doesn't work, please post the result of this command?
```
cat /etc/pulse/client.conf
```
Let us know how it goes.
Regards.

---

### Post by hardikbv on 2012-11-01
I haven't run the last command.  Following in the result of the previous process.  Should I run the last command? 

hardik@hardik-HP-Pavilion-tx1000-Notebook-PC:~$ sudo apt-get install pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-folks-0.6 gir1.2-gee-1.0 language-pack-kde-en language-pack-zh-hans
  language-pack-zh-hans-base libcelt0-0 libopenspc0 nvidia-settings
  packagekit-backend-aptcc python-gmenu screen-resolution-extra
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by papibe on 2012-11-01
What about the first one?

It looks you didn't uninstall pulseaudio before re installing it.

Regards.

---

### Post by hardikbv on 2012-11-02
I guess, this time I did it correctly.  Should I still run the last command?

0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 923 kB of archives.
After this operation, 3,462 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal/main pulseaudio i386 1:2.1-0ubuntu4 [905 kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal/main pulseaudio-module-x11 i386 1:2.1-0ubuntu4 [18.5 kB]
Fetched 923 kB in 17s (53.7 kB/s)                                              
Selecting previously unselected package pulseaudio.
(Reading database ... 184226 files and directories currently installed.)
Unpacking pulseaudio (from .../pulseaudio_1%3a2.1-0ubuntu4_i386.deb) ...
Selecting previously unselected package pulseaudio-module-x11.
Unpacking pulseaudio-module-x11 (from .../pulseaudio-module-x11_1%3a2.1-0ubuntu4_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up pulseaudio (1:2.1-0ubuntu4) ...
Adding user pulse to group audio
Processing triggers for ureadahead ...
Setting up pulseaudio-module-x11 (1:2.1-0ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by hardikbv on 2012-11-02
If above was correct, which I assume yes, then even after uninstall, reinstall and re start the sound recorder is not working.  

I ran the last command and following is the result. 

hardik@hardik-HP-Pavilion-tx1000-Notebook-PC:~$ cat /etc/pulse/client.conf
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for PulseAudio clients. See pulse-client.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; default-sink =
; default-source =
; default-server =
; default-dbus-server =

; autospawn = yes
; daemon-binary = /usr/bin/pulseaudio
; extra-arguments = --log-target=syslog

; cookie-file =

; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; auto-connect-localhost = no
; auto-connect-display = no

---

### Post by hardikbv on 2012-12-17
Papibe,

What should be the way forward?

Hardik

---

### Post by hardikbv on 2013-02-22
Is there any solution for my problem?

---

