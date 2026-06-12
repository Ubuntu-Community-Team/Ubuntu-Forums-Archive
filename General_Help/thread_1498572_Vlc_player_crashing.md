---
title: "Vlc player crashing"
date: 2010-05-31
forum: General Help
---

### Post by satyen on 2010-05-31
Hi all,

I have a strange problem. I am using ubuntu 9.04 . Till yesterday my vlc player was working fine( for both video and audio files), but today if I try to open any video file it opens for 1-2 secs and then suddenly crashing out. For .mp3 files it's simply not working.

thanks in advance

satyen

---

### Post by xfearxnxloathing on 2010-05-31
installed any skins or plugins lately?  try removing them and see if that helps anything, next i would uninstall and reinstall.  i would do this through Ubuntu Software Center.  hope this helps..

---

### Post by JoelOl75 on 2010-06-01
Just blow away ~/.config/vlc

It will use default setting then, re-installing without a purge won't help at all and isn't needed.

It's probably a bad setting (Usually selecting the wrong output filter or a buggy or unsupported plugin)

---

### Post by satyen on 2010-06-01
you mean to say i've just to enter this "~/.config/vlc " command line in the terminal and it 'll automatically configure the VLC ??

---

### Post by jocko on 2010-06-02
> **satyen said:**
> you mean to say i've just to enter this "~/.config/vlc " command line in the terminal and it 'll automatically configure the VLC ??
No. He meant you need to delete the folder ~/.config/vlc where vlc stores all it's settings.

---

### Post by JoelOl75 on 2010-06-02
Yes, sorry.... open a terminal and type

rm -r ~/.config/vlc

~ is a shortcut for /home/username

Just be sure not to delete the whole config directory.  You can do this in nautilus if you enable "Show hidden files and directories in the nautilus settings.  Then you can just navigate to the .config directory and toss out the vlc directory.

---

### Post by satyen on 2010-06-08
hi joel,

thanks for the help.
satyen

---

