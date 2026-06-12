---
title: "sound issues using veetle!"
date: 2010-04-23
forum: General Help
---

### Post by suli8 on 2010-04-23
hi there..
i left windows 2 months ago towards the freedom..!!:P
but im having an issue with veetle...
the sound quality is bad at first, and then after a while it goes better but with sound delay...about 4 seconds!

i dont know if i posted this in the right section, and if not im sorrry!
 
any ideas?
ubuntu 9.10

---

### Post by moore.bryan on 2010-08-24
If you're still looking for a fix, this worked for me. I don't remember where I got it, but I can't take credit for it...

You need to fix Veetle's VLC:
[list=1]
Backup the old Veetle VLC file:
```

mv ~/.veetle_vlc/vlc ~/.veetle_vlc/vlc_original

```
[/list]
[list=2]
Replace it with a fixed VLC:
```
nano ~/.veetle_vlc/vlc
```
Put this into that file:
```

#!/bin/bash
exec ~/.veetle_vlc/vlc_original --aout oss "$@"

```
Ctrl+x to close and save your new VLC file.
[/list]
[list=3]
Now, make the new VLC file executable:
```

chmod +x ~/.veetle_vlc/vlc

```
[/list]
You're done.

---

### Post by Jean Valjean on 2010-11-02
Hi,

This works fine on ubuntu 10.04 but not on 10.10. Do you know why it doesn't work anymore ?

Jean

---

### Post by Jean Valjean on 2010-11-02
Moreover do you know how I can read a veetle stream with VLC player ?

---

### Post by moore.bryan on 2010-11-02
Hmm... 10.10 probably doesn't handle sound the same way as 10.04 did. I know pulseaudio was supposed to take over, practically, everything in Maverick.

Have you searched high and low on the interweb?

---

### Post by Atiq Choudhry on 2010-11-25
> **moore.bryan said:**
> If you're still looking for a fix, this worked for me. I don't remember where I got it, but I can't take credit for it...

You need to fix Veetle's VLC:
[list=1]
Backup the old Veetle VLC file:
```

mv ~/.veetle_vlc/vlc ~/.veetle_vlc/vlc_original

```
[/list]
[list=2]
Replace it with a fixed VLC:
```
nano ~/.veetle_vlc/vlc
```
Put this into that file:
```

#!/bin/bash
exec ~/.veetle_vlc/vlc_original --aout oss "$@"

```
Ctrl+x to close and save your new VLC file.
[/list]
[list=3]
Now, make the new VLC file executable:
```

chmod +x ~/.veetle_vlc/vlc

```
[/list]
You're done.
Worked beautifully! I'm using Ubuntu 10.04. Appreciate your help. Thank you!

---

### Post by moore.bryan on 2010-11-27
Glad to know this at least still works on Lucid.

---

### Post by eightdollarbeer on 2011-09-18
every thing was working fine for me till i rebuilt firefox profile and had to reinstall veetle now its sync but crackles. i think i had some custom switches in there but forget what they were :) sooo bad idea to do that.
they have updated the plus version to use some mods i put on another board i believe the vlc file is different now . does anyone have an older copy of the .17 .

---

### Post by pawel.ad on 2011-11-11
> Hey Linux users - help us pre-test a new release for Linux! We put the old release on a diet, and it's down to about 8MB in size, includes better support for PulseAudio (you should no longer need to uninstall pulse to get audio synced up properly in linux) and works out of the box on my 64-bit Ubuntu. It will still show up as version 0.9.17 (we've got some added fixes we'd like to push out before applying the coveted 0.9.18 moniker) but you can get it in either of your favorite formats from:

[http://veetle.com/download.php/veetle-0](http://veetle.com/download.php/veetle-0) ... install.sh

[http://veetle.com/download.php/veetle-0.9.17plus.tgz](http://veetle.com/download.php/veetle-0.9.17plus.tgz)

If you do install it, let us know how it's working out for you! I'm calling this one "0.9.17+".

[Caveat: This is an experimental release! Not for the weak of heart! Don't install it unless you feel comfortable rolling up your sleeves and tinkering with your Linux box - or at the very least, wait until others confirm that it doesn't horribly break the website...]

[http://s1.veetle.com/forums/viewtopic.php?f=7&t=2312#p8845](http://s1.veetle.com/forums/viewtopic.php?f=7&t=2312#p8845)

---

