---
title: "Audio Problems with PulseAudio in Ubuntu 9.10"
date: 2009-11-13
forum: General Help
---

### Post by Joseph Schwenker on 2009-11-13
I used to think that PulseAudio was okay, until... oh dear.  PulseAudio is a nightmare!  I was thinking that with the "redesigned 3G sound system" in Ubuntu 9.10 would let my source engine games have sound with WINE, but instead, it goofed up WINE, all 3D applications and games, and everything.  I personally love the redesigned audio control panel.  It is great.  It is very simple to use, and I was able to switch microphones in a matter of seconds.  However, I am having numerous "no-sound" incidents, crashes, and bugs due to PulseAudio.  For instance, the Blender game "Yo Frankie!" has crackling, unlistenable audio.  OpenArena, Urban Terror, and every other cool game there is.  NeverPutt and NeverBall aren't having problems for some reason, though.  I am tired of PulseAudio!  Games that worked in WINE before now don't work at all!  **So, my question is, how can I switch back to ALSA and still have a volume control on my panel?**  Of course, WINE games won't even work with ALSA, but better the native ones work and the WINE ones don't than neither work.  Please help!

---

### Post by H13N.H3N on 2009-11-14
i never used to think that pulseaudio is ok, not even fine or worst is nothing (thus having no sound is even better than have pulse audio), i'm a Ubuntu Studio 9.10 K. K. user, the problem is worst for me due that i actually use lots of sound features, i can't work with audacity for example due that PulseAudio is integrated deeply on my system so i can't choice a device for playback like i would do if i used ALSA indeed, i looked at some bugs reports about some problems i have and as far as i understand we will have to make our minds with pulseaudio, because 'it's the only way to improve sound experiencie in linux', i changed from Mandriva because i had TOO many problems with Jack Audio Server, i though that Ubuntu Studio would be a better choice and actually is, amaizing i should say, but PulseAudio is just a mess, in Mandriva, from the control panel i was able to choice what sound services my system could use, and PulseAudio could be deactivated easily from there without the need of purge or uninstall it, with Ubuntu Studio this does not only seem not possible, but now it looks really implosible; PulseAudio is everywhere and many of the programs depends on it, my intel integrated soundcard has native support for open system but pulse audio don't let it work that way and indeed, makes my system slower, aplications in wine are a nightmare, the volume control starts and takes 60% of my memory doing nothing, because not only it can't start, doesn't even close, Rhythmbox crashes randomly, LMMS has sound glitches, Jack is called but not used by Pulse Audio so Rosegarden and Lives have problems, Kdenlive crashes trying to playback and as i mentioned, many of those programs can't choise a device that really works wich would be ALSA..

As i couldn't find how just 'disable' PA, i decided uninstallit, it toke with it a dependency called UbuntuStudio-Desktop, i don't know what it does as the desription is... how i can say it...nonsense, it's the slogan from Ubuntu Studio, after sometime that didn't matter anymore and i uninstalled all what i found with the name 'PulseAudio in it, it was notably fast and good, BUT, incomplete, the GNOME Volume Control is lost and with Pulse Audio is broken plus maybe moreproblems i haven't see because PA is not present, but perhaps is not worst than having it installed.. STIIILLL i re-installed it because i don't know what is really worst.. an incomplete distribution or a full distribution with sound teared appart... just damn it...

---

### Post by Sin@Sin-Sacrifice on 2009-11-14
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats) This might help with pulseaudio. Did for me. Then there's also the sticky [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) which helped me in a lot of cases with different versions of ubuntu. I have absolutely no problems with sound since an upgrade to Karmic and some tweaking from the former link. It is in fact the best audio I've had since playing around with PCs. Audacity is a tool I use quite often along with many of the Ubuntu Studio apps... and I can't complain at all. Hope this helps you guys.

About wine... I had the same issue and setting it to oss only worked. Yo Frankie sucks all around unless you compile it yourself. The binaries aren't that great but can work for some people.

---

