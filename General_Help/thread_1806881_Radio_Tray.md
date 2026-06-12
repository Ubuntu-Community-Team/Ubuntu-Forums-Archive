---
title: "Radio Tray"
date: 2011-07-18
forum: General Help
---

### Post by Rytron on 2011-07-18
Hi.

I love the program 'Radio Tray'. It was working fine until recently. This is the error I get:

```
$ radiotray

(process:3028): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/radiotray", line 7, in <module>
    from radiotray import radiotray
  File "/usr/lib/pymodules/python2.6/radiotray/radiotray.py", line 6, in <module>
    from RadioTray import RadioTray
  File "/usr/lib/pymodules/python2.6/radiotray/RadioTray.py", line 23, in <module>
    from AudioPlayerGStreamer import AudioPlayerGStreamer
  File "/usr/lib/pymodules/python2.6/radiotray/AudioPlayerGStreamer.py", line 25, in <module>
    from StreamDecoder import StreamDecoder
  File "/usr/lib/pymodules/python2.6/radiotray/StreamDecoder.py", line 21, in <module>
    from lib.common import USER_AGENT
  File "/usr/lib/pymodules/python2.6/radiotray/lib/common.py", line 4, in <module>
    import i18n
  File "/usr/lib/pymodules/python2.6/radiotray/lib/i18n.py", line 8, in <module>
    LC_ALL = locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
```

How can I remedy this?

Thanks.

---

### Post by timgood on 2011-07-18
Have you tried:

```
rm -rf .local/share/radiotray/config.xml
``` and then restarting the application? I seem to remember this worked for me when I had similar problems.

---

### Post by Rytron on 2011-07-18
> **timgood said:**
> Have you tried:

```
rm -rf .local/share/radiotray/config.xml
``` and then restarting the application? I seem to remember this worked for me when I had similar problems.

Hey timgood. No change.

---

### Post by timgood on 2011-07-18
What happens if you:

```
locale
```?

Does it complain?

If it does then:

```
sudo dpkg-reconfigure locales
```

---

### Post by Rytron on 2011-07-18
> **timgood said:**
> What happens if you:

```
locale
```?

Does it complain?

If it does then:

```
sudo dpkg-reconfigure locales
```

I ran **sudo dpkg-reconfigure locales** but the output stays the same:
```
$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_IE
LANGUAGE=
LC_CTYPE="en_IE"
LC_NUMERIC="en_IE"
LC_TIME="en_IE"
LC_COLLATE="en_IE"
LC_MONETARY="en_IE"
LC_MESSAGES="en_IE"
LC_PAPER="en_IE"
LC_NAME="en_IE"
LC_ADDRESS="en_IE"
LC_TELEPHONE="en_IE"
LC_MEASUREMENT="en_IE"
LC_IDENTIFICATION="en_IE"
LC_ALL=
```

:confused:

Edit: As a side note; I notice that when I launch VLC from the terminal I get this (VLC runs fine but I cannot upgrade it):
```
vlc
VLC media player 1.0.6 Goldeneye

(process:8744): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
```

What is this '**locale**'? It seems to be the prime suspect.

---

### Post by timgood on 2011-07-18
[This page]("http://ubuntuforums.org/showthread.php?t=1784922&highlight=locales+problem") may help you. Let me know if it does. Locales sets the encoding for installed languages on your system. In your case it should be en_IE (Irish English) but it's obviously broken in some way.

---

### Post by Rytron on 2011-07-19
> **timgood said:**
> [This page]("http://ubuntuforums.org/showthread.php?t=1784922&highlight=locales+problem") may help you. Let me know if it does. Locales sets the encoding for installed languages on your system. In your case it should be en_IE (Irish English) but it's obviously broken in some way.

I used this code and radiotray was working again:
```
export LANGUAGE=en_US.UTF-8
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
locale-gen en_US.UTF-8
sudo dpkg-reconfigure locales
```

Then after a reboot, radiotray has stopped working again so the code only has a temporary effect.

---

### Post by Rytron on 2011-07-19
I followed the advice here: [https://bugs.launchpad.net/lightdm/+bug/797249](https://bugs.launchpad.net/lightdm/+bug/797249)

I slighted tweaked the code to get this, rebooted and radiotray still works

```
sudo dpkg-reconfigure locales
sudo locale-gen en_IE
sudo update-locale LANG=en_IE.UTF8
```

Type ```
locale
``` to get below output (no errors)
```
locale
LANG=en_IE
LANGUAGE=
LC_CTYPE="en_IE"
LC_NUMERIC="en_IE"
LC_TIME="en_IE"
LC_COLLATE="en_IE"
LC_MONETARY="en_IE"
LC_MESSAGES="en_IE"
LC_PAPER="en_IE"
LC_NAME="en_IE"
LC_ADDRESS="en_IE"
LC_TELEPHONE="en_IE"
LC_MEASUREMENT="en_IE"
LC_IDENTIFICATION="en_IE"
LC_ALL=
```

---

### Post by timgood on 2011-07-20
Well done mate. Glad you managed to get it sorted.

---

