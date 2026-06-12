---
title: "No Sound Please help"
date: 2011-06-14
forum: General Help
---

### Post by tej1984 on 2011-06-14
What happened was that I was trying a config setting with Boxx/ HDMI and then the sound worked-  but browser videos such as BBCiplyer/ youtube did not work. NOW I have messed up something with the sound and the volume icon and everything has gone. The only sound I hear is the ubuntu login drum beat and then nothing PLEASE HELP its been 4 days and i have been stressed. Is there anyway of restoring it to default or getting the sound back...I have tryed everything even looked at someones elese thread with simliar issues but nothing PLEASE help me. 

Ubuntu 10.10 
Acer Revo 3700

PS everything worked fine but I did something and now I really do not want to do a full reinstall I have so much work on here!!

---

### Post by tej1984 on 2011-06-15
OK so I reinstalled the Alsamix again and still nothings. So i created a new user and the sound works perfectly for that user. So its  my user work space is there any config file I can change to revert is back to default but not loose any work? OR set the driver to default. 
Acer Revo 3700 running Ubuntu 10.10

I thought I would give ubuntu 10.10 a try & I love it but these issue really makes me think about going back to windows!! BUt i do not want too!!! 

Software should be free!!!!!

---

### Post by Yellow Pasque on 2011-06-15
> everything worked fine but I did something
It's difficult to tell you how to undo something if you don't tell us what you did...

---

### Post by tej1984 on 2011-06-15
sorry my bad ---

Long story short!! 

I wanted to connect my Acer revo to my TV HDMI and there was no sound. So then I Started to play about with the sound driver and alsamixer. I installed it restarted it and then the sound began to work on this program called Boxee but ddn't work on the ubuntu workspace ie VLC or apps on ubuntu

SO then I had enough and thought i would just plug my computer back into my monitor and then the sound didn't work when i wanted to watch youtube videos or bbciplyer but none of the browsers had sound but i could play music in Ubuntu and the sounds worked but now I have no sound I installed pulseaudio again and alsamixer. The sound cards have been picked up but there is no sound I think it still thinks i have connected via HDMI 

Also when i look under Admin > Preferences > sounds 

boths sound card are shown one internal audio intel the other HDMI but there speaker tests does not work...

This is so stressfull !!! I Know i could have fixed this in windows but ubuntu is a different ball game..

How to i ensure that the sound card is set to internal audio and not HDMI 

  Also

in the Alsamixer 

the default card is Pulseaudio and not Alsamixer how do i change it? 

also the PCM sound has no <00> or <MM> i swear they used to be there !!! 

HELP!!

---

### Post by tej1984 on 2011-06-15
sorry my bad ---

Long story short!! 

I wanted to connect my Acer revo to my TV HDMI and there was no sound.  So then I Started to play about with the sound driver and alsamixer. I  installed it restarted it and then the sound began to work on this  program called Boxee but ddn't work on the ubuntu workspace ie VLC or  apps on ubuntu

SO then I had enough and thought i would just plug my computer back into  my monitor and then the sound didn't work when i wanted to watch  youtube videos or bbciplyer but none of the browsers had sound but i  could play music in Ubuntu and the sounds worked but now I have no sound  I installed pulseaudio again and alsamixer. The sound cards have been  picked up but there is no sound I think it still thinks i have connected  via HDMI 

Also when i look under Admin > Preferences > sounds 

boths sound card are shown one internal audio intel the other HDMI but there speaker tests does not work...

This is so stressfull !!! I Know i could have fixed this in windows but ubuntu is a different ball game..

How to i ensure that the sound card is set to internal audio and not HDMI 

  Also

in the Alsamixer 

the default card is Pulseaudio and not Alsamixer how do i change it? 

also the PCM sound has no <00> or <MM> i swear they used to be there !!! 

HELP!!
 		                   		  		  		  		  		 		 			 				 				* 					 						[Last edited by tej1984]("http://ubuntuforums.org/posthistory.php?p=10941469"); 1 Minute Ago at 05:23 AM.. 					 					 				*

---

### Post by tej1984 on 2011-06-15
Anyone out there?

---

### Post by tredegar on 2011-06-15
I'm using 10.04 but...

