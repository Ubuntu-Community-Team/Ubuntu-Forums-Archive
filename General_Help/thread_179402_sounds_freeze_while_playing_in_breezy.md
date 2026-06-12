---
title: "sounds freeze while playing in breezy"
date: 2006-05-19
forum: General Help
---

### Post by Mrbigshot08 on 2006-05-19
Hi, this is my first week as a linux user, and I hate signing up to a forum, and have my first post be for help, it makes me feel like i'm using you people, but i have helped others in the past mostly with video editing in windows.

Anyway, my problem is with playing sounds in gnome in the latest Breezy Badger. Whenever I play an MP3, or movie file, or whatever, the programs i use either Mplayer or Totem, will open the file, play it for a little, but then the sound starts to loop and the system freezes and I have to unplug the computer. It also happens when I use other programs that frequently use sounds such as GAIM Instant Messenger.

My soundcard is a Guillemot Hercules Gamesurround Muse XL. It is supported, i checked the ALSA website, and when I go to preferences i have two possible sound cards the Intel 82801BA-ICH2 (which is the motherboard audio i guess) and C-Media PCI CMI8738. Whenever i boot up the system the sound card is always set at the Intel, but sound still plays. Anyway, it doesn't matter what I have set, the same thing happens.

The sound module for the Gamesurround Muse is
snd-cmipci, if that helps.

By the way, I have installed all the codecs installed properly through Synaptic as far as I can tell.

I think the problem is with the linux trying to play multiple sounds at once through the card. I tried adding code that I found in the Ubuntu Wiki, to the beginning of the asound.state file by logging in as root, but that didn't help. (i know how dangerous it is to log in as root, but thats all i did, and my system still works fine)

Thats all I can think of right now, if you need any log files, just tell me the command to put in the terminal, and i'll post the results. I have a feeling this is a simple problem that happens all the time. But then again probably not, since I've tried all the Ubuntu Wiki sources. Maybe I didn't set up the software mixing to run multiple sounds properly?

---

