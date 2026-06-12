---
title: "Just installed US 9.10 - Initial thoughts and questions"
date: 2010-03-13
forum: General Help
---

### Post by kazakore on 2010-03-13
Hi.

Almost complete Newbie to Linux but have finally got around to installing Ubuntu Studio on my laptop. Main use is for music production, using Renoise, my DAW of choice (and one of only a few on Linux, even though it's not free or open source.)

Anyway going to try and keep questions and thoughts to one thread for neatness for now.


First thing I noticed it there doesn't seem to be a single Theme in the basic package I really think works well. The Ubuntu Studio one isn't too bad but don't like the missing symbols of the Minimize/Maximize/Close buttons. Currently running ClearLooks after having a play with a couple of the others and either some text looked horrible/blurry or just didn't seem neat. Not sure I really like it but seems the least objectionable so far...

Mouse (well touchpad) sensitivity was far too high! Have managed to adjust this to usable although still not quite how i would like it. Acceleration setting works but Sensitivity seems to do nothing.

More irritatingly I can find no way to adjust the mouse wheel (well trackpad scroll) speed. This is FAR to fast! Also missing a setting which is really helpful in WinXP where you get to the end of the pad and it carries on scrolling as long as you hold pressure on the pad. Is it possible to adjust the speed and have this setting?

Had a lot of initial problems with the wireless adapter. Gave up initially and went back to my Windows installation and found that it had been disabled in Device Manager in there, even though I was using it only just before installing Linux. At least re-enabling it there allowed me to actually be able to scan with it in Linux. Setting up was a royal pain in the **** though, as ESSID wouldn't change (according to iwconfig command) unless I restart the whole system inbetween. Eventually managed to get it up and 
running though at least.

But while doing so had to often go into Network Settings. Each time I did, after the first time, clicking on the keys to enable editing mode would not automatically focus the password entry box, making it really annoying when I have to do it again and again trying things, attempting to get the system working. Just having it focus on the box to enter the password after clicking the keys would greatly help alleviate the stress of sorting it out!

Is there a keyboard shortcut to open Terminal (I know I should search, this should be easy to find, but as I'm here anyway...)??

Why does Backspace in Firefox not take me Back a page? I am very used to this operation and use it all the time! Is it possible to set it to work like this? I thought it did very briefly yesterday but maybe I'm confused...


Sorry about the n00b questions and comments. Hopefully I learn to love this OS and it will turn out to be a rock solid system for live performances in the future.

---

### Post by kazakore on 2010-03-13
Should Jack not be installed and working as standard? I know PulseAudio has overtaken it as the default on 9.10 but I need Jack for Renoise.

Typing "jackd -d alsa -help" (as I want to use Jack with ALSA) as told to on this page: [http://tutorials.renoise.com/wiki/Linux_FAQ](http://tutorials.renoise.com/wiki/Linux_FAQ)

Give me this message: "The program 'jackd' is currently not installed.  You can install it by typing:
sudo apt-get install jackd"

Sudo apt-get install jackd doesn't work as it can't find it and manually searching the repository and I couldn't find Jack either.

---

### Post by kazakore on 2010-03-13
OK set backspace in FF to be Back so that's sorted.

Also added a keyboard shortcut to open Terminal so that's another off the list.

But what is the deal with Jack now?

And how do I get Adobe Acrobat Reader plugin for Firefox to install? Downloads as a .bin file but no information of what to do with it.

---

### Post by phillw on 2010-03-13
Re: Renoise

As it is proprieatory software, I reckon you'd be best placed asking on their forum --> [http://www.renoise.com/board/](http://www.renoise.com/board/)

From having had a read of it, they seem very linux friendly and would be more used to implementing it with Ubuntu.

For pdf reader in FFox, go into the "Add-Ons" and add it - no need to download stuff, It'll go get it for you (type in pdf into the search area)

More information on pdf & FFox can be found here --> [http://support.mozilla.com/en-US/kb/opening+PDF+files+within+Firefox](http://support.mozilla.com/en-US/kb/opening+PDF+files+within+Firefox)


Regards,

Phill.

---

### Post by kazakore on 2010-03-13
> **phillw said:**
> Re: Renoise

As it is proprieatory software, I reckon you'd be best placed asking on their forum --> [http://www.renoise.com/board/](http://www.renoise.com/board/)

From having had a read of it, they seem very linux friendly and would be more used to implementing it with Ubuntu.

Yeah I know they are quite Linux friendly, about the only commercial music software with decent Linux support. Most people on there (and most music based sites) are running 8.04 or older though, for various reasons, and Renoise requires Jack, which doesn't seem to be packaged with Ubuntu any more. So it was more a specific question of getting Jack in 9.10 rather than a Renoise question.

> For pdf reader in FFox, go into the "Add-Ons" and add it - no need to download stuff, It'll go get it for you (type in pdf into the search area)

Tried adding it from the Mozilla Addons page:

[https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)

This sends you to a page, where you download the full package, not the way you are talking about where Addons are added from within Firefox itself (which is a piece of pie.)

I believe I have it sorted though (and Java, which also had to do through an install.) Java I managed to put in usr/local/java (which seemed sensible) whereas I didn't get an option for Acrobat Rdr so have a feeling it's put itself in my user/Downloads folder...

> 
Regards,

Phill.


Thanks for the reply.

---

### Post by kazakore on 2010-03-13
And I just had to fully restart my computer due to it stop seeing the wireless adapter again.

Think I have read in the past about people having this problem with the same wireless adapter though, albeit with older versions of Ubuntu.

Computer is a Clevo D901C laptop and wireless is by Intel 4965AGN i believe. Any ideas why this might be?

---

### Post by cchhrriiss121212 on 2010-03-13
Ubuntu studio comes with jack installed, but requires a few fixes to get it running. Look under applications>sound>qjackctl.
You need to use Ubuntu studio controls to enable memlock and realtime priority which I think is under system menu. If you get errors from jack messages then post what you get.
I would also recommend installing any software from synaptic, foxit reader or evince are functional and lightweight pdf readers.   
Wireless connections are not advisable when running jack as it interferes somehow, which is why US does not install with any network manager.

---

### Post by kazakore on 2010-03-13
I only installed US with none of the packages as initially had issues getting it to install at all.

Assuming using Jack with ALSA the main Renoise Linux page says to type this to check if dependancies are there.

jackd -d alsa -help

This gives me this error, which made me think there is no Jack.

The program 'jackd' is currently not installed.  You can install it by typing:
sudo apt-get install jackd


Replacing jackd with qjackctl and same initial error but looks like I have managed to install it with a apt-get qjackctl so thanks for that.


First attempt at running and get some errors (no chance to look into it myself now so will just post but to be honest didn't expect smooth from first load.)

[IMG]http://deaddogdisko.co.uk/Stuff/Screenshot.png[/IMG]

(Is there a more simple program than GIMP for basic image editing and cropping? Just installed that now to do this as I know it but surely there's something easier for simple things.)



[s]Also had difficulties uploading to the 'net. Had to try and get some artwork up for a friend to do a flier. Hotmail upload just sits at 0%, tried Mediafire and Firefox just froze. Didn't dare try Photobucket just now for this image as at least I have found I can access my FTP through the Nautilus browser fine. Any ideas why this may be? Thought most of the relied on Java and fairly sure Java is working now...[/s]

OK just tried now and both Photobucket and Hotmail seem to be working so ignore  this one, maybe just required a restart after Java install, although it didn't say so.

---

### Post by cchhrriiss121212 on 2010-03-13
OK so now you need to edit a system file:
```
sudo gedit /etc/security/limits.conf
```
Add the following at the bottom:
```
@audio - rtprio 99
@audio - memlock unlimited
@audio - nice &#8722;10
```
Shutdown and restart jack and see what happens.

Did your installation trouble have something to do with MS-corefonts?

Also found this on the forum: [http://ubuntuforums.org/showthread.php?t=1414946&highlight=Intel+4965AGN](http://ubuntuforums.org/showthread.php?t=1414946&highlight=Intel+4965AGN)

---

### Post by kazakore on 2010-03-13
Yeah it was something to do with MS-Corefonts, can't remember the exact message(s) now though.

Thanks, will probably have a go with the configs at work tomorrow, just got home and working on weekends sucks (although this does give me something to do!) Should really of been trying to get a piece done for a little comp on the Renoise forum though...


Also seen posts like this and a few others on getting PA and Jack working together. Currently only skimmed them as it's a bit above my head as this is my first Linux install though but sure it will become clearer as I work through it myself.

[http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/](http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/)

---

### Post by kazakore on 2010-03-13
Well I installed the Network Manager for a bit and that completely screwed things up. Could not stay connected for more than a few second (kB of download) before disconnecting and couldn't work out exactly what I had to do to get it to reconnect. Have removed it and at least I can browse solidly with my settings, think I just need to change and then restart to get it to take each time I move between locations.

Reminds a bit of the Network problems mentioned in this (old) report.

[http://linuxlaptopwiki.net/wiki/Talk:Clevo_D901C](http://linuxlaptopwiki.net/wiki/Talk:Clevo_D901C)

---

### Post by cchhrriiss121212 on 2010-03-13
If pulse audio is working then you should not need to worry about getting it to work with jack. On my system pulse works for stuff like firefox and rythmbox, but when you start up jack pulse is suspended. To get them both talking to each other seems more trouble than it is worth to me.

That MS-corefonts bug affected a lot of users, it is a requirement that you have a wired internet connection during the install otherwise it all screws up. 

Did you try out a live cd before installing US?

---

### Post by kazakore on 2010-03-13
Didn't bother with a Live to be honest, left a space on this hard drive for Linux but only just got around to playing.

Yeah thought it may of been due to needing a wired network as I did connect one to the works Domain between it not working and working. Thing is to actually get onto the 'net it would need to be able to give a domain log-on and password (at least I do to browse the internet or anything through that connection) so  not quite sure how it helps when I didn't have to log on or anything.

I know Jack is written as a requirement for Renoise, which is my music app of choice, but I have got audio (and did before) without using Jack.

---

