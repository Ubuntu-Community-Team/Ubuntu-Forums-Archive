---
title: "Lossless Audio - making monkeys lossless work"
date: 2005-03-05
forum: General Help
---

### Post by paretooptimum on 2005-03-05
Can anyone tell me how to get monkeys lossless compression codec working in Ubuntu? 

I am using totem/gstreamer in Ubuntu Hoary.

.I have loaded the rarewares debian repository in synaptic.

[http://www.rarewares.org/debian/packages/unstable](http://www.rarewares.org/debian/packages/unstable)

 From this I have installed: gstreamer0.8-monkeysaudio 0.8.0-1

When I open an .ape file, Totem crashes (bang). 

OK, I'm not the only person with this probelm. The attached link has a story of
someone having exactly the same problem with no solution. This guy says its a
mime problem? (see below)

[http://www.monkeysaudio.com/smf/index.php?topic=1693.msg7466](http://www.monkeysaudio.com/smf/index.php?topic=1693.msg7466)

Can someone solve this?

<snip>

Hi!

Having recently (well... 48 sleepless hours  Cheesy) switched from WinXp to
Linux Ubuntu, the very last step before I drop my dual boot is monkey support.

As Gnome/Ubuntu comes with Gstreamer, I thought it was a good idea to keep that
line of work, and I tried to get the monkey  plug work... in vain.

I know this is not an Ubuntu/Gnome/Gstreamer support forum; but a Monkey one; so
maybe one of you have some human light to put in my ape darkness Wink.

Here I went (please forgive my dumbness, I'm in the linux-newbie category):
* => System up and running, with all latest warty security patches. Audio working.
* I did apt-get a bunch of gstreamer modules and plugins  [from deb
[http://pkg-gnome.alioth.debian.org/debian/](http://pkg-gnome.alioth.debian.org/debian/) experimental main]
* I did apt-get the monkey plug [from deb
[http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./]
* I did gst-register the whole thing.
* => Mp3 (at least)  working.

Now comes the troubles:
(i) Rhythmbox won't play my apes (just hang on)
(ii) I tried to test direclty from gstreamer: monkeysaudio plugin is reporting
there, but following the instructions on
[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/faq/html/chapter-using.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/faq/html/chapter-using.html)
just ended-up with a "no suitable pipe for apes" when trying to play
(iii) Last, I noticed that my apes files were incorrectly showing an audio/x-mp3
mimetype

For this last point (iii), I dug into the "new" Gnome mime type system, ended-up
fighting with [http://freedesktop.org/wiki/Standards_2fAddingMIMETutor](http://freedesktop.org/wiki/Standards_2fAddingMIMETutor), and
finally totally lost: I successfully added a package to define
application/x-ape, but strangely Nautilus swap the mimetype from
application/x-ape to audio/x-mp3 as soon as I click on the file (obviously
caused by that part of the mp3 mime definition:
<magic priority="50">
      <match value="0xfffb" type="big32" offset="0"/>
      <match value="ID3" type="string" offset="0"/>
      <match value="0xfff0" type="big16" offset="0" mask="0xfff0"/>
</magic>
)

I'm not sure about the link between the mime-type problem and the "can't play"
problem...

Anyhow,  I hope that this message has something to do on the monkey forum...

... And wish you all good apes!


dMp

---

### Post by bored2k on 2005-03-05
I didn't even know .ape existed .

---

### Post by paretooptimum on 2005-03-06
If you're an audio freak and into lossless audio, It's the most efficient lossless codec around. 

[http://www.monkeysaudio.com/comparison.html](http://www.monkeysaudio.com/comparison.html)

When you decide to rip all 350 cds in your collection to a lossless format, every megabyte counts. Album for album I'm saving about 10-15 meg in .ape vs. .flac, which really adds up.

[http://www.hydrogenaudio.org/forums/lofiversion/index.php/f19-600.html](http://www.hydrogenaudio.org/forums/lofiversion/index.php/f19-600.html)
[http://mp3.radified.com/audio_codec_comparison.htm](http://mp3.radified.com/audio_codec_comparison.htm)
[http://flac.sourceforge.net/comparison.html](http://flac.sourceforge.net/comparison.html)

Hope these help.

---

### Post by bored2k on 2005-03-06
[QUOTE=paretooptimum]If you're an audio freak and into lossless audio, It's the most efficient lossless codec around. 

[http://www.monkeysaudio.com/comparison.html](http://www.monkeysaudio.com/comparison.html)

When you decide to rip all 350 cds in your collection to a lossless format, every megabyte counts. Album for album I'm saving about 10-15 meg in .ape vs. .flac, which really adds up.

[http://www.hydrogenaudio.org/forums/lofiversion/index.php/f19-600.html](http://www.hydrogenaudio.org/forums/lofiversion/index.php/f19-600.html)
[http://mp3.radified.com/audio_codec_comparison.htm](http://mp3.radified.com/audio_codec_comparison.htm)
[http://flac.sourceforge.net/comparison.html](http://flac.sourceforge.net/comparison.html)

Hope these help.[/QUOTE]
 Nice .

Forwarding to all my DJ friends now ;) ...

---

### Post by paretooptimum on 2005-03-06
We need to get it working first! :o

---

### Post by bored2k on 2005-03-06
[QUOTE=paretooptimum]We need to get it working first! :o[/QUOTE]
 u just wanna be able to play them ??
> I play ape using winamp with wine. First I installed the Monkey audio package, then I installed winamp, then I run the install plugin program in the Monkey audio folder. Works well.

---

### Post by paretooptimum on 2005-03-06
Well, yes, that's the question: can someone tell me how to make then play. I have the plug-in, I have the player, but "Houston, we have a problem..." Hey, post playing though, yea let's go crazy!! Let's make them as well!

---

### Post by Dragon_52 on 2005-03-11
OK, I've got it working  O:) 

Here's how ...

1. Download and install gstreamer0.8-monkeysaudio_0.8.0-1_i386.deb (I think it came from RareWares)
2. Run gst-register to get gstreamer to recognise the plugin
3. Restart Rhythmbox, import some files
4. Sit back and enjoy  O:)  O:)  O:) 

BTW I use Monkeys extensively, it is absolutely the best

---

### Post by paretooptimum on 2005-03-24
In instruction (2) in the comment above Dragon_52 means:

- Open a console
- type "gst-register-0.8" - assuming you are using 0.8
- string of modules, plug-ins registered

Unfortunately I've done this and it still doesn't work. Totem/Rhythmbox just crash. 

I can make ape files play in XMMS, though I would rather use something integrated into gnome. 

It's good to know someone has made ape files play. I'll keep trying. :-P

---

### Post by paretooptimum on 2005-03-24
I appear to have found the answer:

[http://bugzilla.gnome.org/show_bug.cgi?id=168035](http://bugzilla.gnome.org/show_bug.cgi?id=168035)

[http://www.monkeysaudio.com/smf/index.php?topic=1696.msg7484#msg7484](http://www.monkeysaudio.com/smf/index.php?topic=1696.msg7484#msg7484)

All my apes are compressed using the 3.99 codec.

Dragon_52 can you confirm the apes you are playing use an earlier codec?

---

### Post by paretooptimum on 2005-03-31
I can confirm myself that apes encoded with the 3.77 codec work in Totem (but strangely, for me at least, not Rhythmbox 0.8.8 (???) but apes encoded with 3.99 do not when using the rarewares codec. So its a codec issue. 

Anyone want to fix this? I've put a US$50 bounty on it in bugzilla.

---

### Post by paretooptimum on 2005-04-05
Here is a solution: (from the Monkey's Audio Forum)

<quote>
"Re: [LINUX] Gstreamer Monkey Plugin Trouble -- [[ 3.99 FIXED!!! ]]

i have no idea why 3.99 file formats were not backwards compatible, but whatever...

i managed to get it 3.99 encoded files working w/ gst

just build the MAC lib from [http://www.sourceforge.net/projects/mac-port/](http://www.sourceforge.net/projects/mac-port/) for linux (there is a 3.99 there)

then build the libgstmonkeysaudio.so using the monkeys audio plugin from the gstreamer website. after the build, just swap out the .a that is built within that pkg w/ the one you built from the sourceforge site. the output libgstmonkeysaudio.so will be compiled with the 3.99, and all will be good.

im listening to 3.99 apes right now w/ gstreamer :-) "
</quote>

I have to admit, this is probably beyond me. Can some one else "solve" this and send me the solution? i.e. "stick this in that folder"?

---

### Post by paretooptimum on 2005-06-05
FYI - for those who are interested:

OK, I gave up. I converted all my .ape files to .flac

This may not sound like much but we're talking 500+gb of lossless audio.

I used dbpowerAMP on my windows computer in batch mode and converted them all. It took about 2 days.

They all now work fine.

The moral of the story: use free codecs.

---

### Post by GrammatonCleric on 2005-07-28
better late then never... I just posted this HOW TO:

[http://ubuntuforums.org/showthread.php?t=52785](http://ubuntuforums.org/showthread.php?t=52785)

If your willing....give it another try.
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=200158#](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=200158#)

GC

---

### Post by Dragon_52 on 2005-08-04
[QUOTE=GrammatonCleric]better late then never... I just posted this HOW TO:

[http://ubuntuforums.org/showthread.php?t=52785](http://ubuntuforums.org/showthread.php?t=52785)

If your willing....give it another try.
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=200158#](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=200158#)

GC[/QUOTE]
 I've successfuly managed to install the latest gstreamer plugin for monkeys 3.99 (from Rarewares). I can play ape files encoded with monkeys 3.96 through to 3.99.

Unfortunately, I can only play them in Totem - Rhythmbox ignores them completely. It won't import a folder of ape files, and won't play an individual ape file - it doesn't crash, just does nothing.

The MIME type of the ape files is recognised as 'application/x-extension-ape' which may be related to the problem. Except Totem doesn't have any trouble.

Any suggestions anyone?

---

### Post by sc0rpi0n on 2005-08-15
[QUOTE=GrammatonCleric]better late then never... I just posted this HOW TO:

[http://ubuntuforums.org/showthread.php?t=52785](http://ubuntuforums.org/showthread.php?t=52785)

If your willing....give it another try.
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=200158#](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=200158#)

GC[/QUOTE]


this work partially for me cause i'm not able to seek the .ape encoded songs.. Any suggestions?

---

### Post by samtuba on 2005-11-06
Anybody able to make Sound Juicer and Rhythmbox work with Monkey's Audio in Breezy?  What codecs?  Where to get them?  How to conifure the pipline?  I'm a newb that is almost Windoze free.

Thanks

---

### Post by david.vikstrom on 2006-03-15
Can't make it work either, can't make the plugin work for beep, the gstreamer0.8-monkeysaudio_0.8.2-0rarewares1_i386.deb does not seem to be working for amd64 (duhh). So I pretty stuck.

Anyone got it working on breezy amd64?

---

### Post by sup on 2006-09-01
I am using gstreamer 0.10.X already, does work with 0.8 plugins? Because I cannot make apes to play, although I can get them to convert with pacpl (and libmac from morgoth repository)

---