### Post by H13N.H3N on 2009-11-14
i'll check those threads, thanks for your interest by the way, maybe you aren't having nightmarish problems with audio due that your system as you wrote in your sig has nice capabilities, but i'm a student with a student's pc and so space and memory is important for me, i played with wine's settings and only set ALSA and OSS as sound drivers, at first all the programs work decent, not good, but is smoething

---

### Post by Zoot7 on 2009-11-14
> **Joseph Schwenker said:**
> **So, my question is, how can I switch back to ALSA and still have a volume control on my panel?**  Of course, WINE games won't even work with ALSA, but better the native ones work and the WINE ones don't than neither work.  Please help!
The simple answer is you can't, not with Karmic. The developers decided to remove the Gnome Volume Control from Karmic. One particular command that is useful however is **pasuspender**; it temporiarly stops pulseaudio and allows other apps to use Alsa. 
Another option of course is to remove pulsaudio, install the Gnome Alsa Mixer and tie it to the tray with alltray. It's not as nice as an applet but it works.

A possible solution is to fetch the source code for the "Gnome Media" and "Gnome Applets" from the Debian Unstable repositories (which too uses Gnome 2.28 ) and recompile yourself with the configure options specified not to depend on Pulseaudio. Of course that assumes that the Gnome Volume Control is in the Debian Unstable package.
What might also work is to download the source code off the Gnome site for "Gnome Media", remove the version that's installed and re-compile it yourself.
I've been meaning to try this for a while now, but I haven't got around to it yet.

---

### Post by Sin@Sin-Sacrifice on 2009-11-14
> **H13N.H3N said:**
> i'll check those threads, thanks for your interest by the way, maybe you aren't having nightmarish problems with audio due that your system as you wrote in your sig has nice capabilities, but i'm a student with a student's pc and so space and memory is important for me, i played with wine's settings and only set ALSA and OSS as sound drivers, at first all the programs work decent, not good, but is smoething

True... perhaps it is the hardware. I hope the links help man... I know how frustrating it can be to love music and video and editing and all the fun therein but having issues at every corner.

---

### Post by isoToxin on 2009-11-14
I had issues with pulseaudio causing apps to lock my cpu at 100% quite frequently.  In the end, I just stopped the pulseaudio daemon from loading, which cured all my problems.  The only other tweak I needed to make was to add a startup item to restore all my volume levels, as they were being muted on each boot.  Basically, I did the following steps to get my system how I wanted it.

Stopped the daemon from ever auto-spawning itself whenever it is killed.

This is done by creating a file called 
client.conf
in the
~/.pulse
folder.

Add a line to this file:
autospawn = no

Once that's done, you should be able to kill pulseaudio by doing:
pulseaudio -k
If the daemon doesn't restart, it's worked.

Then, I moved the following script to my home folder where it was out of the way, so it wouldn't launch pulse at all.

/etc/X11/Xsession.d/70pulseaudio

Once that's moved, pulse should no longer launch when you login.

I then downloaded gnome-alsamixer so that I had an alternative vol control.

Finally, I set my volume levels how I wanted them, then stored them using:

alsactl store

I added a new startup item (system -> preferences -> startup).  The command for this item is:

alsactl restore

This should use the vol levels you stored previously and set them each time gnome starts.

After all this, I'm finally happy with the audio in ubuntu.  All this was done without completely removing pulse, and it can be started whenever necessary with

pulseaudio -D

and killed again with:

pulseaudio -k

---

### Post by H13N.H3N on 2009-11-15
> The only other tweak I needed to make was to add a startup item to restore all my volume levels, as they were being muted on each boot

This is known issue, as it is written is one of many [Volume anomalies]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") and seems to be a common trouble because i have it too with or without PulseAudio, though it is due to some dependence with pulseaudio relation.

> After all this, I'm finally happy with the audio in ubuntu.  All this was done without completely removing pulse

