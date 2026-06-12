---
title: "File associations -Vlc instead of Totem"
date: 2010-01-21
forum: General Help
---

### Post by motorhead_1 on 2010-01-21
I've edited the default file list association; sudo gedit /etc/gnome/defaults.list
replacing all the totem.desktop with vlc.desktop (ctrl+H). however I don't understand how but VLC opens only certain files such as .flac, .wmv but not .mp3, .avi
how is that possible?

---

### Post by ianto` on 2010-01-21
If you are running a standard Ubuntu installation (with GNOME) then you can simply go to *System > Preferences > Preferred Applications* in the menu.  Change the tab to Multimedia and set it to the VLC Player and it should then work.

---

### Post by squrl on 2010-01-21
I would be interested in knowing exactly how to do that. Vlc has been installed but it doesn't show up as a choice under preferred apps. 

Thank You

---

### Post by VCoolio on 2010-01-21
also the system defaults.list will be overruled by the users own in ~/.local/share/applications (defaults.list and mimeapps.list). For individual filetypes change the default app by rightclick, then properties, then the tab "open with" (so not "open with" right from the context menu).

---

### Post by jamesisin on 2010-01-21
> **squrl said:**
> I would be interested in knowing exactly how to do that. Vlc has been installed but it doesn't show up as a choice under preferred apps.

Choose Custom from the drop-down and enter your preferred command (presumably vlc) in the Command: field.

(It's probably just vlc you want to enter, but there may be arguments you'd like to include.  You have options.  The VLC icon in my panel is actually vlc %f.)

---

### Post by motorhead_1 on 2010-01-21
> **VCoolio said:**
>  then the tab "open with" (so not "open with" right from the context menu).thanks, this was my mistake. so I can do this manually for every file extension now.


the mimeapps.list looks like this
```

[Added Associations]
application/x-bittorrent=kde4-ktorrent.desktop;transmission.desktop;
application/x-wine-extension-inf=userapp-wine-QSS12U.desktop;
application/x-ms-dos-executable=wine.desktop;file-roller.desktop;userapp-wine-QSS12U.desktop;
video/x-msvideo=vlc.desktop;totem.desktop;gnome-mplayer.desktop;mplayer.desktop;
```

I'm not quite sure how to edit it in order to have VLC for everything

> **jamesisin said:**
> Choose Custom from the drop-down and enter your preferred command (presumably vlc) in the Command: field.

(It's probably just vlc you want to enter, but there may be arguments you'd like to include.  You have options.  The VLC icon in my panel is actually vlc %f.)
yea VLC of course :D, but what should I type exactly in the command blank space?

---

### Post by jamesisin on 2010-01-22
vlc

Or

vlc %f

I'm not sure if there are other arguments available.  Nor do I know what the %f argument does.

---

### Post by VCoolio on 2010-01-22
to be specific: /usr/bin/vlc (if you installed vlc from a deb / repo), you can check with 'which vlc'. But because /usr/bin is in your PATH (the folders where the system looks for apps automatically, check with "echo $PATH") you only need  'vlc' to run vlc.

The %f means it will open the file that is piped to it (or drag and dropped on a launcher). %F would mean it could open multiple files at once (in the case of vlc a bad idea); %u / %U the same but for urls, %d for directory. More [here]("http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-0.9.4.html#exec-variables").

---

### Post by jamesisin on 2010-01-22
Thanks.  Very useful.

I wonder...

When I dump a handful of files on VLC they each open an instance of VLC.  Is there a way to set it up so that if I dump a handful of files they are merely added to the playlist when VLC is opened?  (Perhaps %F?)

---

### Post by mc4man on 2010-01-22
> When I dump a handful of files on VLC they each open an instance of VLC. Is there a way to set it up
Depends on what version of vlc you have. If more recent then look in tools -> preferences -> "allow only one instance"

> set it up so that if I dump a handful of files they are merely added to the playlist

Again depends on vlc version and how to do on the ubuntu version
No 1.0.X version will support the enqueue gui setting so you need to create a userapp.desktop (custom command) with a launch comm. of vlc --playlist-enqueue

(Atm vlc remains poor at properly ordered tracks when added in a group, I tend to use a playlist for that (.m3u, .xspf ect.) or add individually from r.click -> open with Vlc Enqueue or d. left click (file association with Vlc Enqueue

The best thing to do with userapp.desktop's is after creating one is to  open in a text editor and give a distinctive name. (found in ~/.local/share/applications

for instance to queue in vlc

> #!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=vlc --playlist-enqueue %f
Name=Vlc Enqueue
Comment=Custom definition for vlc
NoDisplay=true
Icon=/home/doug/Documents/vlc32x32.png
Name[en_US]=Vlc Enqueue

userapp.desktops can also be edited thru their properties, easier on some ubuntu releases than text editor

---

### Post by jamesisin on 2010-01-22
My version has a 'one instance' mode and an associated 'enqueue' setting.  I'll try that.

---

### Post by mc4man on 2010-01-22
the an "associated 'enqueue' setting" is disabled and will be removed from the gui in vlc 1.0.5 (will return working in vlc 1.1

To enqueue - add to playlist without immediately playing (append really), you must do as mentioned, a custom vlc launcher (userapp.desktop

---

### Post by scouser73 on 2010-01-22
Go to the file that you want to play using VLC, right click & select **Properties** and click on the **Open With** tab and choose VLC

---

### Post by jamesisin on 2010-01-23
It works for me.  I can right-click on a bunch of flac files and choose open with VLC and they will all be enqueued (with the first track playing).  I can also drop that same pile of flac files onto my launcher (vlc %f) and the same thing happens.

---

### Post by mc4man on 2010-01-23
> I can right-click on a bunch of flac files and choose open with VLC and they will all be enqueued (with the first track playing). I can also drop that same pile of flac files onto my launcher (vlc %f) and the same thing happens.
Correct, that's expected behaviour. 

What I was referring to and related to the 'enqueue while in one instance mode' was that any further tracks added to vlc, while they will be queued (appended) to the playlist will start playing immediately, bypassing any unplayed tracks in the playlist.

The only way to add an additional track(s) to the queue and not start it (them) playing is to add directly to the playlist itself 

If wanting to add from a left click association or r. 'click open with' you need to use a custom launcher (atm)

---

### Post by jamesisin on 2010-01-23
Well this is good information to have and if I need to append I know where to come for the launcher instructions (so thanks for that too).  For my part, this functionality is enough for me.  I can see the value of having the rest working though.  I just hope they don't remove this part while the fix the other.

---

### Post by mc4man on 2010-01-23
> I just hope they don't remove this part while the fix the other.
No probably not. It seems some bugs or use issues get fixes in the 1.0.X releases, others don't.
The 1.1 version gets the most dev, (for better or worse) and **someday** could be a very impressive release

Edit:
for instance this is the new media browser/playlist  screen in 1.1, now a lot of things don't work well, but there is a direction to make it more full featured so to speak

---

