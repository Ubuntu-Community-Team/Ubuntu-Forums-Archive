---
title: "text in multiple applications is white on white"
date: 2012-08-24
forum: General Help
---

### Post by pmooney78 on 2012-08-24
This is a minor but very annoying problem problem. There are multiple applications in which some text is unreadable because the text is white on a white background. Some dialogs in VLC, for instance, are difficult to read because they display white text on a white background. This is the case for the codec information screen and every other line in the playlist (alternate lines display white on light grey, which I can read). It's possible to read the lines by clicking to highlight them, in which case they're white against the highlight color, but this winds up taking a lot more time as I hit an arrow key repeatedly, read one line, determine it's not the one I'm looking for, and move on to the next line. I'd really prefer that text in dialogs displays in black.

There are similar problems in Google Earth and in the file dialogs for every application that uses the KDE file open/save dialogs.

I've tried changing the theme in the System > Preferences > Appearance applet, but it doesn't seem to make a difference in those applications experiencing the problem. 

The same problem also occurs whether I'm using GNOME or Xfce. I've tried searching these forums and Google, but nothing useful has popped up.

Currently running Ubuntu 10.04 on a Sony Vaio VGN-FZ250E laptop (but this problem also popped up in the past on my old HP notebook, too). Any help is much appreciated.

---

### Post by mzaam on 2012-08-25
have you try changing your theme?
u may use ubuntu-tweak or LXappearance

---

