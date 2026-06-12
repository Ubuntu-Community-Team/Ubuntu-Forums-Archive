---
title: "Couple of 11.10 questions"
date: 2011-10-22
forum: General Help
---

### Post by tpprynn on 2011-10-22
1. I need sometimes to look at the log file viewer at the moment, trying to solve a long-standing kernel issue. When I open what says it is the viewer in the ddash it's completely blank, just a white box without all the former left pane categories of the log file viewer up to 11.04. What's up there? I did also install gnome-utils with no change.

2. Are tooltips still a gtk2 thing? I have had 11.10 for a couple of hours but it looks like the days of a quick tweak in a single file to change colour schemes is gone (maybe for the best, I did lose a lot of time there...) 

3. Is gnome-tweak-tool a front end for something I can alter without it? Though it's useful to Unity it installs and uninstalls with gnome-shell which is unfortunate.

4. Is the Unity top panel a css thing? In 11.04 I could change it by dropping a different image file in the relevant folder but that hasn't worked this time round.

I'm quite liking Unity now and am glad the only thing that horrified me in the beta, a purely aesthetic issue to do with the panel widgets formerly having been opaque on the transparent panel when the dash was on, is fixed. I'm surprised to find I installed and then uninstalled gnome-shell. Congrats to all involved. ('Desktop' feels like an oddly prosaic word to see so prominently on an artsy, attractive new DE though once booted up...)  

Thanks for any input.

---

### Post by rsvancara on 2011-10-22
1. Open a terminal and use the command tail to look at your logs.  It is a very good tool

Examples:

```
tail -f /var/log/messages
tail -f /var/log/authlog
```

Not sure about the other questions.  I am slowly adapting to Unity, but it has not been as easy as using traditional gnome interfaces.

Randall Svancara
[http://www.knowyourlinux.com](http://www.knowyourlinux.com)

---

### Post by tpprynn on 2011-10-24
3. It looks like most useful things though more specific to Gnome 3 can still with Unity be done with dconf-editor, in particular, for me:

org > gnome > applications > interface

where it looks like gtk-colour-scheme might be a lot of use to get rid of some of the oranges... It looks like those lines at the start of a familiar gtk theme could be pasted in here as the form is the same.

org > extensions > plugins > xsettings

where the font rendering settings are.

---

