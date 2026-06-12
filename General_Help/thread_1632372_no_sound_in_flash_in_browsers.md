---
title: "no sound in flash in browsers"
date: 2010-11-27
forum: General Help
---

### Post by Preserved Killick on 2010-11-27
Hi folks.  I hope someone can help.

I'm running Ubuntu 10.4, Firefox 3.6.12 and Flash 10.1 r102 and Chrome 8.0.552.208 beta.  Both of these browsers will show video, but not play sounds.

I *do* have sound with Rhythmbox or when playing games, eg bzflag.

I have tried removing firefox and downloading the tarball version from Mozilla.  I have tried running firefox as root.  I have upgraded to the latest firefox and latest flash.

If you know what's gone wrong or have an idea about how to find out, please reply.

Thanks!

Killick

---

### Post by Preserved Killick on 2010-11-28
I installed Opera and flash still has no sound.  I'm pretty sure this is a flash issue, as it's coming up across three browsers.  Any ideas on how to fix this?

---

### Post by sikander3786 on 2010-11-28
This might help. Courtesy of forum member **lovinglinux**,

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by Preserved Killick on 2010-11-28
Thanks, Sikander.  I appreciate your offering help.  I read through what's there for the 'no sound' problem.  (I have posted what's on the site below).  When I looked, I saw that the file I'm to delete doesn't exist on my system, and that I need to install asound-gtk.  And then I need to make PulseAudio my default sound card.  I thought PulseAudio was a sound server.  I don't understand what exactly ALSA is.

I used to have sound in flash and now I don't.  It failed on Ubuntu 9.04 and I upgraded to 10.4 and it still isn't working.

The directions for changing the sound card don't match what I see when I click System >> Preferences >>.  After Preferences, there is Sound, but none of the tabs mention setting a default sound card.  And by the way, my machine has two sound cards-- one built-in and a second I added but am no longer using.

Sound Preferences "Output volume" is set at 1000%.

When looking at the Sound Preferences "Applications" tab, I tried running a YouTube video on Firefox.  It shows "ALSA plug-in[plugin-container]" and the volume slider is all the way over to the maximum.  But no sound is playing that I can hear.

I then also started Rhythmbox and it shows as "Rhythmbox" and the slider is about 2/3 of the way to the maximum.  I can hear Rhythmbox.

I don't want to break sound everywhere else to fix flash.  If I were to install asound-gtk would that change my System >> Preferences menu and then show me an option to choose a default sound card?  And by sound card, am I talking about the physical hardware, the PulseAudio server, or something else?

Shouldn't I be using PulseAudio already?

Anyone who will help is welcome to jump in here.  Thanks again to Sikander!


Here's what the website instructs:

"    * No sound in flash, but sound works elsewhere


Run the following commands:

Code:

rm -fr ~/.pulse ~/.asound*
sudo rm /etc/asound.conf


Create a asound.conf file with the command below:

Code:

gksudo gedit /etc/asound.conf


Then add the following code and save it:

Code:

pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}


Set up PulseAudio as the default sound card:

Code:

sudo apt-get install asound-gtk 


Then go to System >> Preferences >> Default Sound Card and ensure that PulseAudio is selected, and restart your browser.


Sources:

    * [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
"

---

### Post by Aquix on 2010-11-29
I've had this problem before and after loads of searching the solution was too easy. 

Preferences  > sound > applications tab    ... when playing a video  on youtube it should come up:  ALSA Plug-in [firefox-bin]    and just unmute.  If not then search on.

---

### Post by excetara2 on 2010-12-01
I added the above asound.conf pulse config to the \etc\ folder but what exactly does this do?? Shouldn't the default be pulse anyway?

It made it work so.

Cheers,
Jeff

---

### Post by Preserved Killick on 2010-12-01
> **Aquix said:**
> I've had this problem before and after loads of searching the solution was too easy. 

Preferences  > sound > applications tab    ... when playing a video  on youtube it should come up:  ALSA Plug-in [firefox-bin]    and just unmute.  If not then search on.

Hmmm.  I wish that was my issue.  My sound is already un-muted.  Thanks for the tip, though.

---

### Post by excetara2 on 2010-12-01
Did you give this part a go?? My sound worked everywhere except the browsers in flash. I added this asound.conf file and now it works flawlessly. Just add it and restart browser. Now log out or restart necessary so real easy to try.

> Code:

gksudo gedit /etc/asound.conf


Then add the following code and save it:

Code:

pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}


