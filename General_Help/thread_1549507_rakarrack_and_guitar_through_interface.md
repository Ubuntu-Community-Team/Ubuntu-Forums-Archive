---
title: "rakarrack and guitar through interface??"
date: 2010-08-09
forum: General Help
---

### Post by oleink on 2010-08-09
Hey I got rakarrack and have tried hooking up my guitar from usb interface but I can't get it to work with rakarrack (no effects on guitar.)  I really gotta get this working

---

### Post by oleink on 2010-08-09
anyone I need that to work

---

### Post by transmogrifox on 2010-08-09
Hmmm... could be a number of things in the path.

Most likely is the volume on your sound card's internal mixer isn't turned up.  The best way I know to really get all the controls is to open a terminal and type 
```
alsamixer
```
enter

It will give you a simple interface to adjust all the volumes onboard your mixer as well as software volume control. Navigate the controls with the left/right arrow keys, and volume adjustments with up/down keys.  Select view with tab key.

In order to give the community a chance at something better than a stab in the dark more information is needed:
What sound card?
Does it work without jack running?
How is jack configured with this sound card?
Do you see the VU bars bouncing on rakarrack?  If not then you aren't getting any signal to the input and need to look for a mic or line input level to turn up in alsamixer.
If you see VU bars bouncing, then you need to look for an output level to turn up.

Is jackd running properly?  
Do you get sound if you route the output of a media player (like totem) into Rakarrack?

In this case I don't think software version has anything to do with your problem, but often in posts like this it helps to mention a software version, or if you have installed it from a PPA, who's PPA...etc.  The more information you can give, the more help some kind-hearted soul can offer. ;)

