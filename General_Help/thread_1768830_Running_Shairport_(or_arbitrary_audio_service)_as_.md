---
title: "Running Shairport (or arbitrary audio service) as a Daemon"
date: 2011-05-27
forum: General Help
---

### Post by Ryan Marcus on 2011-05-27
Hey guys,

While I wouldn't consider myself a complete Linux newb, I'm at a bit of a loss here.

I'm trying to get [Shairport](https://github.com/albertz/shairport), a Perl script that acts as an AirPlay speaker, to run as a "daemon" on my Ubuntu machine.

Originally, I had Shairport setup to run whenever I logged in through the "Startup Applications" system panel -- but I'd like the script to run in the background without requiring a user to be logged in.

Obviously, I can't run Shairport until Ubuntu has finished setting up all the audio and network (including avahi) requirements. I took a look at Upstart, and while I understand the event driven model, I'm not sure what I want to execute Shairport after or before. In Narwhal, I see a few things that might be relevant, including: alsa-restore, alsa-store, and avahi-daemon.

I'm also a little confused about how Ubuntu handles audio in general -- I know PulseAudio is the standard, but there appears to be some "hold overs" of ALSA stuff, or perhaps ALSA is just functioning as a plugin to Pulse. Either way, since I can't run Shairport with my own user account (as I don't want to have to login), is there any "gotchas" I should be aware of in terms of other users accessing audio-out?

**TL;DR: How do I run an audio and network enabled Perl script as a daemon without requiring a login?**

Thanks,

Ryan Marcus

---

### Post by iLLNiSS on 2012-04-27
found how to do this under an xbmc thread somewhere.

for simplicity, download shairport, compile it, and move the folder to ~/yourusername/.shairport

```

cd ~/yourusername/.shairport/
sudo nano shairport.pl
```
Find the line (52) where it starts with &#8220;my $hairtunes_cli =&#8221; change the path to the hairtunes file in the shairport folder

```
sudo cp shairport.init.sample /etc/init.d/shairport
sudo nano /etc/init.d/shairport
```
Find the line (20) where it starts with &#8220;DAEMON =&#8221; change the path to the shairport.pl file in the shairport folder

```

sudo chmod +x /etc/init.d/shairport
sudo update-rc.d shairport defaults
sudo service shairport start

```
Test, then reboot and test!

i literally just stumbled on this now and knew there was a thread here with no response that ive stumbled on many times looking for an answer myself!

after re-reading your thread i cant comment on the login issue though... but this will certainly run it as a service.

---

