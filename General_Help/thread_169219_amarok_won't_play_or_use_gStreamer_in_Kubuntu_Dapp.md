---
title: "amarok won't play or use gStreamer in Kubuntu Dapper"
date: 2006-05-02
forum: General Help
---

### Post by dan_kent on 2006-05-02
Hi all

I've got Kubuntu Dapper installed and amarok refuses to play files. When I load an Mp3 into it the timer skips ahead rapidly and no music comes out.
It's using the Xine engine, I've fiddiling with the options and i've tried running it with the arts engine.. I don't seem to be able to get gStreamer to install as an option however.

Anyone got any ideas?

---

### Post by trotski on 2006-05-02
Perhaps you might wanna try the 1.4 beta:

[http://kubuntu.org/announcements/amarok-1.4beta3.php](http://kubuntu.org/announcements/amarok-1.4beta3.php)

---

### Post by Neo Ex on 2006-05-02
Try [this](https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970)

---

### Post by dan_kent on 2006-05-03
I've tried both of these sugestions now.

The sudo apt-get install gstreamer0.10-plugins-ugly comes up as saying that gstreamer is already installed. However it's still not accessible form the engines drop down.

And Amarok 1.4 beta just crashes during the splash screen.

---

### Post by ComplexNumber on 2006-05-03
try 'gst-register' from the commandline.  that registers the plugins(mp3, ogg etc) with gstreamer and the various apps.

---

### Post by Neo Ex on 2006-05-03
I've forgotten that! I don't know how it is with GStreamer 0.10, but with 0.8 the command is 'gst-register-0.8'. I think it's 'gst-register-0.10'. Try to write gst-reg and then press tab ;)

---

### Post by ComplexNumber on 2006-05-03
[quote=Neo Ex]I've forgotten that! I don't know how it is with GStreamer 0.10, but with 0.8 the command is 'gst-register-0.8'. I think it's 'gst-register-0.10'. Try to write gst-reg and then press tab ;)[/quote] i don't seem to have gst-register for gstreamer 0.10. it was present for version 0.8, though. then again, i don't have the gst editor either where the user can construct the various multimedia 'pipelines'.

try gst-inspect. that gives a list of the installed plugins. maybe gstreamer 0.10 registers them automatically.

---

