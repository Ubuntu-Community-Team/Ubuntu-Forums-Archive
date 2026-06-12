---
title: "Example media files won't play"
date: 2006-06-03
forum: General Help
---

### Post by mwheeler on 2006-06-03
I've just installed Dapper on my desktop and the media files in the Examples folder won't play. Totem tells me "An error occurred. Could not get/set settings from/on resource." Rythmbox won't play either. When I go to System>Prefrences>Sound, however, I am able to hear system sounds just fine. Also, I was able to play oggs in Totem and Rythmbox on this computer under Hoary.

Can anyone help me fix this?

Sound chip is AU8830, if that makes any difference.

Thanks,
Mike

---

### Post by mc-rpg on 2006-06-03
install libmad if you cant play mp3 files. remember that ubuntu (like so many other distros) dont support propietary multimedia files. but the package for support them are available in universe and multiverse repository.

---

### Post by mwheeler on 2006-06-03
Thanks for the reply, but the files that won't play are the OGG files in the "Examples" folder that is included with Ubuntu.

I've done a little searching, and I think that this might be a Gstreamer related problem, but I'm not sure that I'm smart enough to fix it. Any help would be appreciated!

---

### Post by Simon Bridge on 2006-06-04
The only thing I can think of is to reinstall totem ... you should see if this is purely a totem issue by trying the files in a different player, like xmms? gxine?

I'm not suggesting totem-xine due to my own experience:

multimedia involving video will hang the entire x session after a short time (30secs to 5mins - varies).

I am using dapper from flight 7 and dist-upgraded yesterday (see date).

1st experience was that the update manager tells me to restart - and offers a "click here" to help. I do so, this restarts gdm happily - then update manager tells me to restart... repeat ad infinitum. I got around this by manually restarting with sudo shutdown -r now ... the message went away.

I notice that there are vorbis and theora format files in an "examples" directory (actually a link). Folk here all realise that the .ogg extension refers to the *container* not the format.

Since I had previously had trouble playing the sound part of mpeg video files in beta2, I was interested to see what video support was like.

Totem plays vorbis nicely, unless the goom visualisation in one of the larger ones (say "normal" sized) in which case, the x session hangs. The mouse moves, but mouse-clicks do nothing and keyboard input likewise. Presumably I can ssh into this - but I need another computer to do that.

This is the same for totem-xine, xmms and xine-ui... so it isn't a totem problem.

This is the same for playing the ogg/theora file "Experience Ubuntu" interview with Nelson Mandala. Sometimes it dosn't get past the opening sequence, sometimes I can get right to where Nelson is answering the first question.

Thinking there may be a conflict with the x screensaver - I went to preferences > screensaver to switch it off. The screensaver dialog dosn't seem to do anything. There is no way to select individual screensavers, or configure them. No power management options, nothing. What happened?

On the plus side: I see that totem gstreamer will now play DVD video (with the above problem of course - at least the "no url handler" error is no longer).

I am assuming that all this may be an artifact of the upgrade process - though going from dapper->dapper should be seamless(?) so today I am downloading the dapper CDROMs and trying a fresh install.

Previous issues with beta2 were due to the "upgrade" method. Anyone experience odd issues after upgrading: I'll recommend a fresh install before complaining. (Then complain about the shoddy upgrade process.)

---

### Post by mwheeler on 2006-06-08
Wow! Thanks for the detailed advice. I managed to get video and audio playing on my own, and realized I should probably post what I did in case anybody with the same problem runs across this post. All it took was running gstreamer-properties and switching my Default Audio Output Plugin to ESD or OSS (it was on autodetect). This is also accessable through System>Preferences>Multimedia Systems Selector, although that entry was not present in my menus by default.

I must say, however, I have switched over to totem-xine for video because gstreamer was choppy for me.  Totem-xine worked very well for me under Breezy, and is good so far under Dapper.

Thanks again to those who offered advice.

---