---

### Post by Preserved Killick on 2010-12-02
I tried creating /etc/asound.conf and restarting the browser, but there was no change.

I then went through all the steps described.  Now I have no sound, at all, in any program.

When it came time to install asound-gtk, I saw that this package didn't exist, but there was a program call asoundconf-gtk, described as an applet to select the default sound card.  So I installed it.

Next I looked in the System >> Preferences >> and found that there was a "Default Sound Card" separate from the "Sound" item.  I clicked it, but it never launched-- I saw the message in my bottem panel that it was starting, but nothing ever showed on my screen.  I tried it twice.

Now when I try to use System >> Preferences >> Sound, the Sound applet will not start.  Instead I get a box "Waiting for sound system to respond" [cancel].  

I tried launching asoundconf-gtk from the terminal, thinking I'd at least get an error.  I saw this: 

~$ asoundconf-gtk
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

So I looked for .asoundrc.asoundconf but it's not in my system.

Next I tried copying /etc/asound.conf to /home/user/.asoundrc.asound.conf.

Then I tried running sudo asoundconf-gtk again, and got the same message as above.

Rhythmbox-- no sound
Mplayer-- no sound
YouTube-- no sound

My sound system is thoroughly borked now.  

Anyone have advice on how to recover?  I'm 1/2 way to thinking I'll just reinstall the whole OS, even though the fresh install didn't fix the flash problem last time.  At least I had some sound.

Anyone?  Thanks,

killick

---

### Post by excetara2 on 2010-12-02
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils and 

then

sudo apt-get install linux-sound-base alsa-base alsa-utils gdm gnome-desktop

This resets your sound drivers so reinstall is not necessary. Reboot after running the above two commands. It won't remove the asound.conf file so I'd leave that in place for now. Hopefully, you get your sound back. If not, post again. Maybe with the reset and asound.conf file you'll get flash sound back. If not, install FLASH-AID and run it. It's a firefox app to remove all extraneous flash apps and just install the 64-bit square beta. Give the above a go and let us know.

Cheers.

---

### Post by Preserved Killick on 2010-12-02
Thanks excetara2.  I did the removals and then ran the installs you suggested, but didn't find gnome-desktop.  I suspected you meant ubuntu-desktop, so I ran that install instead.  No sound anywhere.  :-(

Not sure what to try next.  I haven't been down this road.  Suggestions?

---

### Post by excetara2 on 2010-12-02
Did you restart after the installs. That should set it back to default sound settings but there is an alsa-info script floating around you can run to provide more information. I'd search for it and post the link to the results after trying the removal and reinstall again. Make sure to reboot after. You should get sound back as it was on the original install. Did you ever change the /etc/modprobe.d/alsa-base.conf file previously to get it working because the above will reset that??

---

### Post by Preserved Killick on 2010-12-03
> **excetara2 said:**
> Did you restart after the installs. 

Yes.  Script wouldn't run.  Did do cat /proc/modules.  

Did you ever change the /etc/modprobe.d/alsa-base.conf file previously to get it working because the above will reset that??

I am not aware that anything I have done would have changed the alsa-base.conf file.

Here is the output of cat /proc/modules.  I don't know what this tells me, but you can see that I have two sound cards installed.  

