---
title: "No sound from my SB Live"
date: 2006-05-29
forum: General Help
---

### Post by karneevor on 2006-05-29
Hi there.

I'm new to Ubuntu, but somewhat experienced with debian.

I've installed kubuntu dapper on my pc and I can't get any sound at all.

I've learned this so far:
[LIST]
[*]Modules for the sound card IS loaded.
[*]Nothing about the SB Live in dmesg output.
[/LIST]

Apparently the sound configuration is not like anything I've seen before in debian or gentoo. I don't know where to start. I can't find anything in the official documentation.

My questions:
[LIST]
[*]How do I setup sound in general?
[*]How do I setup gstreamer if thats the problem?
[/LIST]

Thanks in advance.

/Karneevor

---

### Post by lost_newbie on 2006-06-05
Hi,

I am new to Ubuntu (and Linux) myself and had the same problem but I belive I have found the answer.

I am using a Soundblaster Live Value.

I went to System>Properties>Sound and made sure the Soundblaster was the default soundcard

Then, I double clicked on the volume control at the top of the screen which opened up the Alsa Mier.  I clicked File>Change device to make sure I was on the sounblaster and then  Edit>Preferences and then selected all the tickboxes (this is not necessary, but I dont know what I am doing!) , then after clicking close I just made sure the volume was turned up on everything.... and that was it.... worked!

Oh, if your trying to open a file such as an MP3 you need to go to Add/Remove applictions then select the unsupported and commercial applictions and download something like Xine (and the plugins)

Hope this helps

---

### Post by wingzinco on 2006-06-06
I'm having the same issue.  Device Manager shows the card as being recognized...problem is,  I don't have any options in the default soundcard dropdown.  Same issue Karneevor?

---

### Post by dan4444 on 2006-06-11
I have the same issue as wingzinco for my sound card (a Realtek alc880 - of type hda-intel). You would think that with all the people showing this same inconsistency (between System-Preferences-Sound-Default sound cards and Device Manager), that there would be an explanation and/or solution for it somewhere by now. Searching, searching, waiting, waiting.

---

### Post by dan4444 on 2006-06-12
I found my solution - see the thread at [http://www.ubuntuforums.org/showthread.php?t=195434](http://www.ubuntuforums.org/showthread.php?t=195434)

---

### Post by Se[BBB]e on 2006-06-16
[QUOTE=lost_newbie]Hi,

I am new to Ubuntu (and Linux) myself and had the same problem but I belive I have found the answer.

I am using a Soundblaster Live Value.

I went to System>Properties>Sound and made sure the Soundblaster was the default soundcard

Then, I double clicked on the volume control at the top of the screen which opened up the Alsa Mier.  I clicked File>Change device to make sure I was on the sounblaster and then  Edit>Preferences and then selected all the tickboxes (this is not necessary, but I dont know what I am doing!) , then after clicking close I just made sure the volume was turned up on everything.... and that was it.... worked!

Oh, if your trying to open a file such as an MP3 you need to go to Add/Remove applictions then select the unsupported and commercial applictions and download something like Xine (and the plugins)

Hope this helps[/QUOTE]
Hey that worked :D I had to reinstall Ubuntu just a while ago because I installed another distro and when I selected Ubuntu from the bootloader the boot image was gone and some hardware didnt work anymore. It was weird.

Anyway, my sound worked before, and now I couldnt figure how I did it... But this solved it. The default sound card was my webcam... WTF... It has a mic in it but it's still weird it lists as a sound card. At least I think so. And on top of that, the default sound card.

It really puzzled me since the sound worked in the default movie player but it wouldnt work in any other application, including whatever program plays the startup sound.

So shame on some developer, Totem was more clever than the operating system :D

---