Click your volume icon (if it's not there, RClick panel, add, indicator applet)
Click preferences. Click Hardware Tab.
Select the non HDMI device.
Set it to Analog stereo Duplex.

Click Output Tab. Select the non-HDMI device.

Check the output volume.

Close. Does sound work?

Note, in alsamixer, in a terminal **<MM>** means Muted and **F6** allows you to select which card to configure.

Alternatively, make a note of the settings for the user who does have sound, and then apply them to your user.

---

### Post by tej1984 on 2011-06-15
Hello thanks so much for this input I will give it a try..
 
I have heard that there are folders which can be deleted to set the configration to default is this possible that it will resolve my should issues?

---

### Post by Yellow Pasque on 2011-06-15
> So then I Started to play about with the sound driver and alsamixer. I installed it..
You installed what? A sound driver? Which one?

> SO then I had enough and thought i would just plug my computer back into my monitor and then the sound didn't work when i wanted to watch youtube videos or bbciplyer but none of the browsers had sound but i could play music in Ubuntu and the sounds worked but now I have no sound I installed pulseaudio again and alsamixer. 
Wow. That is one confusing run-on sentence.

> I have heard that there are folders which can be deleted to set the configration to default is this possible that it will resolve my should issues?
You can try resetting pulseaudio config files and logging out.
```
rm -rf ~/.pulse*
```

Please run the alsa-info script: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

### Post by tej1984 on 2011-06-15
Hi sorry to be a pain but how to i run it?

I installed pulse audio

---

### Post by Yellow Pasque on 2011-06-15
If, for example, you saved the tar file to ~/Downloads:
```
cd ~/Downloads #or whatever directory you have the file in
untar alsa-info.tar
chmod +x alsa-info.sh
./alsa-info.sh
```

---

### Post by tej1984 on 2011-06-15
i ran that rm pluseaudio and by volume icon has gone form the top bar oh no!!! 

I ran this -- is this correct? 



tej@Tyson:~/Downloads$ untar alsa-info.tar
No command 'untar' found, did you mean:
 Command 'unrar' from package 'unrar-free' (universe)
 Command 'unrar' from package 'unrar' (multiverse)
untar: command not found
tej@Tyson:~/Downloads$ 
tej@Tyson:~/Downloads$ chmod +x alsa-info.sh
chmod: cannot access `alsa-info.sh': No such file or directory
tej@Tyson:~/Downloads$ chmod +x alsa-info.sh
tej@Tyson:~/Downloads$ chmod +x alsa-info.sh
tej@Tyson:~/Downloads$ chmod +x alsa-info.sh
tej@Tyson:~/Downloads$ ./alsa-info.sh
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: Failed to open config file alsa-base.save: Permission denied
ALSA Information Script v 0.4.58
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See './alsa-info.sh --help' for command line options.

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: Failed to open config file alsa-base.save: Permission denied
Newer version detected: 0.4.60
To view the ChangeLog, please visit [http://www.alsa-project.org/alsa-info.sh.changelog](http://www.alsa-project.org/alsa-info.sh.changelog)
The original file ./alsa-info.sh will be overwritten!
If you do not like to proceed, press Ctrl-C now..
ALSA-Info script has been updated. Please re-run it.
tej@Tyson:~/Downloads$

---

### Post by Yellow Pasque on 2011-06-15
> **tej1984 said:**
> i ran that rm pluseaudio and by volume icon has gone form the top bar oh no!!!
Did you log out?
Also, I guess the alsa-info script needs root permissions:
```
sudo ./alsa-info.sh
```

---

### Post by tej1984 on 2011-06-15
See './alsa-info.sh --help' for command line options.

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
Home directory /home/tej not ours.
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=01c81296decb1eec61293ec51078ae8e408521d9](http://www.alsa-project.org/db/?f=01c81296decb1eec61293ec51078ae8e408521d9)

Please inform the person helping you.

---

### Post by tredegar on 2011-06-15
> I ran this -- is this correct?


**beyonce_4-wallpaper-1152x864.jpg**
**Birdy_-_Skinny_Love.6230444.TPB.torrent**
Boxee
firefox-4.0.1.tar.bz2
**Get_Him_to_the_Greek_(2010)_DVDRip_XviD-MAX.5840407.TPB.torrent**
gnome-do-docklets_0.8.2-2_all.deb
**IMG00476-20110515-1442.jpg**
**IMG00478-20110515-2038.jpg**
**Jeepers.Creepers.Pack.DVDRip.XviD-TPB.6336986.TPB.torrent**
**[MZC] DJ Sanj - Rewind (30 Minutes Of Old Skool Madness)(By.NagRa)[320-VBR-iTunes Rip]-May.2k11.zip**
**Nero_-_Guilt_[2011_-_Single].6282170.TPB.torrent**
ortek-2.6.35.patch.gz
**PITBULL_HOTEL_ROOM_SERVICE_Official_Video_720p_HD_ VIDEO_BY_DHOOM2011_mp4-[Fenopy.eu].torrent**
[B]Pitbull_-_I_Know_You_Want_Me_(Calle_Ocho)[2009]_AVI_VIDEO_SHAR19.5496233.TPB.torrent
Radio Stations[/B]
**[COLOR="Red"]Sexy-Colombianas-Girls-Gone-WIld[/COLOR][[www.savevid.com].flv](www.savevid.com].flv)**

I fear you have lost the plot, or perhaps are otherwise incapacitated.

Unsubscribing from this thread.

---

### Post by tej1984 on 2011-06-15
it would be helpful if you could resolve this issue

---

### Post by Yellow Pasque on 2011-06-15
4chan might have some helpful advice for you..

---

### Post by tej1984 on 2011-06-15
Waiting for sound system to respond

this is what i get when i click on system> preferences >sound

---

### Post by tej1984 on 2011-06-15
Its all over people - I messed up my workspace 

What i did was copy the files form a new workspace i had created - 

.gnome .gnome2 .gconf .gconfd

and now when i login I get this Message saying there is a password miss match and the whole desktop is locked I can only turn computer off mines to restart it!! I have failed and hit a brick wall.

---

### Post by tej1984 on 2011-06-15
is there anyway of transferring my files from that work space to the one i am using now or have access to that work space and once I transfer the files I can delete it???

---

