---
title: "Can i use Notify in a script"
date: 2010-03-19
forum: General Help
---

### Post by cbaughman on 2010-03-19
I was hoping to have a pop up come up after my rssdler completes, I was hoping for the nice pop ups that Ubuntu for brightness, audio volume, instant messages ect, i think it's called notify but i'm still figuring things out. 

Is there a way i can write this into my rssdler start up script? or any other script i'm writing?

Thanks

---

### Post by rnerwein on 2010-03-19
hi
have a looku at: man zenity
here is a little example you can place in a script. this example pops up a window and wait for klick ok/no. but you can do much more with zeinity.
/usr/bin/zenity  --question --title='=> little message <=' --text='time for a break'
cia

---

### Post by ciscosurfer on 2010-03-19
> **cbaughman said:**
> I was hoping to have a pop up come up after my rssdler completes, I was hoping for the nice pop ups that Ubuntu for brightness, audio volume, instant messages ect, i think it's called notify but i'm still figuring things out. 

Is there a way i can write this into my rssdler start up script? or any other script i'm writing?

ThanksI believe Notify OSD is what you are thinking of. It might be easier to use zenity for a quick pop-up alert though.

[Notify OSD Design Spec]("https://wiki.ubuntu.com/NotifyOSD")
[Notification Development Guidelines]("https://wiki.ubuntu.com/NotificationDevelopmentGuidelines")
See the man pages for some examples of zenity in action; searching the forums for keyword "zenity" should also prove useful.

---

### Post by kerry_s on 2010-03-19
does notify-send work with notify-osd? i use the old notification so can't test, you need libnotify-bin installed.

---

### Post by stinkeye on 2010-03-19
notify-send is included in the libnotify-bin package.
I use this in a script for conky which also plays a sound file.
```
notify-send -i ~/conky/gmail2.png "Gmail" "You have new mail" &
play -q ~/Sounds/message.wav
```

For the play command to work you need to install sox.

---

### Post by cbaughman on 2010-03-19
I looked at zenity But was hoping for something that would pop up in the little less intrusive way. Looks like notify-sends is what i'm looking for. thanks i'll give that a try.

---