### Post by pmooney78 on 2012-08-26
Thank you -- I did try changing the theme already, and neither Ubuntu Tweak nor LXAppearance seems to have any helpful options (where there are options for setting text color, it's already set to black).

Is there somewhere that these options are kept, so that I can just delete a file and (hopefully) it will be recreated with default settings?

---

### Post by MrGiedi on 2012-08-27
Have you tried this [http://askubuntu.com/questions/105471/white-text-on-white-background-problem](http://askubuntu.com/questions/105471/white-text-on-white-background-problem)?  I think changin theme files might solve this issue.

---

### Post by bogan on 2012-08-27
Hi!, **pmooney78**, 

I had exactly the same proplem and solved it by changing the 'GTK' & 'Window' Themes in Ubuntu Tweak. It is the Default Themes that cause the problem [Ambience ].

I used Adwaita & Cruz sucessfully, but now use Clearwaita down loaded from gnome.org.

There is also a rather complex program called : 'Gnome Color Chooser', which also allows widening the annoyingly narrow Scroll bars.

Chao!,  you are lucky, I got no response to my thread in 10 days. **bogan**.

---

### Post by pmooney78 on 2012-08-27
@bogan: 

Ah, this is actually my second attempt. I initially posted in the Multimedia thread because I only noticed it happening with VLC.

Neither of these actually works, though: I can't find a place to change GTK- or window-theme-related settings in Ubuntu Tweak, and I've tried forcing text to black in the GNOME color chooser, but it doesn't seem to help.

---

### Post by pmooney78 on 2012-08-27
@MrGiedi:

I took a look at the article you mentioned, but it is perhaps targeted at GNOME 3 users: poking around in /usr/share/themes/{name of various theme} shows a different directory structure than is mentioned in that article. For instance, here is the output of 'find /usr/share/themes/Gorilla -iname "*"' :

```

/usr/share/themes/Gorilla
/usr/share/themes/Gorilla/gtk-2.0
/usr/share/themes/Gorilla/gtk-2.0/gtkrc
/usr/share/themes/Gorilla/index.theme
/usr/share/themes/Gorilla/metacity-1
/usr/share/themes/Gorilla/metacity-1/metacity-theme-1.xml
/usr/share/themes/Gorilla/metacity-1/wm-menu.svg
/usr/share/themes/Gorilla/metacity-1/wm-close.svg
/usr/share/themes/Gorilla/metacity-1/wm-restore.svg
/usr/share/themes/Gorilla/metacity-1/wm-min.svg
/usr/share/themes/Gorilla/metacity-1/wm-max.svg
/usr/share/themes/Gorilla/xfwm4
/usr/share/themes/Gorilla/xfwm4/close-active.xpm
/usr/share/themes/Gorilla/xfwm4/close-pressed.xpm
/usr/share/themes/Gorilla/xfwm4/shade-active.xpm
/usr/share/themes/Gorilla/xfwm4/menu-pressed.xpm
/usr/share/themes/Gorilla/xfwm4/title-2-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/maximize-pressed.xpm
/usr/share/themes/Gorilla/xfwm4/maximize-active.xpm
/usr/share/themes/Gorilla/xfwm4/title-5-active.xpm
/usr/share/themes/Gorilla/xfwm4/top-right-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/right-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/bottom-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/hide-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/shade-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/themerc
/usr/share/themes/Gorilla/xfwm4/hide-pressed.xpm
/usr/share/themes/Gorilla/xfwm4/close-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/title-1-active.xpm
/usr/share/themes/Gorilla/xfwm4/bottom-active.xpm
/usr/share/themes/Gorilla/xfwm4/top-right-active.xpm
/usr/share/themes/Gorilla/xfwm4/hide-active.xpm
/usr/share/themes/Gorilla/xfwm4/title-3-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/title-4-active.xpm
/usr/share/themes/Gorilla/xfwm4/right-active.xpm
/usr/share/themes/Gorilla/xfwm4/bottom-left-active.xpm
/usr/share/themes/Gorilla/xfwm4/top-left-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/stick-active.xpm
/usr/share/themes/Gorilla/xfwm4/left-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/shade-pressed.xpm
/usr/share/themes/Gorilla/xfwm4/menu-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/title-2-active.xpm
/usr/share/themes/Gorilla/xfwm4/maximize-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/README
/usr/share/themes/Gorilla/xfwm4/title-3-active.xpm
/usr/share/themes/Gorilla/xfwm4/top-left-active.xpm
/usr/share/themes/Gorilla/xfwm4/stick-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/bottom-right-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/stick-pressed.xpm
/usr/share/themes/Gorilla/xfwm4/title-4-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/title-1-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/bottom-right-active.xpm
/usr/share/themes/Gorilla/xfwm4/title-5-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/bottom-left-inactive.xpm
/usr/share/themes/Gorilla/xfwm4/left-active.xpm
/usr/share/themes/Gorilla/xfwm4/menu-active.xpm

```

You'll note that of the three files mentioned in the suggested answer, neither /usr/share/themes/{theme name}/gtk-3.0/gtk.css nor /usr/share/themes/{theme name}/gtk-3.0/settings.ini exists. In fact, neither 'find /usr/share/themes -iname "gtk.css"' nor 'find /usr/share/themes -iname "settings.ini"' returns anything at all -- there are no gtk.css or settings.ini files for any of my themes (and I installed a bunch of themes when I initially thought that just changing the theme might solve the problem).

There ARE various "gtkrc" files in subfolders of the themes mentioned, but opening them up and searching doesn't show any entries at all for base_color, text_color, bg_color, or fg_color -- there ARE many various colors listed in this file, but all of them seem to have sensible values, as far as I can tell, for what they seem to be trying to set (things that look like settings for text are black or close to it, whereas backgrounds are white or nearly so).

Sigh. This is definitely one of my "dammit, why aren't I just using a commercial OS?" kind of days.

---

### Post by pqwoerituytrueiwoq on 2012-08-28
if you are using a theme on xfce you may want to get it from the devs
[https://github.com/shimmerproject](https://github.com/shimmerproject)
for albatross what i did was delete /usr/share/themes/Albatross/* and put everything from the copy albatross on the above link in there

---

### Post by pmooney78 on 2012-09-23
Well, I finally managed to solve it by deleting a bunch of stuff from subfolders of ~/ (while booting from a USB key) -- I just went in and deleted everything that I wasn't absolutely sure I needed. Of course, I made a backup first, and deleted carefully, and I'm now running through applications I use to be sure I haven't lost anything.

Anyway, problem seems to be solved! I appreciate everyone's assistance. (=

---