that is provably the closest way to do things 'right' because no other solution works for now, i explored PulseAudio Manager and it has a button which 'let's you shutdown PulseAudio' as far as i understand for it's look:
[IMG]http://img410.imageshack.us/img410/4342/screenshotcd.jpg[/IMG]
Unfortunately this does not work as it should/would seem/be, i haven't tried yet what you said about avoid PulseAudio from spawning every time is killed from the System Monitor, i learned from all the times i messed my Mandriva distro that forcing an app to close or 'die' would cause internal conflicts that can lead to a system crash.

> The simple answer is you can't, not with Karmic. The developers decided to remove the Gnome Volume Control from Karmic.

that's not thrue at all, and i don't know if it's good or not, because the process gnome-volume-control does exist as such, "works" and eats memory, but can't start properly, not even die if you kill it from the system monitor, when succesfully killed and restarted the next error appear:

```
(gnome-volume-control-applet:4475): WARNING **: Connection failed
```

maybe completely removed from karmic would be a better idea then, as for gnome-volume-control is not available from the repos but i think is included in the package that has 'various panel applets', returning to the page were the known issues that karmic has, is also mentioned that:
```

The ALSA volume control is hidden in Karmic, because you normally do not need to mess with it (most things you need are in the new volume control applet). But in some cases you still need to access the ALSA-level volume control.
```

Also i don't know if anyone else has noticed yet, but there's also a constant intermittent sound glitch even if no aplication is playing sound, this is not fault of my drivers or hardware because i also had Mandriva and Ubuntu 8.10 installed before 9.10.

---

### Post by gradinaruvasile on 2009-11-16
The gnome-volume-control is brand new in Karmic... Its essentially pavucontrol wrapped and transformed in a more user friendly/ergonomic format - despite this i found that changing stream volumes dont really work well in it - pavucontrol on the other hand does the job just fine. 
So ALSA users are condemned to the alsamixergui(s), or alsamixer in terminal.
The "Connection failed" message comes from the inability to connect to the PulseAudio server (for example when the PulseAudio process is killed).

Lately i have been playing around PulseAudio in Karmic Xubuntu (this distribution comes with ALSA by default and u have the control applet just like in Jaunty)  
and i found it quite useful for some situations - i have a bluetooth hands free and PA (+blueman manager) lets u use it. Its really awesome stuff. 2-3 clicks and u are set.

But on the downside is the bugged nature of PulseAudio, or should i say its inability to cope with non so standard ALSA implementations. This makes that only newer/standards compliant applications work 100% stable with PulseAudio. But it seems that many apps around are designed to work standalone with their output plugins and they dont like being pushed around by this newcomer supervisor...

Most complex games have problems (excepting maybe the ones that right now are developed actively and there is possibility to add/modify the sound plugins) not to speak about Wine emulation.

---

### Post by H13N.H3N on 2009-11-16
i made my mind and followed the steps mentioned before:

> 1.-create a file called  ¡client.conf' in the ~/.pulse folder.

2.-Add a line to this file: autospawn = no

3.-kill pulseaudio by doing: pulseaudio -k  If the daemon doesn't restart, it's worked.

4.-move the following script to 'home' folder where it was out of the way, so it wouldn't launch pulse at all: /etc/X11/Xsession.d/70pulseaudio

plus, i added a 'custom' launcher in my panel with the comand 'gnome-alsamixer' to have an easy way to access to the sound panel, i can't control the volume anymore with the mouse wheel but is a minor issue, also when i press the volume buttons from my laptop the graphic showing how much the volume is increasing or decreasing does not show up anymore, indeed i assume that the volume is changed accordingly to the buttons, finally i disabled also the 'Volume Control' from the startup, not removed but just disabled, nothing is uninstalled or modified so it's cool with the system, now i'm working good with Karmic Koala, but i have to say it, what a stupid idea make PulseAudio so depply integrated with the system, just so stupid does not even matter if is the only way to evolve the sound experience, by default Ubuntu Studio has version 'stable' of wine installed, 1.0 as well with many if not all packages, why then using the worst bugy unstable sound system and making it by force the one that controls all the sound in a Ubuntu Distribution?, why not keeping with alsa that is really stable and keep PulseAudio as an option? man, that makes no sense no matter what the explain for this cause is.

