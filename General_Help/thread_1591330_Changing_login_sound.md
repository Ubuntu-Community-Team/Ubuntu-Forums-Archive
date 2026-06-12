---
title: "Changing login sound?"
date: 2010-10-09
forum: General Help
---

### Post by roger465 on 2010-10-09
I'm fluent in Windoze, but new to Linux. Thought I'd try and do a few basic things, but got stuck at the first hurdle! Basically, I've tried to change my startup sound. What I did was this:
 

 
[LIST=1]
[*]I went to System &#8211; Preferences &#8211;     Startup Applications.
[*]Gnome Login sound.
[*]Path is shown as     /usr/share/sounds/ubuntu/stereo/desktop-login.ogg.
[*]I copied my desired startup sound     (the old W98 one, which I really like &#8211; call me retro) into     /usr/share/sounds/ubuntu/stereo/.
[*]Edited the path above to     /usr/share/sounds/ubuntu/stereo/98.ogg.
[/LIST]
 

 However... when I log in now, all I get is silence.
 

 What have I done wrong please!
 

 Thanks  :)

---

### Post by sendblink23 on 2010-10-09
> **roger465 said:**
> I'm fluent in Windoze, but new to Linux. Thought I'd try and do a few basic things, but got stuck at the first hurdle! Basically, I've tried to change my startup sound. What I did was this:
 

 
[LIST=1]
[*]I went to System &#8211; Preferences &#8211;     Startup Applications.
[*]Gnome Login sound.
[*]Path is shown as     /usr/share/sounds/ubuntu/stereo/desktop-login.ogg.
[*]I copied my desired startup sound     (the old W98 one, which I really like &#8211; call me retro) into     /usr/share/sounds/ubuntu/stereo/.
[*]Edited the path above to     /usr/share/sounds/ubuntu/stereo/98.ogg.
[/LIST]
 

 However... when I log in now, all I get is silence.
 

 What have I done wrong please!
 

 Thanks  :)

hehe I'm also interested on this...

I'm on 10.10 RC (pretty certain tomorrow I'll update to final 10.10)  but according to my *Startup applications on "Gnome login Sound"  the command I see in edit its: /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

So I'd guess its different than yours right?

---

### Post by roger465 on 2010-10-09
Hhmmm, certainly looks different, doesn't it! Maybe I should edit mine to look more like yours...

> **sendblink23 said:**
> hehe I'm also interested on this...

I'm on 10.10 RC (pretty certain tomorrow I'll update to final 10.10)  but according to my *Startup applications on "Gnome login Sound"  the command I see in edit its: /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

So I'd guess its different than yours right?

---

### Post by lightningfox on 2010-10-09
See this thread:  [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1520547](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1520547)

---

### Post by roger465 on 2010-10-09
Maybe I should use that as my login sound!
 

 Thanks, that sorted it. I must have carelessly edited it without looking. Beside the command line there's a Browse button, which I stupidly assumed meant that you could browse to the file you wanted for a login sound... and it doesn't work that way at all, does it!
 

 Thanks. All I need to do now is figure out how to stop OpenOrifice Writer bringing up the paragraph formatter every few words as I type. Could it be possible that something Microsoft (Turd) might actually be better, in some way, than something else?

---

### Post by sendblink23 on 2010-10-09
> **roger465 said:**
> Maybe I should use that as my login sound!
 

 Thanks, that sorted it. I must have carelessly edited it without looking. Beside the command line there's a Browse button, which I stupidly assumed meant that you could browse to the file you wanted for a login sound... and it doesn't work that way at all, does it!
 

 Thanks. All I need to do now is figure out how to stop OpenOrifice Writer bringing up the paragraph formatter every few words as I type. Could it be possible that something Microsoft (Turd) might actually be better, in some way, than something else?

Maybe you will need to play with WINE & install Microsoft Office 2007 (I mean plain *Word) :P

---

### Post by jogonjr on 2011-02-28
Why can I not find the gnome login sound nor the "desktop-login"
All I see is the canberra-gtk-play. Could anyone please direct me to where I could change the login sound?

---

### Post by Frogs Hair on 2011-02-28
Sound files are found in File System > usr/share/sound. The menu options are found in System > Preferences > Sound .

---

### Post by odh1412 on 2011-06-17
Hey. So I was messing around trying to figure out how to change the login sound and I 
added a file to the sounds/ubuntu or w/e folder (where  desktop-login.ogg) is stored and changed the gnome login sound settings  from 

"/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login""

to

/usr/bin/canberra-gtk-play --id="wos" --description="GNOME Login"  (wos being the name of my new file)

This did not work and no sound played.

I then changed the file name wos to desktop-login and changed the original settings.

Still. no sound.

I then tried to cut my losses and revert to the original settings with the original sounds but that wont even play. 

any suggestions?

Thanks.

---

