---
title: "getting mpeg NOT to play in firefox"
date: 2006-06-07
forum: General Help
---

### Post by Blnd2Spll on 2006-06-07
Currently I use the firefox mplayer plugin to play media files, and when i click on media links such as wmv, it asks if I would like to save to disk, open, etc, but when I click on an .mpeg or .mpg link, the mplayer plugin just opens and plays the video in a new tab, without the option to d/l it.  Is there a way to disable this from happening without removing the functionality of mplayer plugins? 

Thanks.

---

### Post by scxtt on 2006-06-07
edit --> preferences --> downloads --> download actions --> view/edit actions ...

should be something specified for file extensions like that, probably depends on the plugins you have installed ...

this is w/ the latest version of Firefox ...

---

### Post by Blnd2Spll on 2006-06-07
when I go to the view/edit actions, it only has a couple filetypes listed, but no media extensions (just flash extensions and such), and I can't find a way to manually add an extension to this list.  This is with version 1.5.0.3.

---

### Post by scxtt on 2006-06-07
just for curiousity - what does typing about:plugins into firefox give you? -- is the mplayer plugin listed, i'd imagine so ...

i remember wanting to do the same thing when i was using the mplayer plugin in Fedora (back when i used Fedora :p) ...

---

### Post by Blnd2Spll on 2006-06-07
It has mplayerplug-in 3.17 listed as the plugin for mpg, mpeg, mp3's.

---

### Post by scxtt on 2006-06-07
looking @ the windows box here (at work) -- there's a ton of items in the plugin listing (too many really :p) - and looking @ view/edit almost everything but mp(e)g is listed ... maybe it isn't an option w/ mp(e)g? ... i only have flash on my ubuntu install and it's the only thing listed in view/edit ...

:-k

---

### Post by Blnd2Spll on 2006-06-08
In general firefox never remembers my d/l preferences at all...if i select "save to disk" for a specific file type, on the next session it no longer has that saved.  Do you think this is related at all, and is there a file where you can manually edit the d/l options?

---

### Post by sdbillin on 2006-09-10
To get the prompt to open an mpeg file - 

enter about:config in the location bar
search for plugin.disable_full_page_plugin_for_types
double click to edit
add video/mpeg to the string

The string is comma separated, mine for example is - 

video/x-ms-wm,video/x-ms-wvx,video/fli,video/mpeg

Once you've done this restart firefox and all should be good.

---

