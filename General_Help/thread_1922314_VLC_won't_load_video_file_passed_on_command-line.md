---
title: "VLC won't load video file passed on command-line"
date: 2012-02-08
forum: General Help
---

### Post by Carl Foxmarten on 2012-02-08
I'm not sure when this happened, but I just recently discovered that VLC isn't loading the video file passed by the command line, which means that it's loading up blank when launching a video file that was associated with VLC.

I get this stuff on the command line:```

$ vlc sample.ogv
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9d3b8fc] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to setenv("ORBIT_SOCKETDIR", "/tmp/orbit-dvanhumb", 1)
Warning: call to srand(1328653041)
Warning: call to rand()
Blocked: call to setlocale(6, "")
```
I'm not sure what it all means, either.

Does anybody have suggestions?
I'm running VLC 1.1.9 on XUbuntu Natty Narwhal.

---

### Post by jamesisin on 2012-02-08
Do you have permissions to access the file?  Can you open it in VLC directly?

---

### Post by Carl Foxmarten on 2012-02-09
Yes, I have read permissions for the file.
It plays just fine if I use the Open File dialog.

But not if I pass it in as a parameter.

---

### Post by winh8r on 2012-02-09
Looks similar to this problem:


[http://ubuntuforums.org/showthread.php?p=10171212#post10171212]("http://ubuntuforums.org/showthread.php?p=10171212#post10171212")


might be some help to you.

---

