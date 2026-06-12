---
title: "Switching between line and mic"
date: 2010-05-02
forum: General Help
---

### Post by Graemej on 2010-05-02
I installed 10.04 LTS. I previously had Ubuntu 10.04 RS and had a separate line and mic control. There was an option in 10.04 RC in the Sound Options to change the Mic Input into a Line Input but it is not showing in 10.04 LTS.

I have only 1 audio input ports in the laptop: Capture.

Computer: Dell Inspiron E1505
Sound Card: Sigmatel STAC92xx

I have added the line: options snd-hda-intel model=dell-m44
to: /etc/modprobe.d/alsa-base.conf

I know this can go but can't understand why it does not in this installation. I would appreciate some help and I know that others have this problem too.
Thanks Graeme

---

### Post by Graemej on 2010-05-02
Here is some additional information which may help.

The first screenshot is of a good setup where there is a connector combo box for choosing the input.

the second is of my system where there is no combo box.

---

### Post by Graemej on 2010-05-02
Whoops! missed the second pic. Sorry - very new to this.

---

