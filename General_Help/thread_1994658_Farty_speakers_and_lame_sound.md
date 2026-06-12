---
title: "Farty speakers and lame sound"
date: 2012-06-03
forum: General Help
---

### Post by samwillc on 2012-06-03
Hi everyone,

Although I am enjoying the new linux experience, one thing is holding back full enjoyment, and that is the amount of trouble I have had getting the sound working properly!

In windows, all I had to do was nip over to the realtek website, download the realtek HD drivers, and bingo, I had a little program in the taskbar that I could open and adjust the equalizer and do other things with the sound, it was just so simple.

Ubuntu and simple sound setup don't seem to go hand in hand at all. There's alsa, pulseaudio, and a massive myriad of sliders (I must have about 15 sliders for various volumes all doing what exactly?) and options which would have Stephen Hawking saying "sod this, I'm reinstalling windows!".

I have a logitech speaker set with a sub and a front left/right plugged into the headphones out on the back of the pc, so 2.1 sound in other words. My monitor is connected via HDMI but as far as I know, no sound goes between these two.

I really want to get this sorted as ubuntu 12.04  is a sweet OS and I love using it but this is quite annoying. I put on crowbar, and as you may know, the guitars are down tuned and there's a lot of bass, perfect testing material. The front left/right speakers sound like there's a farting mouse stuck inside even at quite low volume! I've tried banshee and rhythmbox and both have the same issue.

Now I'm so confused with this array of volume controls, would anyone suggest a complete removal of pulseaudio and start from the beginning with the sound? I am using the pulseaudio equalizer which seems to work but I can't figure out where this problem is coming from. All I know is that my sound used to sound great on win7, and now it sounds crap.

Or can I even install the realtek drivers that I used on win7? (the ones for linux though)

Any help or suggestions is more than appreciated!

Thanks.

Sam.

---

### Post by traditionalist on 2012-06-03
Go to "System Settings", "Sound",