BTW ixoToxin, thanks for the suggestion, now i can start real work on my PC =D

---

### Post by isoToxin on 2009-11-16
> **H13N.H3N said:**
> BTW ixoToxin, thanks for the suggestion, now i can start real work on my PC =D

Glad you found it useful & got your audio under control.  There are quite possibly more elegant solutions, but this is what worked for me and I'm happy with it.  The best thing about doing it this way is that it's all completely reversible without messing about ripping & replacing stuff.  I'll probably do as you say and disable the new vol control too as it's completely redundant without pulse daemon running.

It is a  shame about losing the OSD for vol though, and I'm in complete agreement with you about it being wrong for the devs to force pulse down everyone's throat so readily with this release.  Should definitely still be an "optional" component imo.

---

### Post by Joseph Schwenker on 2009-11-21
Gosh, why the HELL did the Ubuntu team integrate PulseAudio so deeply into the system when it is so bad!  Ubuntu is supposed to be about choice and freedom, not about forcing buggy sound servers down people's throats whether they work or not.  "Thousands of games, solitaire is not the only game in town." says Ubuntu.  Oh really?  Thousands of games that do not work with PulseAudio, thanks a bunch!  I think that I might just downgrade back to Ubuntu 9.04; 9.10 is turning out worse than Vista.  I really hope that they go back to ALSA in the next release, or at least release an update for Ubuntu 9.10.  I thought that you were good, Ubuntu!

---

### Post by James Goode on 2009-11-21
Is there an easy way to restart PulseAudio, without restarting the whole system?  I have random audio disappearances.

---

### Post by isoToxin on 2009-11-21
> **James Goode said:**
> Is there an easy way to restart PulseAudio, without restarting the whole system?  I have random audio disappearances.

If your system is completely default, and you haven't reconfigured anything then from a terminal, do

pulseaudio -k

The pulse daemon will stop, then it should automatically spawn itself again.

---

