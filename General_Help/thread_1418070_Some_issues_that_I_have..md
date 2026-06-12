---
title: "Some issues that I have."
date: 2010-02-28
forum: General Help
---

### Post by ynwa1892 on 2010-02-28
Hi everyone.This is my first post and probably one of my last ones because I can't be much of a help of Ubuntu users.Actually this is why I am here in the first place - i need some help.

There are some issues that I want to talk about.But first of all it's important to say that I'm a complete newbie when talking about Ubuntu or any Linux operating system.I am using Ubuntu 8.04 LTS(which is amazing by the way),my computer is a Presario C700 and since I don't actually know what kind of information you guys need,please ask me.

So the issues in question are:

**1.Sound issue** - Everytime I try to listen a song in youtube I must keep the video's volume at minimum because if I don't the sound becomes quite unpleasent(like when the speakers have reached they maximum power and they start to make this ugly sound..fc...).So the only way I can listen to any video is keeping the volume to minimum and regulating the computer volume.
I tryied various sound schemes but non of them worked.Currently I am using this configuration:
1 - ESD "Enlightened"
2 - PulseAudio
3 - PulseAudio
4 - PulseAudio
5 - Conexant CX20549 (Venice) (OSS Mixer)

Respectively.
[B]
2.Standby issue[/B] - Everytime I put the computer to standby mode and try to run it again I get a blackscreen and I am unable to do anything but keep pressed the power button untill the machine goes off and then start it up again.
[B]
3.Microfone issue[/B] - Two days before installing Ubuntu I was using the XP operating system.My computer has a buildin microfone that worked fine.Now with Ubuntu when I try to use the microfone with Skype for example it seems like it doesn't work which means that the other person can't hear me.I know it must be something about the configurations but I don't know what exactly I must look for.I have a friend who's also using Ubuntu and he has no problems at all.

**4.Wine issue** - I know that it doesn't have much to do with Ubuntu but I think it has to do something even if this sounds kind of strange.I can't get any program installed with Wine to work.
My friend I told you about can.

**5.Account issue** - Sometimes when I change between users accounts(since I have three accounts acording to the usage of the computer) the computer freezes.I don't know what the reason is,but it's a major problem to me.

So those are the things that I have some trouble resolving.Any help would be helpful.

Before I go I must say(for second time) that Ubuntu is an amazing operating system and that I am very happy of knowing about it and being able to use it.Cheers.

Have a wonderful day. :grin:

---

### Post by 3rdalbum on 2010-02-28
For your first problem, it sounds like your "PCM" channel is too loud. This can be fixed. Hit Alt-F2 and type:

```
alsamixer
```

and check "Run in Terminal". Hit Ok.

Use the arrow keys to scroll across to PCM, and turn it down to 90 or less. While we're at it, hit Tab to switch to input devices and check that there's some volume on your microphone. Hit Escape to exit.

Try it now.

3. If your microphone is still giving you trouble, you might just need to set it as the Pulseaudio input device. Right-click your volume control applet on your panel and choose Sound Preferences. Go to the Input tab and choose your microphone.

4. A lot of programs won't work in Wine, no matter what you do. Are these programs listed on the [http://appdb.winehq.org/](http://appdb.winehq.org/) Wine HQ website as working?

It also might help if you specified how you are trying to run these programs. Generally, I open a terminal and type "wine" followed by a space, and then I drag the program I want to run into the terminal.

5. This can sometimes be caused by buggy ATI graphics drivers. I used to have this issue back in 2006 when I had an ATI graphics card - actually it was worse because it would crash on logout. What graphics card are you using?

---

### Post by ynwa1892 on 2010-03-02
Well,the micro problem persists.The sound is now ok.I somehow fixed the changing accounts issue.Don't know really how.And jsut for the record I must say I'm not using Ati nor Nvidia.Anyway...Thanks,3rdabulm :D

---

