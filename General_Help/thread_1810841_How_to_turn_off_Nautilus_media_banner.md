---
title: "How to turn off Nautilus media banner?"
date: 2011-07-23
forum: General Help
---

### Post by amoebios on 2011-07-23
The file browser Nautilus displays a banner with a statement about what type of media is connected, what files are stored on the media (music on a CD, movies on a DVD, photos on a camera, etc.) and a button to open the suggested application when I insert or connect media to the computer and choose to open it in the file browser. I did not find this behaviour useful, yet. (There already is the pop-up window that is displayed when media is inserted or connected which asks what application to open.)

In a specific case, where I connect my cellphone to the computer there are two notices:
"The media contains digital photos [Open F-Spot Photo Manager]" and
"These files are on a digital audio player [Open Banshee Media Player]"

It is little useful. One is okay, but two notices take up too much screen space for displaying files.
How do I turn this off?

---

### Post by CatKiller on 2011-07-23
System -> Preferences -> Preferred Applications -> Multimedia, I think.

---

### Post by amoebios on 2011-07-28
That is only the music player. :(

Edit:
Here is a screenshot for better illustration.
[IMG]http://i186.photobucket.com/albums/x100/amoebios_4m/nautilus_media_banner.jpg[/IMG] It is okay on a big screen, but gets in the way in small windows.

---

### Post by CatKiller on 2011-07-28
Actually, I sent you to the wrong screen (wasn't at my computer at the time). The bit I was thinking of was Nautilus -> Edit -> Preferences -> Media. I thought that if you change the Music Player and Photos options to Do Nothing, it would stop it doing that. But it doesn't, I just checked.

It's something to do with the x-content/audio-player MIME type, but I'm afraid I don't really know how that works. I tried commenting lines from a few files, but it didn't seem to help. I could change which application showed, but I haven't been able to make nothing show.

The only other solution I can suggest is using a different file manager. Nautilus is user-friendly, but not terribly configurable. There might be one that behaves more to your liking.

FWIW, you can turn off the pop-up notifications.

---

### Post by amoebios on 2011-07-28
Thanks, I will try other file managers. :)

I thought I may have overlooked and missed a setting.

---