[[IMG]http://img16.imageshack.us/img16/7568/sound001.th.png[/IMG]]("http://img16.imageshack.us/i/sound001.png/")

Check that everything there is set up correctly.

---

### Post by samwillc on 2012-06-03
Ok thanks.

I had options like that too, why is there an HDMI one?? The only HDMI I use connects the pc to the monitor. I chose 'analogue stero duplex' before.

This is what I've done so far. Removed alsa, removed pulseaudio. Now opening settings > sound looks like this:

[http://dl.dropbox.com/u/63070476/Screenshot%20from%202012-06-03%2011%3A42%3A32.png]("http://dl.dropbox.com/u/63070476/Screenshot%20from%202012-06-03%2011%3A42%3A32.png")

Tried banshee, stuck on the trusty crowbar album, cranked it up (for a short period before my neighbours kill me...) and lo and behold, no farting, nothing, just clear sound.

Of course it still sounds a bit crap because I need an equalizer, but I am trying to find out where along the line did these issues start to happen.

Sam.

---

### Post by traditionalist on 2012-06-03
Some people use the HDMI setups for sound.  Some monitors have speakers built in.

I use a logitech 2.1 setup . Don't bother with anything else. Great sound. Once you start messing with all sorts of stuff it gets confusing, and in my experience, rarely better.

You do realise that you have your sound output set to zero?  If you try to use very low amplitude signals the sound will be very poor.

---

### Post by samwillc on 2012-06-03
Thanks.

I am going through the steps here:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

and now have:

[http://dl.dropbox.com/u/63070476/Screenshot%20from%202012-06-03%2012%3A13%3A00.png]("http://dl.dropbox.com/u/63070476/Screenshot%20from%202012-06-03%2012%3A13%3A00.png")

(ignore the mode bit, I have reset that to 'analogue stereo duplex' - there is no option for 2.1 even though I have a sub? 4.1 includes a sub, but I have no rear speakers!)

Strangely, in banshee/youtube etc, I get sound, but on 'test sound' clicking on the front left or front right, I get no sound.

Sam.

---

### Post by traditionalist on 2012-06-03
Also, you should use the speaker output, not the headphone output;


[http://4.bp.blogspot.com/_6QR_qOso91Y/S_ZolTka23I/AAAAAAAAAZo/_OI4VXtjivc/s1600/example+sound+card.jpg](http://4.bp.blogspot.com/_6QR_qOso91Y/S_ZolTka23I/AAAAAAAAAZo/_OI4VXtjivc/s1600/example+sound+card.jpg)

---

### Post by traditionalist on 2012-06-03
I think you have your leads in the wrong output sockets, and also if you are using a 2.1 system, that is what you need to set up. 

Turn the sound down before testing!

---

### Post by samwillc on 2012-06-03
Thanks for the help so far, I really appreciate it!

So here's the update, got the camera out and uploaded to dropbox.

[http://dl.dropbox.com/u/63070476/P1230899.JPG](http://dl.dropbox.com/u/63070476/P1230899.JPG)

I had it plugged in to the green one bottom middle (says FRONT). I only did this because the jack from the logitech is also green so matched the colours and stuck it in! I see the top left greyish one says SPK (side), should it be in there instead??

There is only ONE lead from the logitech speakers, a 3.5mm jack. That goes into a little control thing on my desk where I can control the bass from. The bass speaker does not have its own lead to plug in. You can see the speaker in the photo on the left :)

Also, how do I configure ubuntu to use front/left/sub, there is no option for 2.1.

What I *think* is happening is that all the sound (including bass) is being sent only to the front/left making them fart like mad.

Sam.

---

### Post by traditionalist on 2012-06-03
Looks like the same system I use. It is a Logitech Z.2300

[http://forums.logitech.com/t5/image/serverpage/image-id/2826i8E52EF2278D197C0/image-size/original?v=mpbl-1&px=-1](http://forums.logitech.com/t5/image/serverpage/image-id/2826i8E52EF2278D197C0/image-size/original?v=mpbl-1&px=-1)

If you only have one lead then you can only use one socket of course.  If you set up for stereo the logitech systems split the signal automatically. For stereo output the jack needs to be in the green socket.  The sound needs to be set up for stereo.

back in a sec.........

OK. Mine is in the green socket;

[[IMG]http://img27.imageshack.us/img27/9391/examplesoundcard.jpg[/IMG]]("http://img27.imageshack.us/i/examplesoundcard.jpg/")

my sound settings are these;


[]("http://img715.imageshack.us/i/sound001.png/")

---

### Post by traditionalist on 2012-06-03
[[IMG]http://img715.imageshack.us/img715/7568/sound001.png[/IMG]](http://img715.imageshack.us/i/sound001.png/)

---

### Post by traditionalist on 2012-06-03
[[IMG]http://img715.imageshack.us/img715/2037/sound001j.th.png[/IMG]](http://img715.imageshack.us/i/sound001j.png/)


That should work perfectly, it does on my setup.

You  can choose loads of other things, 

[[IMG]http://img525.imageshack.us/img525/7568/sound001.th.png[/IMG]](http://img525.imageshack.us/i/sound001.png/)

but they are irrelevant here.

So, that should all be working now?

---

### Post by samwillc on 2012-06-03
I have no 'hardware' tab in my sound settings and using SPK socket or the green FRONT one seems to make no difference.

Enabling pulseaudio EQ has a dramatic effect on the sound, going to sound awesome once it works!

By the way, are you using pulseaudio EQ too?

Also, the little speaker icon in the top right is missing too! I think I may have not installed all the features of pulseaudio.

Sam.

---

### Post by traditionalist on 2012-06-03
> **samwillc said:**
> I have no 'hardware' tab in my sound settings and using SPK socket or the green FRONT one seems to make no difference.

Enabling pulseaudio EQ has a dramatic effect on the sound, going to sound awesome once it works!

By the way, are you using pulseaudio EQ too?

Sam.

No hardware tab????  

When you click on "Built in Audio" do you have a drop down box with a lot of choices in it?

You need to choose Analog Stereo Output from that box.

It is irritating me that your setup boxes are not the same......................

---

### Post by traditionalist on 2012-06-03
OK.  In this box on your screenshot, ( I have marked it with a red arrow), 

[[IMG]http://img191.imageshack.us/img191/5179/screenshotfrom201206031.png[/IMG]]("http://img191.imageshack.us/i/screenshotfrom201206031.png/")

you need to choose; Analog Stereo Output.  that should have sorted it.  Test that and see if it works properly.

No I don't use anything other than the Logitech setup. It has a digital processing setup built in. Adding more stuff would just deform the sound.

---

### Post by samwillc on 2012-06-03
Maybe getting somewhere:

[http://dl.dropbox.com/u/63070476/Screenshot%20from%202012-06-03%2013%3A09%3A36.png]("http://dl.dropbox.com/u/63070476/Screenshot%20from%202012-06-03%2013%3A09%3A36.png")

Now it seems I can ascess these mystery items that were in your hardware tab.

In pavucontrol, built in audio > proifle > BIG long list of stuff like in your screenshot, looks promising.

Why don't I have the same settings??

Sam.


*-------------------------------------------------*

!!ALSA Version !!------------  Driver version:     1.0.24 Library version:    1.0.25 Utilities version:  1.0.25

These numbers are supposed to be the same, something is not right. Will check this out and get back.

Sam.

---

### Post by traditionalist on 2012-06-03
> **samwillc said:**
> Maybe getting somewhere:

[http://dl.dropbox.com/u/63070476/Screenshot%20from%202012-06-03%2013%3A09%3A36.png](http://dl.dropbox.com/u/63070476/Screenshot%20from%202012-06-03%2013%3A09%3A36.png)

Now it seems I can ascess these mystery items that were in your hardware tab.

In pavucontrol, built in audio > proifle > BIG long list of stuff like in your screenshot, looks promising.

Why don't I have the same settings??

Sam.

I have no idea why your settings are different, possibly because you have pulse audio and other stuff installed?  Doesn't matter, we are getting there slowly but surely.

have you tested that?

---

### Post by samwillc on 2012-06-03
Let me get back to you (See my edit above).

I think something is wrong in my setup. Either pulseaudio or alsa. I'll do a full reinstall if I have too! I need decent sound :D

Sam.

---

### Post by traditionalist on 2012-06-03
You do not want " Analogue stereo duplex", you want "Analog Stereo Output".

---

### Post by traditionalist on 2012-06-03
> **samwillc said:**
> Let me get back to you (See my edit above).

I think something is wrong in my setup. Either pulseaudio or alsa. I'll do a full reinstall if I have too! I need decent sound :D

Sam.

It doesn't matter. If you can get "Analog Stereo Output" into that box you should be good to go. You can worry about the other stuff later.

In point of fact I have "Analog Stereo Output + Digital Stereo (IEC958 ) Input"  in that box. But just "Analog Stereo Output" will work fine.

---

### Post by samwillc on 2012-06-03
> **traditionalist said:**
> You do not want " Analogue stereo duplex", you want "Analog Stereo Output".

Unsurprisingly after the way this is going, I can tell you that I have no 'Analogue stereo output' option.

I am going through the troubleshooting trying to get the sound back to normal so at least I have the same options as you, that would make your job a whole lot easier trying to explain things and we're looking at different menus!

Sam.

---

### Post by traditionalist on 2012-06-03
> **samwillc said:**
> Unsurprisingly after the way this is going, I can tell you that I have no 'Analogue stereo output' option.

I am going through the troubleshooting trying to get the sound back to normal so at least I have the same options as you, that would make your job a whole lot easier trying to explain things and we're looking at different menus!

Sam.

What options do you have when you choose the drop down arrow from that box?

---

### Post by samwillc on 2012-06-03
Still trying to find out why I have no hardware tab.

The dropdown  for MODE as is shows:

Analogue stereo duplex
Analogue surround 4.0 Output
Analogue surround 5.1 Output
Analogue surround 5.0 Output
Analogue surround 7.1 Output
Analogue surround 4.1 Output

(I would take a screenshot but that doesn't seem to work with the dropdown open)

Sam.

---

### Post by samwillc on 2012-06-03
> **traditionalist said:**
> 

That should work perfectly, it does on my setup.

You  can choose loads of other things, 

[[IMG]http://img525.imageshack.us/img525/7568/sound001.th.png[/IMG]]("http://img525.imageshack.us/i/sound001.png/")

but they are irrelevant here.

So, that should all be working now?

This is seriously getting on my nerves, I can't find anywhere why your sound settings would be different from mine??

All I could find was this:
**Ubuntu 12.04 doesn't have a hardware tab, the settings have merged and there are fewer options now. &#8211; [Sman789]("http://askubuntu.com/users/38510/sman789") [May 18 at 13:28]("http://askubuntu.com/questions/138397/volume-control-out-of-phase-with-actual-volume-and-alsamixer#comment165748_138787")**

I am using:

Alsa driver 1.0.24
Fresh install ubuntu 12.04
Kernel Linux 3.2.0-24-generic

And still, I have no hardware tab and no way of selecting anything other than 'analogue stereo duplex'.

Did you install anything else to do with sound??

Sam.

---

### Post by traditionalist on 2012-06-03
> **samwillc said:**
> This is seriously getting on my nerves, I can't find anywhere why your sound settings would be different from mine??

All I could find was this:
**Ubuntu 12.04 doesn't have a hardware tab, the settings have merged and there are fewer options now. – [Sman789]("http://askubuntu.com/users/38510/sman789") [May 18 at 13:28]("http://askubuntu.com/questions/138397/volume-control-out-of-phase-with-actual-volume-and-alsamixer#comment165748_138787")**

I am using:

Alsa driver 1.0.24
Fresh install ubuntu 12.04
Kernel Linux 3.2.0-24-generic

And still, I have no hardware tab and no way of selecting anything other than 'analogue stereo duplex'.

Did you install anything else to do with sound??

Sam.

No, it is just a normal installation of 12.04.  You MUST be able to choose the hardware. I can't think why you shouldn't be able to,. I will have a poke around and try to find a reason. If I find anything I will get back to you.

---

### Post by traditionalist on 2012-06-03
I don't have an alsa driver

[http://linux.softpedia.com/get/Programming/Libraries/ALSA-driver-164.shtml](http://linux.softpedia.com/get/Programming/Libraries/ALSA-driver-164.shtml)

This may be the problem here?

---

### Post by samwillc on 2012-06-03
> **traditionalist said:**
> I don't have an alsa driver

[http://linux.softpedia.com/get/Programming/Libraries/ALSA-driver-164.shtml](http://linux.softpedia.com/get/Programming/Libraries/ALSA-driver-164.shtml)

This may be the problem here?

Thanks.

I downloaded the newer driver earlier but didn't know how to actually install it or whether I would have to also faff about with the kernel?!

How do you get sound without the driver?

I thought the pulseaudio EQ had something to do with it but that's not installed at the mo.

Sam.

---

### Post by traditionalist on 2012-06-03
> **samwillc said:**
> 

How do you get sound without the driver?

Sam.

The alsa driver is a replacement driver. The system has its own drivers. I never found the need for any others.

If you want to install various drivers etc, then it is best to get the basic system running first as it is much easier to troubleshoot. You can get a lot of stuff at the Ubuntu Software Center, and it will install the stuff for you.

[[IMG]http://img580.imageshack.us/img580/5117/ubuntusoftwarecenter001.th.png[/IMG]]("http://img580.imageshack.us/i/ubuntusoftwarecenter001.png/")

---

### Post by samwillc on 2012-06-03
I think you're right.

This has possibly been my most unproductive day ever and I could do with moving on!

It doesn't explain the hardware tab difference though. I have read since that the hardware tab has been phased out, so confused as to how you've got it!

Maybe I could uninstall alsa and pulseaudio and start again from scratch, another day.

Sam.

---

### Post by traditionalist on 2012-06-03
[QUOTE=samwillc;11994622

<SNIP>
Maybe I could uninstall alsa and pulseaudio and start again from scratch, another day.

Sam.[/QUOTE]

Up to you.  In your position I would be considering a new install of Ubuntu. Don't tweak anything at all until you have the basic system running properly.  It produces great sound without any tweaks.

---

### Post by samwillc on 2012-06-03
I did a clean install earlier after the speakers started making a high pitched noise that I couldn't stop! I changed some settings in pulseaudio volume control, the thing people rave about in the reviews?! Didn't work quite so well for me!

Of course, with the clean install comes alsa and pulseaudio! However, I haven't installed pulseaudio volume control or pulseaudio equalizer, both have caused me problems.

Sound is decent enough now. The quality of the sound is subjective as I like to take out the middle and have particular sound settings, and for that I need an EQ.

The built in EQ in banshee is BAD, I mean really bad! And it wouldn't help with vids I watch on youtube as it needs to be global. The standard sound without any tweaks I think sounds a bit lacking. I'm a bit stuck for ideas unless another global EQ comes along.

Sam.

---

### Post by traditionalist on 2012-06-03
> **samwillc said:**
> 

>SNIP>

 The standard sound without any tweaks I think sounds a bit lacking. I'm a bit stuck for ideas unless another global EQ comes along.

Sam.

You can try this if you like, a friend off mine reckons it is great;

[http://www.xmms.org/](http://www.xmms.org/)

[http://www.xmms.org/effect.php](http://www.xmms.org/effect.php)

have not tried it myself.

For "Bleeding Edge" stuff you need to be looking at the audiophile specialists;

[http://www.head-fi.org/t/316477/audiophile-linux-software](http://www.head-fi.org/t/316477/audiophile-linux-software)

---

### Post by samwillc on 2012-06-03
Thanks for the links.

Not sure they will afford a global EQ though.

I only want to set it up once, from then it would handle sound from any source i.e mp4,  mp3, youtube...

Pulseaudio is close but appears to have some issues. The logitech setup is a beast for such small speakers and a sub. It demands a decent EQ!

Sam.

---

### Post by samwillc on 2012-06-04
UPDATE:

I've just noticed that when my logitech speakers are turned all the way down via the control, I can still hear the music faintly!

Maybe naive of me but I always thought turning the volume down should turn it off. I wonder if a volume is set at over 100% somewhere on the system maybe causing to much input to the speakers? Just a guess. Not even sure that's possible.

Sam.

---

### Post by nicolasforum89 on 2012-06-04
Thanks for the links.

---

### Post by traditionalist on 2012-06-04
> **samwillc said:**
> UPDATE:

I've just noticed that when my logitech speakers are turned all the way down via the control, I can still hear the music faintly!

Maybe naive of me but I always thought turning the volume down should turn it off. I wonder if a volume is set at over 100% somewhere on the system maybe causing to much input to the speakers? Just a guess. Not even sure that's possible.

Sam.

Audio equipment can be very fussy indeed about signal levels.  Too high an input into the main amplifier can cause problems, and there are lots of other things.  Turning the volme down does not turn off an amplifier, it merely reduces signal levels.

---

### Post by samwillc on 2012-06-04
But I shouldn't be able to still hear it.

All I know is that with win7/realtek HD audio driver I had excellent sound quality with a global equalizer. With 12.04, the sound is not great!

I think it is pulseaudio equalizer that is crapping it up. As soon as I enable that, sound goes to hell. So I am stuck without it which sounds to me like the equivalent setting on any normal equalizer set to 'flat'.

The sound is clear now, don't get me wrong, it's just not how I'd like it to sound. Even on a cheapo £5 stereo there would be a choice of 'rock', 'pop' or 'classical'. I can't believe this is not built in. Some people may not need it, but others do, and the add-ons to achieve this are nothing more than useless.

There is no point having an equalizer on each program (besides the banshee one is DREADFUL!), only needs a global one. If I had more coding skills, I would quit moaning and write one!

I am going to add a screenshot of the realtek screen from my wifes win7 machine and upload. We have the same speaker system, except hers sounds good, lol.

Sam.

---

### Post by samwillc on 2012-06-04
Ok, here we go, awwwww how I miss the realtek HD!!

[IMG]http://dl.dropbox.com/u/63070476/realtek-1.png[/IMG]

See how easy it is! You can select individual speakers, turn them on/off....

[IMG]http://dl.dropbox.com/u/63070476/realtek-2.png[/IMG]

And behold, a global equalizer, that works!

5 mins and you're done, with great sounds whatever setup you're using. Pulseaudio should take a long look at something like this. I never had any problems whatsoever on a variety of different machines with different speaker systems too.

Sam.

---

### Post by samwillc on 2012-06-04
With a lot of tweaking it appears the bass sliders on the left may be the culprit. This gives me pretty good sound, and with a few restarts, the settings persist and no farting thus far:

[IMG]http://dl.dropbox.com/u/63070476/Screenshot%20from%202012-06-04%2013%3A21%3A06.png[/IMG]

Maybe the key is to keep all the bass ones at zero (0) or below. Treble end is fine.

Sam.

---