Finally have you read the Help provided with Rakarrack?
Here is a good start:
[http://rakarrack.sourceforge.net/general.html](http://rakarrack.sourceforge.net/general.html)
The same information can be found by pressing the "F1" key, but in this case you may find the troubleshooting linux audio links helpful to click from within your web browser.

And another worthwhile read:
[http://rakarrack.sourceforge.net/hardware.html](http://rakarrack.sourceforge.net/hardware.html)

In the event noise and/or sound quality plague you after you have got sound to come out.

---

### Post by oleink on 2010-08-10
> **transmogrifox said:**
> Hmmm... could be a number of things in the path.

Most likely is the volume on your sound card's internal mixer isn't turned up.  The best way I know to really get all the controls is to open a terminal and type 
```
alsamixer
```
enter

It will give you a simple interface to adjust all the volumes onboard your mixer as well as software volume control. Navigate the controls with the left/right arrow keys, and volume adjustments with up/down keys.  Select view with tab key.

In order to give the community a chance at something better than a stab in the dark more information is needed:
What sound card?
Does it work without jack running?
How is jack configured with this sound card?
Do you see the VU bars bouncing on rakarrack?  If not then you aren't getting any signal to the input and need to look for a mic or line input level to turn up in alsamixer.
If you see VU bars bouncing, then you need to look for an output level to turn up.

Is jackd running properly?  
Do you get sound if you route the output of a media player (like totem) into Rakarrack?

In this case I don't think software version has anything to do with your problem, but often in posts like this it helps to mention a software version, or if you have installed it from a PPA, who's PPA...etc.  The more information you can give, the more help some kind-hearted soul can offer. ;)

Finally have you read the Help provided with Rakarrack?
Here is a good start:
[http://rakarrack.sourceforge.net/general.html](http://rakarrack.sourceforge.net/general.html)
The same information can be found by pressing the "F1" key, but in this case you may find the troubleshooting linux audio links helpful to click from within your web browser.

And another worthwhile read:
[http://rakarrack.sourceforge.net/hardware.html](http://rakarrack.sourceforge.net/hardware.html)

In the event noise and/or sound quality plague you after you have got sound to come out.

Thanks for the reply.  Its the audio interface uca222 (behringer).  The sound is fine on it because I'm using mixer plugged into the interface and have recorded through it but for some reason I can't find a way for it to sync up with rakarrack.  I checked out the links you gave me and will try a few of the tips in there and get back to you.  (PS yes I do try to connect capture to rakarrack)  I have qjackctl running fine besides the fact I cannot use the "realtime" box

---

### Post by transmogrifox on 2010-08-10
Did you record through it using jack or was the recording into something like Audacity without jack running?

I have a UCA202 -- very similar.  One interface was the USB Audio, and another called USB Audio CODEC.  It seems I remember it worked with either selected as an input or output in jack configuration settings, but you can't select the same thing for input and output.  My setting as I remember is USB Audio is input, USB Audio CODEC is output. 

Attempting to use a different sound card for input and output can be problematic, so anything incoming or outgoing in your jack configuration needs to be the UCA222.

The UCA202 says it supports several sample rates, but mine works the best at its maximum, 48kHz.  It seems I get some instability (jack crashing) with 44.1kHz samplerate.

Here is another good read:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

And some more useful information about using jack with qjackctl:
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

Again, I'm just stabbing in the dark, maybe something will turn on a light bulb :)

A common misconception I see is the idea that qjackctl is a necessary program.  It is only a front end utility that allows you to configure jackd and provides a nifty graphical interface for making connections.

If you have configured your sound card to work and qjackctl is able to start jack successfully, then it has saved a valid configuration in your home folder .jackdrc.  If this file contains a valid configuration for the desired sound card, you can start Rakarrack without qjackctl running and Rakarrack will cause jackd to start.

In Rakarrack preferences->Jack, there is an option to autoconnect to a list of ports on startup. The list for input and output is populated according to what jack ports are available for connection.  You can select the ports you want Rakarrack to connect to when it starts.  Hold down the Ctrl key and mouse click to select multiple for stereo inputs.

The next time you start Rakarrack, it will automagically connect to those ports.  In the end of it all, you will be able to start Rakarrack and it will launch jackd (if it's not already running) and connect itself to the inputs/outputs you selected in the preferences.

If you don't have sound coming out after that, then the problem has nothing to do with rakarrack, but everything to do with your jack configuration or alsamixer settings.

Finally it may be a good idea to visit the jackaudio site
[http://jackaudio.org/](http://jackaudio.org/)

And learn what jack is, what it's for, and why we use it in Linux.  I would start with the FAQ after reading the basic description on the home page.

Again if you can give more information about your jack settings, it will help.

For example:
```
cat ~/.jackdrc
cat /etc/security/limits.d/audio.conf
```
And paste the output here.

It would be helpful if you answer my question about the VU bars in Rakarrack.  When you connect capture to Rakarrack and play, do the VU bars indicate signal going through?  Then of course, Rakarrack output needs to be connected to a valid System output amplified to speakers or headphones.

Your mentioning that you can't launch jack without RT option makes me think you haven't given your user the privileges to do rt audio yet. Edit (as root/sudo) /etc/security/limits.d/audio.conf and uncomment these lines:
@audio   -  rtprio     99
@audio   -  memlock    unlimited

...log out, then log back in.

---

### Post by oleink on 2010-08-10
> **transmogrifox said:**
> Did you record through it using jack or was the recording into something like Audacity without jack running?

I have a UCA202 -- very similar.  One interface was the USB Audio, and another called USB Audio CODEC.  It seems I remember it worked with either selected as an input or output in jack configuration settings, but you can't select the same thing for input and output.  My setting as I remember is USB Audio is input, USB Audio CODEC is output. 

Attempting to use a different sound card for input and output can be problematic, so anything incoming or outgoing in your jack configuration needs to be the UCA222.

The UCA202 says it supports several sample rates, but mine works the best at its maximum, 48kHz.  It seems I get some instability (jack crashing) with 44.1kHz samplerate.

Here is another good read:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

And some more useful information about using jack with qjackctl:
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

Again, I'm just stabbing in the dark, maybe something will turn on a light bulb :)

A common misconception I see is the idea that qjackctl is a necessary program.  It is only a front end utility that allows you to configure jackd and provides a nifty graphical interface for making connections.

If you have configured your sound card to work and qjackctl is able to start jack successfully, then it has saved a valid configuration in your home folder .jackdrc.  If this file contains a valid configuration for the desired sound card, you can start Rakarrack without qjackctl running and Rakarrack will cause jackd to start.

In Rakarrack preferences->Jack, there is an option to autoconnect to a list of ports on startup. The list for input and output is populated according to what jack ports are available for connection.  You can select the ports you want Rakarrack to connect to when it starts.  Hold down the Ctrl key and mouse click to select multiple for stereo inputs.

The next time you start Rakarrack, it will automagically connect to those ports.  In the end of it all, you will be able to start Rakarrack and it will launch jackd (if it's not already running) and connect itself to the inputs/outputs you selected in the preferences.

If you don't have sound coming out after that, then the problem has nothing to do with rakarrack, but everything to do with your jack configuration or alsamixer settings.

Finally it may be a good idea to visit the jackaudio site
[http://jackaudio.org/](http://jackaudio.org/)

And learn what jack is, what it's for, and why we use it in Linux.  I would start with the FAQ after reading the basic description on the home page.

Again if you can give more information about your jack settings, it will help.

For example:
```
cat ~/.jackdrc
cat /etc/security/limits.d/audio.conf
```
And paste the output here.

It would be helpful if you answer my question about the VU bars in Rakarrack.  When you connect capture to Rakarrack and play, do the VU bars indicate signal going through?  Then of course, Rakarrack output needs to be connected to a valid System output amplified to speakers or headphones.

Your mentioning that you can't launch jack without RT option makes me think you haven't given your user the privileges to do rt audio yet. Edit (as root/sudo) /etc/security/limits.d/audio.conf and uncomment these lines:
@audio   -  rtprio     99
@audio   -  memlock    unlimited

...log out, then log back in.

yeah I can record through qjackctl but for some reason even pluging the capture into the rakarrack input doesn't work.  No indication it's working (in answer to your question about the VU bars)  I'm running at 44800khz 128frames/period and 3 periods a buffer.

PS about the realtime box:
I've already adjusted the limits.conf file and added

@audio - nice -10
along with those

---

### Post by oleink on 2010-08-10
> **transmogrifox said:**
> 
For example:
```
cat ~/.jackdrc
cat /etc/security/limits.d/audio.conf
```
And paste the output here.



jordan@jordan-laptop:~$ cat ~/.jackdrc
/usr/bin/jackd -r -dalsa -dhw:2 -r48000 -p128 -n3
jordan@jordan-laptop:~$ cat /etc/security/limits.d/audio.conf
# generated by jackd's postinst.
#
# Do not edit this file by hand, use
#
#    dpkg-reconfigure -p high jackd
#
# instead.
@audio   -  rtprio     99
@audio   -  memlock    unlimited
#@audio   -  nice      -19
jordan@jordan-laptop:~$

---

### Post by cchhrriiss121212 on 2010-08-10
Are you part of the audio group?

---

### Post by oleink on 2010-08-10
> **cchhrriiss121212 said:**
> Are you part of the audio group?

No i dont even know about it.  Haven't been using linux very long

---

### Post by -kg- on 2010-08-10
I know next to nothing about your issues (though I also play guitar), but I just noticed something from your profile:

> Ubuntu Development Release 

Are you currently running the (Maverick) Development Release?  Could it be a bug?

---

### Post by oleink on 2010-08-10
> **-kg- said:**
> I know next to nothing about your issues (though I also play guitar), but I just noticed something from your profile:



Are you currently running the (Maverick) Development Release?  Could it be a bug?

No actually I switched back to 10.04.  I gotta go change that haha

---

### Post by cchhrriiss121212 on 2010-08-10
> **oleink said:**
> No i dont even know about it.  Haven't been using linux very long
Well that is why your rt jack is not working. Go to the Users&Groups app under the system menu and add your user account to the audio group. You should get better performance now, but I'm not sure whether it will be related to your rakarrack issue.

---

### Post by oleink on 2010-08-10
> **cchhrriiss121212 said:**
> Well that is why your rt jack is not working. Go to the Users&Groups app under the system menu and add your user account to the audio group. You should get better performance now, but I'm not sure whether it will be related to your rakarrack issue.

Oh wait no I am part of the audio group so that didn't help... Thanks for your response though

---

### Post by oleink on 2010-08-10
I can get realtime checked if I run in root.  It is strange because I am part of the audio group but it says I am not when I am not in root...?

---

### Post by transmogrifox on 2010-08-10
thanks for posting the .jackdrc file:

```
usr/bin/jackd -r -dalsa -dhw:2 -r48000 -p128 -n3
```

One possible problem is you're using default for input & output.  I can't say anything for sure, but I do have some guesses at things that may help:

1) Instead of using default for input & output on hw:2, go to the Input Device and Output Device lists in setup and click on the ">" button to select a specific interface on that card.  For example, USB Audio for input, USB Audio CODEC for output.  I suspect jack may be trying to use the same buffers for input and output.
2) -n3 is not correct.  It should be 2 periods per buffer on this card. JACK documentation indicates the ability to use more than 2 is a work-around for certain hardware.  Basically this means one period latency to get an input from the audio card, and one period latency to push it out the door.  Most pro audio interfaces don't need any extra time for this process.
3) -p128 is risky without RT working.  I suggest trying 512 frames per period or even 1024 just to get it working.  You can fine tune performance after you have resolved the "it's not working" problem. That is another can of worms.

Actually I had a real problem with this RT issue on my Linux Mint box (which is Ubuntu 10.04 with frills, so it has the same bugs).  I have never taken the time to debug it because I use Sidux on another partition in a really minimalistic mode for my studio environment...and everything works perfectly as expected there.  However, at least I can get sound in & out on the LM box.

Another thing that is good to try is route capture to playback channels directly and see if you can send sound straight through.  I suspect you're having a problem with Jack.  The idea is to start small and work up.  Once you eliminate jack as a problem and you're getting audio into and out of your computer correctly, then you can start with the software to process the audio.

When you start jack, look at the messages for xruns.  If the system can't keep up with such a low latency setting then you will basically have a frozen system as far as audio goes.  I have had times when it's so bad it doesn't even report xruns.

---

### Post by oleink on 2010-08-10
> **transmogrifox said:**
> thanks for posting the .jackdrc file:

```
usr/bin/jackd -r -dalsa -dhw:2 -r48000 -p128 -n3
```

One possible problem is you're using default for input & output.  I can't say anything for sure, but I do have some guesses at things that may help:

1) Instead of using default for input & output on hw:2, go to the Input Device and Output Device lists in setup and click on the ">" button to select a specific interface on that card.  For example, USB Audio for input, USB Audio CODEC for output.  I suspect jack may be trying to use the same buffers for input and output.
2) -n3 is not correct.  It should be 2 periods per buffer on this card. JACK documentation indicates the ability to use more than 2 is a work-around for certain hardware.  Basically this means one period latency to get an input from the audio card, and one period latency to push it out the door.  Most pro audio interfaces don't need any extra time for this process.
3) -p128 is risky without RT working.  I suggest trying 512 frames per period or even 1024 just to get it working.  You can fine tune performance after you have resolved the "it's not working" problem. That is another can of worms.

Actually I had a real problem with this RT issue on my Linux Mint box (which is Ubuntu 10.04 with frills, so it has the same bugs).  I have never taken the time to debug it because I use Sidux on another partition in a really minimalistic mode for my studio environment...and everything works perfectly as expected there.  However, at least I can get sound in & out on the LM box.

Another thing that is good to try is route capture to playback channels directly and see if you can send sound straight through.  I suspect you're having a problem with Jack.  The idea is to start small and work up.  Once you eliminate jack as a problem and you're getting audio into and out of your computer correctly, then you can start with the software to process the audio.

When you start jack, look at the messages for xruns.  If the system can't keep up with such a low latency setting then you will basically have a frozen system as far as audio goes.  I have had times when it's so bad it doesn't even report xruns.

I got it to work but only in root.  I've got real time box checked now and can go at 8msec with no xruns.  I set it to 3 buffers.  Problem with # one I have guitar sound going in it just wasn't working with rakarrack

---

### Post by transmogrifox on 2010-08-11
> I got it to work but only in root. I've got real time box checked now and can go at 8msec with no xruns. I set it to 3 buffers. Problem with # one I have guitar sound going in it just wasn't working with rakarrack
How do you know you had sound going in?  Did you record in the same session to some other jack device or another FX unit?  It seems particularly like a twilight zone mystery if it works as root :(  The only thing I could think could cause that is if jack was being run as root and Rakarrack was being run as normal user, or vice versa.  Were you launching qjackctl with sudo, or launching Rakarrack with sudo?  

This ubuntu and jackd only working as root even when things appear to be properly configured... :-(  This is where I gave up on Linux Mint and stuck with Debian unstable (Sid).

Maybe this thread will be of some value
[http://ubuntuforums.org/showthread.php?t=1031815&page=3](http://ubuntuforums.org/showthread.php?t=1031815&page=3)

Now I am out of ideas.  At least now you know you can get it to work as root, even if that isn't the optimal solution.

I still think you should try to run with -n2 instead of -n3.  You can get down to 5ms latency w/ 128 frames & 2 periods with the UCA222.

Perhaps somebody who knows something will chime in and give us both a morsel of good fortune :-)

---

### Post by cchhrriiss121212 on 2010-08-11
> **oleink said:**
> I can get realtime checked if I run in root.  It is strange because I am part of the audio group but it says I am not when I am not in root...?
Don't ever run things as root, trust me you will end up with more problems down the line.
There are 2 possible reasons why jack will not run with rt:
You did not edit and save the audio.conf file correctly
You are not part of the right group

Seeing as you have done these, I would recommend changing the lines in the .conf file from @audio to @jordan.

---

### Post by oleink on 2010-08-11
> **transmogrifox said:**
> How do you know you had sound going in?  Did you record in the same session to some other jack device or another FX unit?  It seems particularly like a twilight zone mystery if it works as root :(  The only thing I could think could cause that is if jack was being run as root and Rakarrack was being run as normal user, or vice versa.  Were you launching qjackctl with sudo, or launching Rakarrack with sudo?  

This ubuntu and jackd only working as root even when things appear to be properly configured... :-(  This is where I gave up on Linux Mint and stuck with Debian unstable (Sid).

Maybe this thread will be of some value
[http://ubuntuforums.org/showthread.php?t=1031815&page=3](http://ubuntuforums.org/showthread.php?t=1031815&page=3)

Now I am out of ideas.  At least now you know you can get it to work as root, even if that isn't the optimal solution.

I still think you should try to run with -n2 instead of -n3.  You can get down to 5ms latency w/ 128 frames & 2 periods with the UCA222.

Perhaps somebody who knows something will chime in and give us both a morsel of good fortune :-)

actually no I couldn't get rakarrack to start without being in root either.  The reason I knew my input was working was I recorded one guitar track clean before I even tried rakarrack

---

### Post by oleink on 2010-08-11
> **cchhrriiss121212 said:**
> Don't ever run things as root, trust me you will end up with more problems down the line.
There are 2 possible reasons why jack will not run with rt:
You did not edit and save the audio.conf file correctly
You are not part of the right group

Seeing as you have done these, I would recommend changing the lines in the .conf file from @audio to @jordan.

Good point thanks I'll give it a shot

---

### Post by oleink on 2010-08-11
> **cchhrriiss121212 said:**
> Don't ever run things as root, trust me you will end up with more problems down the line.
There are 2 possible reasons why jack will not run with rt:
You did not edit and save the audio.conf file correctly
You are not part of the right group

Seeing as you have done these, I would recommend changing the lines in the .conf file from @audio to @jordan.

I just double checked my audio.conf file because i knew my limits.conf file was set up right and found out somehow my rtprio got #(commented) out.  qjackctl now works without being root

---

### Post by transmogrifox on 2010-08-11
Yeah, I agree the suggestion to narrow the scope to @jordan is a good suggestion.  Another thing you can do is add jordan, the user (specifically), then it will not depend on group inheritance.  If you try that and it works, just keep in mind there is still a bug hiding somewhere, because the configuration you have already implemented is the way it works in most instances & most computers.  Sometimes such bugs spring out because the media used to install the system (CD, DVD, USB) had corrupted data.  For future reference it is a good idea to run the check sum (using the SHA or MD5 sum provided with the iso).  This is assuming you didn't.  I make that assumption because I myself am lazy and don't bother unless I have problems later on, even though I know better :).

Do let me know if you can narrow it down to Rakarrack specifically (for example if things work properly for all other applications you use in JACK, but Rakarrack does not).  The fact that it works as root makes me think it is not a Rakarrack bug, but rather something is bad in the system.

---

### Post by oleink on 2010-08-11
> **transmogrifox said:**
> Yeah, I agree the suggestion to narrow the scope to @jordan is a good suggestion.  Another thing you can do is add jordan, the user (specifically), then it will not depend on group inheritance.  If you try that and it works, just keep in mind there is still a bug hiding somewhere, because the configuration you have already implemented is the way it works in most instances & most computers.  Sometimes such bugs spring out because the media used to install the system (CD, DVD, USB) had corrupted data.  For future reference it is a good idea to run the check sum (using the SHA or MD5 sum provided with the iso).  This is assuming you didn't.  I make that assumption because I myself am lazy and don't bother unless I have problems later on, even though I know better :).

Do let me know if you can narrow it down to Rakarrack specifically (for example if things work properly for all other applications you use in JACK, but Rakarrack does not).  The fact that it works as root makes me think it is not a Rakarrack bug, but rather something is bad in the system.

It randomly started working and I've tested multiple times to make sure it wouldnt stop working again.  Hopefully it continues working I'm going to mark this as solved even though I'm slightly uneasy about it

---

### Post by transmogrifox on 2010-08-11
Might it have started working as a result of a reboot? Strange :/

---

### Post by oleink on 2010-08-11
> **transmogrifox said:**
> Might it have started working as a result of a reboot? Strange :/

No cause it'd been happening for days and I'd restarted my computer each day.

---

