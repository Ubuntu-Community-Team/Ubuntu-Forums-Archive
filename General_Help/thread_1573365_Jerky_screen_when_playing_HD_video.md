---
title: "Jerky screen when playing HD video"
date: 2010-09-12
forum: General Help
---

### Post by DanH860 on 2010-09-12
Hi all,

I've been using Ubuntu 10.04 for about a month and generally the graphics work fine (I have a Radeon 2600 XT graphics card and have installed Catalyst Control Centre 10.7).

3D games such as Nexuiz work fine and I can generally play different types of video but when I try to play HD video it gets pretty jerky. The same files play fine in windows so I'm guessing it's a software/driver issue. 

I've read various related posts to this and after typing 'top' into the terminal, I can see that playing the video takes most of the CPU processing resource up, which I as I understand, suggests that most of the work is not being offloaded to the GPU.

Is there anything I can do to sort this problem and be able to play HD video files?

Thanks,
Dan

---

### Post by Ginsu543 on 2010-09-13
What software are you using to play these files? Are you using Totem?

You might also want to give other media players a try, such as VLC (my favorite), mplayer, or xmbc. See if these other programs give you smooth playback.

---

### Post by Mark Phelps on 2010-09-13
+1 for VLC.  It provides its own codecs, so it tends to work when other media players won't.

---

### Post by pkchips on 2010-09-14
I had the same problem as you a long time back in 9.10, and I found the solution.

VLC was also jerky but in a different way to the other media players.

The solution was mplayer - for some reason, although it still uses the CPU, it uses it more efficiently than the others.

mplayer itself has no GUI - use SMPlayer.

Additionally, if you have a newer nvidia card, you can try changing the video renderer in SMPlayer to VDPAU (didn't work for me as my card is in the 7xxx series, you need at least 8xxx series)

---

### Post by DanH860 on 2010-09-19
Thanks for all the suggestions, I normally do use vlc but still get jerky playback both with vlc or the standard ubuntu player (totem I think it's called?). I also tried mplayer and still no luck.

I did try playing various different files and I found that I can play 720p .mp4 files in vlc and mplayer fine but couldnt get smooth playback with .mkv or .avi files, so I'm starting to think it is a codec issue.

Is there anyway I can check into this - presumably if the file plays (even if its jerky), then the codec must be installed?

Additionally, when typing 'top' into a terminal I can see what the cpu is doing, is there anyway I can do the same for the graphics card?

Thanks,
Dan

---

