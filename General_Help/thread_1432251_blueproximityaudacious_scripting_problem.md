---
title: "blueproximity/audacious scripting problem"
date: 2010-03-17
forum: General Help
---

### Post by whiterabbit7500 on 2010-03-17
I'm running a custom script with Blueproximity to auto-lock my screen whenever I walk away, and I had it set to auto-pause/play on Amarok as well. I've switched over to Audacious for the much sleeker UI and close feel to Winamp. I'm using audtool2 to control it, and using the below code in my script:
```
#!/bin/sh
PATH=$PATH:/opt/kde3/bin:/usr/bin
echo ${KDE_SESSION_VERSION}
case "$1" in
        lock)
                if [ -n ${KDE_SESSION_VERSION} ] && [ "$KDE_SESSION_VERSION" -eq 4 ]; then
                        echo "KDE4 detected do the magic..."
                        ####qdbus org.freedesktop.ScreenSaver /ScreenSaver Lock #one way
                        # better way bellow (unified) - should work with gnome too (gnome users please test)
                        dbus-send --type=method_call --dest=org.freedesktop.ScreenSaver /ScreenSaver org.freedesktop.ScreenSaver.Lock
                        # Dear NVIDIA shitty drivers so don't use this one too often
                        #xset dpms force off
			#audacious pause
			audtool2 playback-pause
                else
                        echo "KDE3 detected do the magic..."
                        dcop kdesktop KScreensaverIface lock
                fi
                ;;
        unlock)
                if [ -n ${KDE_SESSION_VERSION} ] && [ "${KDE_SESSION_VERSION}" -eq 4 ]; then
                        echo "KDE4 detected do the magic..."
                        dbus-send --type=method_call --dest=org.freedesktop.ScreenSaver /ScreenSaver org.freedesktop.ScreenSaver.SetActive boolean:false
                        # Dear NVIDIA shitty drivers so don't use this one too often
                        xset dpms force on
			#audacious play
			audtool2 playback-play
                else
                        # KDE 3
                        echo "KDE3 detected do the magic..."
                        dcop kdesktop KScreensaverIface quit
                fi
                ;;
        *)
                echo "usage of $0:"
                echo " $0 (lock|unlock)"

esac
```

My problem is that Audacious opens, and plays, but it starts play again every second or so. I'm assuming that each time blueproximity checks to see if the phone is within range, it reloads the script and begins play again. Is there any options I can set, or any ideas to avoid this problem?

---

