---
title: "Wifi and power management icone lost"
date: 2010-08-26
forum: General Help
---

### Post by Thanatosv on 2010-08-26
First of all hi to everybody and thanks for your answers. two weeks ago I lost my Wifi icone and next i also lost my Power management icone, although both softwares are still running because i still can navegate using my wifi and the monitor shows me that power managment programe is still running.
 
Can some one give me a hint please? at least to see if my battery is charged. it's very anoying. Thanks again.

---

### Post by afrowildo on 2010-08-26
Open up a console and enter this command (you don't have to be root)

```
rm -r ~/.gconf/apps/panel
```

Then log out and log back in. Your gnome panel should have reset itself to the default settings, bringing with it your WiFi and Power icons.

---

### Post by Thanatosv on 2010-08-26
hey thank you for the help, I entered the command and the panel did reset itself but the battery icon is still missing. 
Any other idea?
Thanks in advanced.

---

### Post by afrowildo on 2010-08-26
By default, the battery indicator won't appear if you are plugged in. If you go back into power management and select the **General** tab, then you'll get to choose how the battery indicator behaves.

---

### Post by Thanatosv on 2010-08-27
I tried with and without the battey pluged, I also entered the in the generat tab and finaly after a couple of rebooting I got back the battery indicator but now it's the Wifi icone that's lost... Any ideas? please.

---

### Post by afrowildo on 2010-08-27
I know this is going to sound like a stupid question, and I'm sorry if it sound a bit insulting, but are you actually connected to the WiFi at this point? If you're only connected using ethernet then the WiFi icon isn't going to appear (like the battery icon on AC power). Sorry, but I just have to eliminate this as a possibility.

If you are connected with WiFi, then this thread may be of some use

[http://ubuntuforums.org/showthread.php?t=828149](http://ubuntuforums.org/showthread.php?t=828149)

It's two years old at this stage, but the information may still be relevant.

---

### Post by Thanatosv on 2010-08-28
Don't worry I understand your question. And yes i always connect using WiFi that's the point.
I'm really thankful for your answers.
I'm going to read the link you sent me to see if i can solve my problem.
Again thank you.

---

### Post by Thanatosv on 2010-08-28
Ok problem solved!!
to get back the power icone I used the code that you sent me
Code:
rm -r ~/.gconf/apps/panel

And to get back the Wifi icone I used
 System -> Preferences -> Sessions
I clicked on the startup tab and entered
       nm-applet

And after i rebooted the session the icon was back.

Thanks a lot for your help afrowildo.

---

### Post by afrowildo on 2010-08-28
No problem at all, and welcome to the forums.

---

