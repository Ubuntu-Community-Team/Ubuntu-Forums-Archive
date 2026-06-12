---
title: "Sound missing in Totem, but present in VLC &amp; Ogle"
date: 2006-05-04
forum: General Help
---

### Post by georgetoon on 2006-05-04
When I play a DVD in Totem, parts of the soundtrack are missing, mainly the dialog soundtrack.  When the same DVD is played in VLC or Ogle, all the sound is present.  how can I get totem to play all the sound?

---

### Post by Al3xanR0 on 2006-05-04
ConfigureTotem to use the same soud driver as VLC and Ogle. For example, if Ogle uses oss or alsa or esd have Totem use it also.

---

### Post by georgetoon on 2006-05-04
[QUOTE=Al3xanR0]ConfigureTotem to use the same soud driver as VLC and Ogle. For example, if Ogle uses oss or alsa or esd have Totem use it also.[/QUOTE]

Yes, I'd like to do this, but as far as I can see, Totem does not have any way for me to configure this option via its GUI.  Is there another way to configure? Or am I overlooking a control...toggling something on which gives me more options?

---

### Post by harishg on 2006-05-04
which version of totem do you use for gui.There is a totem-gstreamer and totem-xine version.I also had problems with totem when i first installed it and when i changed my totem player it worked fine.

---

### Post by georgetoon on 2006-05-04
[QUOTE=harishg]which version of totem do you use for gui.There is a totem-gstreamer and totem-xine version.I also had problems with totem when i first installed it and when i changed my totem player it worked fine.[/QUOTE]

I'm using Totem 1.2.1 Movie Player using xine-lib version 1.0.1

---

### Post by pixelat3d on 2006-05-06
~/.gnome2/totem_config

-- SNIP --
# audio driver to use
# string, default: auto
#audio.driver:auto
-- END SNIP -- 

esd, oss, and alsa are your best options here, don't forget to make sure you're using totem-xine and have libdvdcss installed. Also, don't forget to uncomment the line (remove the #) so your changes actually mean something. 

Good luck = )

---

### Post by georgetoon on 2006-05-06
[QUOTE=pixelat3d]~/.gnome2/totem_config

-- SNIP --
# audio driver to use
# string, default: auto
#audio.driver:auto
-- END SNIP -- 

esd, oss, and alsa are your best options here, don't forget to make sure you're using totem-xine and have libdvdcss installed. Also, don't forget to uncomment the line (remove the #) so your changes actually mean something. 

Good luck = )[/QUOTE]

Thanks for all this.:)

I was fiddling around with totem last night and noticed that the sound profile was not what it should be.  Duh!  I changed from 5.1 to 4.1, rebooted the program and things are fine.:)

---