```

binfmt_misc 6587 1 - Live 0xf8044000
snd_hda_codec_realtek 203344 1 - Live 0xf962d000
snd_hda_intel 22005 2 - Live 0xf95d0000
snd_hda_codec 74201 2 snd_hda_codec_realtek,snd_hda_intel, Live 0xf95a3000
snd_hwdep 5412 1 snd_hda_codec, Live 0xf9580000
snd_ca0106 31531 2 - Live 0xf956b000
snd_ac97_codec 100646 1 snd_ca0106, Live 0xf9539000
ac97_bus 1002 1 snd_ac97_codec, Live 0xf950e000
snd_pcm_oss 35308 0 - Live 0xf94fc000
snd_mixer_oss 13746 1 snd_pcm_oss, Live 0xf94e4000
snd_pcm 70694 5 snd_hda_intel,snd_hda_codec,snd_ca0106,snd_ac97_codec,snd_pcm_oss, Live 0xf94a5000
snd_seq_dummy 1338 0 - Live 0xf9483000
snd_seq_oss 26722 0 - Live 0xf9471000
snd_seq_midi 4557 0 - Live 0xf945d000
snd_rawmidi 19056 2 snd_ca0106,snd_seq_midi, Live 0xf944b000
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi, Live 0xf9439000
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xf9420000
snd_timer 19098 2 snd_pcm,snd_seq, Live 0xf84bc000
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xf847c000
fbcon 35102 71 - Live 0xf93e0000
ppdev 5259 0 - Live 0xf8459000
usbhid 36110 0 - Live 0xf8467000
tileblit 2031 1 fbcon, Live 0xf8141000
font 7557 1 fbcon, Live 0xf80f1000
bitblit 4707 1 fbcon, Live 0xf80ea000
snd 54180 22 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xf811c000
parport_pc 25962 1 - Live 0xf808d000
hid 67032 1 usbhid, Live 0xf80b1000
nvidia 7087672 24 - Live 0xf8c4a000 (P)
softcursor 1189 1 bitblit, Live 0xf8041000
agpgart 31724 1 nvidia, Live 0xf84b2000
intel_rng 2276 0 - Live 0xf8499000
soundcore 6620 1 snd, Live 0xf848c000
snd_page_alloc 7076 3 snd_hda_intel,snd_ca0106,snd_pcm, Live 0xf847f000
vga16fb 11385 1 - Live 0xf8471000
vgastate 8961 1 vga16fb, Live 0xf8462000
lp 7028 0 - Live 0xf8455000
parport 32635 3 ppdev,parport_pc,lp, Live 0xf815a000
ohci1394 26950 0 - Live 0xf8131000
usb_storage 39553 0 - Live 0xf8110000
ieee1394 81181 1 ohci1394, Live 0xf80d4000
via_rhine 19154 0 - Live 0xf80aa000
mii 4381 1 via_rhine, Live 0xf8097000
floppy 53016 0 - Live 0xf807e000
sky2 40807 0 - Live 0xf8051000

```

---

### Post by excetara2 on 2010-12-03
Did you chmod a+x scriptnamehere ?? Its just an info script no reason it shouldn't run.

---

### Post by excetara2 on 2010-12-03
Script name is alsa-info.sh

---

### Post by Preserved Killick on 2010-12-03
As I was googling the script, I came across the command ubuntu-bug audio.

I ran that and it launched a gui that asked me some multiple choice questions and began self-testing.  

It paused and told me, 

"You seem to have configured PulseAudio to use the "pci-0000_00_1b.0" card, while you want output from "CA0106 - CA0106".
 Please correct that using pavucontrol or the GNOME volume control. Continue anyway?"

so I ran pavucontrol but this didn't seem to have any way to choose soundcards.  Neither did the GNOME volume control, But when I looked in my Applications >> Sound and Video I saw Pulse Audio Volume Control.  I don't know when that got installed, but I would swear it wasn't there the last time I'd looked. 

At some point, something I monkeyed with fixed things.  I now have sound in flash, from Rhythmbox, and in games.  I even have system sound when I click a button in the panel.  

Excetera2, thank you for hanging in here with me.  

Killick:P

---

### Post by excetara2 on 2010-12-03
No worries, sounds like pulse got borked but good to hear its going.

---

### Post by boofly on 2011-01-28
> **Aquix said:**
> I've had this problem before and after loads of searching the solution was too easy. 

Preferences  > sound > applications tab    ... when playing a video  on youtube it should come up:  ALSA Plug-in [firefox-bin]    and just unmute.  If not then search on.

ROFLOL. Worked! Thanks.

---

