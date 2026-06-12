---
title: "media players everywhere, but no single solution"
date: 2006-02-28
forum: General Help
---

### Post by lapsey on 2006-02-28
Let's see..

VLC: averagely good at everything but some codecs it just can't handle. Certain Mov, or Wmvs for example. 
Mplayer: not bad at all but isn't very forgiving. Not a bad mozilla plugin though. See also "could not find wmvdmod.dlll"
Totem: "could not find device fd:///"   ? huh?


These are some pretty ok solutions but it seems there is no one program that supports everything. 

But please, if you know of any way to get any one of these programs to play everything under the sun (including the latest windows and apple codecs) I'd love to know.

More to the point, how is it that mplayer as packaged with xbmc (xbox media center) can handle absolutely everything I throw at it, yet the ubuntu cannot?

just for the sake of argument I reside in a country with no copyright. DMCA or patent restrictions whatsoever ;)

---

### Post by jrib on 2006-02-28
mplayer with w32codecs has played everything I've thrown at it, what kind of files gave you trouble?

[edit] I did recompile mplayer on my own to get matroska support (and I enabled everything I could while I was at it :)), but even when I was using the repository version, it played everything I downloaded from general media sites (usually wmv, rm, mov, avi)

---

### Post by rkakkar on 2006-02-28
in my experience so far, i found xine + mplayer codecs to be the best bet... although it still messes up sound on certain wmv files.

---

### Post by Bachstelze on 2006-02-28
I never read WMVs so VLC is the choice for me :)

---

### Post by lapsey on 2006-02-28
here are some examples of players not handling various things (via Firefox 1.0.5 on Breezy)

mplayer: [http://news.bbc.co.uk/nolavconsole/ukfs_news/hi/bb_rm_fs.stm?checkedBandwidth=bb&nbram=1&subtitles=hide&checkedMedia=ram&news=1&bbwm=1&nbwm=1&bbram=1&nol_storyid=4756116](http://news.bbc.co.uk/nolavconsole/ukfs_news/hi/bb_rm_fs.stm?checkedBandwidth=bb&nbram=1&subtitles=hide&checkedMedia=ram&news=1&bbwm=1&nbwm=1&bbram=1&nol_storyid=4756116)

totem: [http://news.bbc.co.uk/nolavconsole/ukfs_news/hi/bb_wm_fs.stm?nbram=1&nbwm=1&bbram=1&nol_storyid=4756116&news=1&bbwm=1](http://news.bbc.co.uk/nolavconsole/ukfs_news/hi/bb_wm_fs.stm?nbram=1&nbwm=1&bbram=1&nol_storyid=4756116&news=1&bbwm=1)
totem: [http://www.archive.org/stream/poetry_in_motion_clip/poetry_in_motion_clip_64kb.mp4](http://www.archive.org/stream/poetry_in_motion_clip/poetry_in_motion_clip_64kb.mp4)

mplayer, totem, vlc: [http://x1200.putfile.com/videos/d5-5207532424.wmv](http://x1200.putfile.com/videos/d5-5207532424.wmv)

---

### Post by Perfect Storm on 2006-02-28
Compile the newest VLC it can handle everything :cool:

---

### Post by jrib on 2006-02-28
[QUOTE=lapsey]here are some examples of players not handling various things (via Firefox 1.0.5 on Breezy)

mplayer: [http://news.bbc.co.uk/nolavconsole/ukfs_news/hi/bb_rm_fs.stm?checkedBandwidth=bb&nbram=1&subtitles=hide&checkedMedia=ram&news=1&bbwm=1&nbwm=1&bbram=1&nol_storyid=4756116](http://news.bbc.co.uk/nolavconsole/ukfs_news/hi/bb_rm_fs.stm?checkedBandwidth=bb&nbram=1&subtitles=hide&checkedMedia=ram&news=1&bbwm=1&nbwm=1&bbram=1&nol_storyid=4756116)

totem: [http://news.bbc.co.uk/nolavconsole/ukfs_news/hi/bb_wm_fs.stm?nbram=1&nbwm=1&bbram=1&nol_storyid=4756116&news=1&bbwm=1](http://news.bbc.co.uk/nolavconsole/ukfs_news/hi/bb_wm_fs.stm?nbram=1&nbwm=1&bbram=1&nol_storyid=4756116&news=1&bbwm=1)
totem: [http://www.archive.org/stream/poetry_in_motion_clip/poetry_in_motion_clip_64kb.mp4](http://www.archive.org/stream/poetry_in_motion_clip/poetry_in_motion_clip_64kb.mp4)

mplayer, totem, vlc: [http://x1200.putfile.com/videos/d5-5207532424.wmv](http://x1200.putfile.com/videos/d5-5207532424.wmv)[/QUOTE]

have you installed the w32codecs?  all those file play fine with mplayer here except the .mp4 one

---

