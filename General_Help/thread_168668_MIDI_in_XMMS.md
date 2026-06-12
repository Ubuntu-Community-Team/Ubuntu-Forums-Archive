---
title: "MIDI in XMMS"
date: 2006-04-30
forum: General Help
---

### Post by oofnik on 2006-04-30
I've read everything I found on here about how to get MIDI working. So far I've gathered that Timidity is a software synthesizer that can play MIDI files with a soundfont. However, I have an Audigy soundcard which is perfectly capable of playing MIDI files on hardware. I can play the files using both ```
$timidity file.mid
``` and ```
$playmidi -a file.mid
``` The -a option of playmidi uses the direct hardware synthesizer, which I'm guessing is accessed through snd_emu10k1_synth. I've probably got this all backwards, but it works.

Now I really want to be able to play these files in XMMS. I tried installing libtimidity, and xmms-timidity, but neither of them work. They open the file, and appear to be playing it but no sound is produced. What is the best way to play a MIDI file through XMMS using the hardware synthesizer instead of the timidity emulation?

If you're wondering why the hell I want to do this, there are two reasons, 1) to preview ringtones I download before I go through the trouble of bluetoothing them to my phone, and 2) because I'm freakishly OCD about things and I want it all to work my way. :D

Thanks everyone!

---

### Post by Zimmer on 2006-05-01
A Guess. Change the default sound card in Preferences? to the MPU-401UART 
MIDI interface?  Might only switch it to output the midi data, though...

---

### Post by oofnik on 2006-05-01
Unfortunately this does not work, but thanks for the suggestion.  Apparently playmidi -a is doing something that I haven't been able to do with any other program, and I can't quite figure out what it is doing. There is hardly any documentation out there on linux MIDI support... argh.

---

### Post by Zimmer on 2006-05-02
> Installed timidity lastest version, installed this xmms midi plugin, loaded a .mid file, the xmms shows it is playing, but there is no sound! I am using xmms lastest version on RH6.1. I then tried playmidi, and got a message saying /dev/sequencer cannot be found. Looked into /dev and found it. What went wong? If the existing /dev/sequencer is invalid, how to recreate it? Thanks.
> 
You don't need /dev/sequencer or any other midi interface with TiMidity (and xmms-midi plugin). TiMidity converts midi to wave by using Gravis Ultrasound Wavetable patches. I suppose you don't have those. Check out [http://www.goice.co.jp/member/mo/timidity/](http://www.goice.co.jp/member/mo/timidity/) for more information.
are snippets I found here: [http://www.xmms.org/plugins.php?details=42](http://www.xmms.org/plugins.php?details=42)
and if you read the other posts there, too, you may find some more helpful hints re: Timidity. The config file  for Timidity may be set up to look at the wrong directories for your Ubuntu set up , for example.. 
I looked to trying midi on Ubuntu late last year, I needed it as backup for the Roland keyboard we use in our singing group. Because of time constraints I gave up and used a Windows laptop instead :(  (Shame on me!)
However, you have just re awakened my curiosity, so perhaps I will load Timidity in the next few days and investigate...
Oh, and I just found this, by chance..any use?
[http://www.geocities.jp/midi_organ_net/timidity/](http://www.geocities.jp/midi_organ_net/timidity/)

---

### Post by FarEast on 2006-05-04
Hi;) ,

> Now I really want to be able to play these files in XMMS. I tried installing libtimidity,
> and xmms-timidity, but neither of them work. They open the file, and appear to be
> playing it but no sound is produced. What is the best way to play a MIDI file through
> XMMS using the hardware synthesizer instead of the timidity emulation?

I think it may be better to use 'kmid'.  It depends on kde packages but runs on gnome
with no problem.

Regards

---