### Post by H13N.H3N on 2009-11-21
by default PulseAudio can re-spawn itself after crashing, but this might be the bug itself (with PulseAudio anything can be a bug btw) in the first page, near of the end (if you have the default view of # of post) you have a way to avoid pulseaudio to re-spawn, this way you can use pulse audio whenever you need it and indeed having ALSA support by default, just place the client.conf in your home directory in the ".pulse" folder, and add an extra entry on your panel with the command "gnome-alsamixer" so this way you don't need the """"gnome"""volume-control" (gnome-volume-control infected with PA), if you want to ''disable'' PA for once read carefully the first page.

Now, talking about this "technique" to avoid PA to be the default sound server: the method works, and it does good, buutt i'm very very very sad, not to say very very disappointed, Audacity now works as PA does not interfere and can detect ALSA devices indeed **BUT**, most if not 90% of my applications, programs, apps, widgets, and other software related to sound **does not work anymore!!!** why? because they are setup to be linked with pulseaudio but they cannot work with any other audio server than PA, for example: VirtualBox, Jack, BEAST, Mixxx, TerminatorX, Ardour, Kdenlive and the list keeps growing, i just can't belive it!!!, now.... i had to sacrifice Audacity for having my system running at that 90% lost, reverted the process and all worked 2-2, like it did at first, i tried, i swear i did, i tried to made my mind that PulseAudio cannot be that bad, but if you know "Angry German Kid" fad from YouTube you know now how i feel, but at least i have sound back.... or at least that's what i believed... like i said on my latest post, messing with the system and audio servers can lead to strange behavior of the distro, i say that this **'non-destructive'** process to keep PA from runnning had not fault on this **new problem**;

PulseAudio now starts but the volume control does not work anymore!!, PA and Gnome-Volume-Control start also like they have did since the first install (buggy, but they where always there) but in the recent days now they don't seem to control de volume anymore, i had to keep my launcher for the ALSA Mixer because the regular volume control now does not work, not crash or error notification, it just don't work D=. no, seriously WTF is going on here???? not to say that MIDI works only when PA has the mood to allow it, yesterday i was working on Rosengarden and MUSE, and now both can't playback MIDI for legion's sake!!! (i will not say this is fault of PulseAudio at all till i discover the source of the problem, still this must be due that Timidity is waiting for PA instructions, blame PA for every error of sound could be a bad mistake, it can lead you in the wrong direction while the solution could be as easy as just setting up right Timidity) no updates are available, and i don't want to say this, but Karmic Koala is making me thing that definitely **is not one of the best Ubuntu Distributions** and this is more for the problems leading to constant crashes on sound apps and i repeat, i don't know why devs think that PA is cool enough to make it default, _i admit that Pulse Audio has it own and it's usefull **but only when it's required**, [U]called by the will of the user_, it's a good support but only when it's there inconditionally not as the only way to make a PC to 'speak'[/U].

About PulseAudio itself, on my personal own toughs  and will from me authoring my criteria and sponsoring my opinion, most of the developers say PA works good, but i doubt that up of the 5% of them use, and i mean really use the sound server for media purposes, they have beta testers of course, but is no the same that feel by own flesh what is like for an user to feel the daily pain of facing a complete malfunction of the sound, is not enough for the system just 'sound'. 

Finally to enlighten "why" PulseAudio is supposed to be a good choice i'll post some important parts taken from an article i found on google, you can look for the entire article by it's tittle:

> Why you should care about PulseAudio (and how to start doing it) 

...It's easiest to explain where PulseAudio fits into the GNOME system because of that desktop environment's separation between individual tasks. An application like Rhythmbox relies on GStreamer to decode sound files from compressed form into raw audio. GStreamer in turn passes the audio down to ESD, and ESD delivers it to the ALSA hardware driver.

In this situation, PulseAudio replaces ESD without affecting the rest of the pipeline. But another player might rely on the ALSA userspace library, which is not part of the previous example. Here you can insert PulseAudio into the pipeline, again right above the kernel-level hardware drivers. It adds an extra layer, but with it you enjoy the benefit of all of your audio passing through the same sound server.

If you can reroute all of the audio through one handler, you get more control, fewer conflicts, and fewer surprises...

...Using PulseAudio as a drop-in replacement for ESD, and setting up ALSA to use PulseAudio through /etc/asound.conf, will account for 90% of the audio needs of a regular desktop Linux session....

sooo.... no audacity anymore =(....

> The only major holdouts at present are the audio editor Audacity and the video player MPlayer. Both require fetching development version code from their respective project pages. More importantly, because of the way Audacity controls the sound device, you must shut down PulseAudio before you use it. Changes are in the works, but have not made it to the stable code base yet.

Finally some of the things that PulseAudio can do... or that atleast it is supposed to:

> Basic service is well and good, but PulseAudio earned a place in Linux distros' default audio stacks by doing considerably more. PulseAudio can route audio from multiple sources to multiple sinks, both locally and over the network. You can use it to combine multiple soundcards into a single virtual device, to forward music from one PC to another, or to share a single microphone as an input between multiple PCs.

as i said, PA is a good support, BUT only when it's an option and not an imposition, WHY, just WHRYYY!!!! when i finally found i wouldn't face more problems related to sound in a distro this happens!?!?! and perhaps there is no escape, i heard that many other distros are planing to do the same.. what i might think of all this?:

-Karmic Koala, the brave pioner that revolutioned the sound streaming adventuring to the full integration with PulseAudio?

 ooooorrr... 

-Karmic Koala, the disaster of making an utopic sound server the heart of the noises on my PC??

 i personally want to think in the first option as the right... but most of us are finding that all this only leads to the second one =( still, is too soon to speak about a disaster, Karmic Koala is still on early stages and my hopes are directed in a solution in future updates... but what am i suppose to do today?? i can't work properly!! my boss will fire me!!!!

---

### Post by josh gura on 2009-11-25
+1 for an **urgent update** on pulseaudio.

---

### Post by DataMatrix on 2009-11-26
I'm going to oss soon :-k
I had it with pulse!

---

### Post by H13N.H3N on 2009-11-27
well, some light seemed to shown about all this, VertexPusher explained me (after some of my complains) how PA is working on Ubuntu 9.10:

> **VertexPusher said:**
> There is no audio application that needs PulseAudio. All of them work with ALSA, either directly or through Jack. Since PulseAudio is broken in many ways, it makes perfect sense to remove it, especially from multimedia production environments such as Ubuntu Studio.

PulseAudio is not deeply integrated into Gnome either. Gnome is designed to use whatever sound system is available. The PulseAudio mixer and configuration applet in Ubuntu is _not_ part of Gnome. You can replace it with gnome-alsamixer any time. GStreamer applications such as Totem Movie Player can use any sound system for which a plugin is installed. Just replace gstreamer0.10-pulseaudio with gstreamer0.10-alsa, remove pulseaudio and see what happens.

Statements such as "PulseAudio is the only option" or "PulseAudio is here to stay" are just nonsense.

still the dependency named 'ubuntustudio-desktop' is uninstalled also at removing pulse audio and gstreamer-pulseaudio, the only thing that is still missing is the gnome-volume-control, i have one idea or two on how i can solve this but i'll wait for more info before start messing with the audio

---

### Post by Zoot7 on 2009-11-27
> **H13N.H3N said:**
> still the dependency named 'ubuntustudio-desktop' is uninstalled also at removing pulse audio and gstreamer-pulseaudio, the only thing that is still missing is the gnome-volume-control, i have one idea or two on how i can solve this but i'll wait for more info before start messing with the audio
Regarding the Gnome-Volume-Control, you could try the Debian Unstable repos. AFAIK Debian is staying away from Pulse until all the issues are worked out, and of course Ubuntu being a fork of Debian should be compatible with the Debain repos with no issues.
I've been meaning to try this for a while now, but on account of being a victim of flooding I haven't got around to it yet.

---

### Post by H13N.H3N on 2009-11-27
> **Zoot7 said:**
> Regarding the Gnome-Volume-Control, you could try the Debian Unstable repos. AFAIK Debian is staying away from Pulse until all the issues are worked out, and of course Ubuntu being a fork of Debian should be compatible with the Debain repos with no issues

that is one of those two ideas, i can't imagine how different can be the Debian package (with no PA integration) compared with the actual one in Ubuntu 9.10, can be as simple as just replacing liraries or binaries? is something with a .conf file? how hard can be that one fix can came in an update? well, i don't know but i'll consider to use the debian unstable package if no other solution is found, thanks for the tip btw

---

### Post by Zoot7 on 2009-11-28
> **H13N.H3N said:**
> that is one of those two ideas, i can't imagine how different can be the Debian package (with no PA integration) compared with the actual one in Ubuntu 9.10, can be as simple as just replacing liraries or binaries? is something with a .conf file? how hard can be that one fix can came in an update? well, i don't know but i'll consider to use the debian unstable package if no other solution is found, thanks for the tip btw
AFAIK It'd just be a case of maybe downloading and running the Debian Stable install, activating the unstable repos (like you do if you wanted to use Lucid now). Running:
```

apt-get source gnome-applets gnome-media
```
Transferring those to your Ubuntu install, and running this to compile the source and build the packages:
```
dpkg-buildpackage -b -j4 -D
```
Then lastly telling apt to ignore the packages upon running apt-get update.

I have a post here about re-compiling the source to get the volume control applet back in the bar after removing Pulseaudio.
[http://ubuntuforums.org/showpost.php?p=8343644&postcount=40](http://ubuntuforums.org/showpost.php?p=8343644&postcount=40)

---

### Post by ed-koala on 2009-11-28
For those having troubles with Wine and Pulseaudio, use Synaptic to load pulseaudio-utils. Set your Wine audio to OSS.  Then run your Wine app with the prefix "padsp wine ..."

This lets your Wine apps use OSS so their sound is clear and still lets other apps also play sound. Works like a charm.

---

### Post by H13N.H3N on 2009-11-28
> **Zoot7 said:**
> AFAIK It'd just be a case of maybe downloading and running the Debian Stable install, activating the unstable repos (like you do if you wanted to use Lucid now). Running:
```

apt-get source gnome-applets gnome-media
```
Transferring those to your Ubuntu install, and running this to compile the source and build the packages:
```
dpkg-buildpackage -b -j4 -D
```
Then lastly telling apt to ignore the packages upon running apt-get update.

I have a post here about re-compiling the source to get the volume control applet back in the bar after removing Pulseaudio.
[http://ubuntuforums.org/showpost.php?p=8343644&postcount=40](http://ubuntuforums.org/showpost.php?p=8343644&postcount=40)

Looks simple, i hope don't kill my system or other important part of my distro, with a bit of luck i'll be editing this post to annotate my results

---

### Post by Cresho on 2009-12-03
Ya!  Pulseaudio really sucks but...  It's sort of working now.  I pulled out my audigy gamer and activated my motherboard's sound card.  I configured the onboard for 6 channel audio and now it works just fine.  The sound prefferences has pretty much everything i want minus the treble and base controls.

The only thing i cant get working is the microphone in quake wars.  It runs fine in quake wars though.  There's alot of good suggestions here like pausing or temporarily killing pulseaudio.  I think im going to try those.  I feel a bit sad that i yanked out my audigy audio card to use the motherboards.

---

### Post by Zoot7 on 2009-12-03
> **H13N.H3N said:**
> Looks simple, i hope don't kill my system or other important part of my distro, with a bit of luck i'll be editing this post to annotate my results
Shouldn't kill anything really except the media apps inherent to Gnome. And even if the compiled version doesn't work (It will if it compiles fine) you can easily just **sudo apt-get update && sudo apt-get upgrade** and that'll reset the gnome media packages back to their default.
If it does work okay, use apt to pin them.

BTW I also forgot to mention, another command to run would be
```
sudo apt-get build-dep gnome-applets gnome-media
```
to pull in all the dependencies required to compile from source.

---

### Post by Zoot7 on 2009-12-03
BTW I've a guide posted here how to get back the volume control applet on the panel after removing pulseaudio, it should be of some use to you.
[http://ubuntuforums.org/showpost.php?p=8343644&postcount=40](http://ubuntuforums.org/showpost.php?p=8343644&postcount=40)

---

### Post by Schotty on 2010-01-26
> **ed-koala said:**
> For those having troubles with Wine and Pulseaudio, use Synaptic to load pulseaudio-utils. Set your Wine audio to OSS.  Then run your Wine app with the prefix "padsp wine ..."

This lets your Wine apps use OSS so their sound is clear and still lets other apps also play sound. Works like a charm.

great tip, but the solution [here](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats) fixed *my* issue.  So for those running into issues, try mine first, then I would go your route if it fails.  I prefer to make the whole system work right, rather than an app by app basis (I use Crossover and bottle each app on its own to make sure each game doesn't booger up any other).

My issue was DDO having stuttering sound every now and then.  This resolved it.  Generally the start of the stuttering was a problem with the ingame voice chat that would start PA into hell.  

HTH.

---

### Post by nairatinu on 2010-02-24
Thanks for this, worked well for me and I like the relatively "non-invasive" approach especially compared to the others being offered up.  Pulse seems to be embedded into Totem, so it's volume control is grayed out, but I use VLC anyway and it allows you to choose ALSA for sound.  QAmix seems to work fine also and retains it's gains and settings between sessions, so I didn't bother with the Alsamixer steps.

I'm of the opinion, so far, that Pulsaudio should be abandoned in future releases.  I fail to see its merits, but I'm no geek...

:D :D :D :D :D (five smiles for you)

---

