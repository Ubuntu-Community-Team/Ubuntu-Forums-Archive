---
title: "VLC and SKINS"
date: 2006-03-14
forum: General Help
---

### Post by GreveFelix on 2006-03-14
Hi,
I am very new to Umbutu. But please tell me how to change the skin of VLC media player (because the original one is quite ugly). I tried to run VLC with the Terminal and tried to run "Skins2" but it says that:



felix@ubuntu:~$ vlc skins2
VLC media player 0.8.4-svn20040920 Janus
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat skins2
Datei oder Verzeichnis nicht gefunden
libdvdnav: vm: faild to open/read the DVD
[00000278] main input error: no suitable access module for `skins2'

Gdk-CRITICAL **: file gdkgc.c: line 689 (gdk_gc_set_clip_rectangle): assertion `gc != NULL' failed.

Gdk-CRITICAL **: file gdkdraw.c: line 90 (gdk_draw_rectangle): assertion `gc != NULL' failed.

Gdk-CRITICAL **: file gdkgc.c: line 689 (gdk_gc_set_clip_rectangle): assertion `gc != NULL' failed.
[00000269] main playlist: nothing to play
[00000269] main playlist: stopping playback
[00000278] main input error: no suitable access module for `skins2'
[00000269] main playlist: nothing to play
[00000269] main playlist: stopping playback




Do I have to download "skins2" first and how do I have to install it? Thanks for help ... :)

---

### Post by twigboy on 2006-03-15
Im pretty sure that skins2 already comes with vlc you just need to default to it.  Ive never used vlc from the cl tho so my experience is pretty limited there.

---

### Post by public_void on 2006-03-15
Try vlc -I skins2. Judging by the error message I think vlc it trying to play skins2 as a DVD.

---

### Post by GreveFelix on 2006-03-15
Thanks for your help but as i wrote "vlc -I skins2" an other error happend ... But the VLC Controller looked differend as it opened (but not very good aswell.... )



felix@ubuntu:~$ vlc -I skins2
VLC media player 0.8.4-svn20040920 Janus
[00000275] main interface error: no suitable access module for `/home/felix/.vlc/skins2/default.vlt'
[00000275] skins2 interface error: Failed to open /home/felix/.vlc/skins2/default.vlt for reading
[00000275] skins2 interface error: Failed to parse /home/felix/.vlc/skins2/default.vlt
[00000275] main interface error: no suitable access module for `share/skins2/default.vlt'
[00000275] skins2 interface error: Failed to open share/skins2/default.vlt for reading
[00000275] skins2 interface error: Failed to parse share/skins2/default.vlt
[00000275] skins2 interface: skin: VLC OSX Interface  author: BigBen
[00000275] main interface error: no suitable access module for `/home/felix/.vlc/skins2/default.vlt'
[00000275] skins2 interface error: Failed to open /home/felix/.vlc/skins2/default.vlt for reading
[00000275] skins2 interface error: Failed to parse /home/felix/.vlc/skins2/default.vlt
[00000275] main interface error: no suitable access module for `share/skins2/default.vlt'
[00000275] skins2 interface error: Failed to open share/skins2/default.vlt for reading
[00000275] skins2 interface error: Failed to parse share/skins2/default.vlt
[00000275] skins2 interface: skin: VLC OSX Interface  author: BigBen
felix@ubuntu:~$ vlc -I skins2
VLC media player 0.8.4-svn20040920 Janus
[00000275] skins2 interface: skin: VLC OSX Interface  author: BigBen

---

### Post by public_void on 2006-03-15
I'd go to Synaptic and mark vlc for reinstallation. After that, try vlc -I skins2 again. vlc should look for the the skin default.vlt in /usr/share/vlc/skins2. If the reinstallation fails to fix it, I'd try adding /home/username/.vlc/skins2/default.vlt.

---

### Post by GreveFelix on 2006-03-16
Hi, 
I deinstalled the hole VLC stuff and installed it again. But nothing is differend ... its still not working...

As I wrote:

felix@ubuntu:~$ /home/username/.vlc/skins2/default.vlt.
bash: /home/username/.vlc/skins2/default.vlt.: Datei oder Verzeichnis nicht gefunden

this happend .... the last sentence is german and means:"file directory not found"

---

### Post by public_void on 2006-03-16
Yeah /home/username/.vlc/skins2/default.vlt doesn't exists, you could try creating the directory skins2 in .vlc and copying default.vlt from /usr/share/vlc/skins2.

---

### Post by rowol on 2006-11-01
Anyone getting this to work?

I'm running Edgy release with VLC 0.8.6.

[email]rowol@dali:~/.vlc[/email]/skins2$ vlc --version
VLC media player 0.8.6 Janus
VLC version 0.8.6 Janus
Compiled by [email]buildd@palmer.buil[/email]dd
Compiler: gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.


I got some skins from videolan's website and copied them into /usr/share/vlc/skins2/default.vlt
(I also tried putting them in ~/.vlc/skins2 as the instructions on videolan's website suggest, but that didn't seem to work as well.)

When I start VLC with "vlc -I skins2" it comes up with the default interface.   Then I hit control+s to change the interface....  I can choose a new one, but every one I try crashes with an error similar to:

[00000285] skins2 interface: skin: MediaPlayer 1.01  author: Asim Siddiqui
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)


:(

---

### Post by sakis on 2006-11-03
> **rowol said:**
> Anyone getting this to work?

I'm running Edgy release with VLC 0.8.6.

[email]rowol@dali:~/.vlc[/email]/skins2$ vlc --version
VLC media player 0.8.6 Janus
VLC version 0.8.6 Janus
Compiled by [email]buildd@palmer.buil[/email]dd
Compiler: gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.


I got some skins from videolan's website and copied them into /usr/share/vlc/skins2/default.vlt
(I also tried putting them in ~/.vlc/skins2 as the instructions on videolan's website suggest, but that didn't seem to work as well.)

When I start VLC with "vlc -I skins2" it comes up with the default interface.   Then I hit control+s to change the interface....  I can choose a new one, but every one I try crashes with an error similar to:

[00000285] skins2 interface: skin: MediaPlayer 1.01  author: Asim Siddiqui
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)


:(
It's working o.k to me...

try to save the skin file to  ~/.vlc/skins2 and then open VLC and go Settings--> Preferences--> Interface--> Main Interfaces and change the "Interface module" option from "Default" to "Skinnable Interface". Then Save and restart VLC. Then right click and from the menu category "Select skin" and choose the skin that you save to the ~/.vlc/skins2 directory.

I hope this will work to you too :)

---

### Post by rowol on 2006-11-03
Thanks!  
For some reason that worked a little better.

I was able to load the vlcosx.vlt skin okay.

But when I tried any of these:

[INDENT]chaos.vlt
D-GFX_Dark_Skin.vlt
MediaPlayer.vlt
winamp5.vlt
[/INDENT]

they all crashed in various different ways.   

Do any of these work for you?

Ross

---

### Post by Lord Illidan on 2006-11-03
They also crash for me.

---

### Post by sakis on 2006-11-04
> **rowol said:**
> Thanks!  
For some reason that worked a little better.

I was able to load the vlcosx.vlt skin okay.

But when I tried any of these:

[INDENT]chaos.vlt
D-GFX_Dark_Skin.vlt
MediaPlayer.vlt
winamp5.vlt
[/INDENT]

they all crashed in various different ways.   

Do any of these work for you?

Ross
I didn't try them, i only try the two first on the list (Dalin Media Player and Blissta) and worked fine,

but now that you mentioned it, same here! :p

At least some of them work and we can change the ugly default skin :mrgreen:

---

