---
title: "totem and mplayer problems"
date: 2006-03-18
forum: General Help
---

### Post by buttari on 2006-03-18
Hi,
I followed the instructions in here:
[http://wiki.ubuntu.com/RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats")

but totem doesn't play wmv files. I can ear the audio but see no video. Running totem from a shell I get the following error:
> 
** Message: don't know how to handle video/x-wmv, wmvversion=(int)3, framerate=(double)25, width=(int)640, height=(int)480, codec_data=(buffer)4ee11a01


So I decided to move to mplayer and thus did:

> apt-get install mplayer-386

 but whatever I try to play (even audio or video with whatever format) I get this error msg:

> MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel Pentium M Banias (Family: 6, Stepping: 5)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for Debian.


Option Creating needs a parameter at line 1


Is there anybody that can help me with these problems?
Regards,
Alfredo

---

### Post by Moonhill on 2006-03-18
In my case, I couldn't make it work with totem. So I turned to mplayer with no problem.

1. uninstall all totem
2. install mplayer-586 through synaptics package installer with mplayer-font
3. install w32codecs..you can check wiki or some where here to download w32codecs. It's *.deb file. So you can install it 'sudo dpkg -i w32*'
4. You can change skin using other skin package..you can find the link somewhere here by searching 'mplayer skin'. Uncompress it under /home/{user}/.mplayer/Skin

---

### Post by buttari on 2006-03-18
done. mplayer still gives the same error as before.

---

