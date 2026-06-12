---
title: "flickering laptop monitor after switching TTYs"
date: 2009-10-12
forum: General Help
---

### Post by trancegoa on 2009-10-12
Hello

I downgraded my laptop OS to ubuntu hardy (8.04) to take advantage of my old graphics card (ati mobility radeon X700) and everything were smoothly until i tried to go console (alt+ctrl+f1) and then go back to x windows (ctrl+alt+f7). The funny thing is i can take screenshots and they're displayed correctly so it's made me think it's all about my screen frequency goes unsynchronized when changing between framebuffer and gnome (fglrx). If i wanted to recover my x session i would have to do ctrl + alt + backspace what is a rather annoying since i need consoles quite often

I've tried to edit xorg.conf with "get-edid | parse-edid" command to state on the monitor section the proper vrefresh, hsync, timing values; I've also tried to change fb modes (791,771,795, etc), deactivate usplash, etc without results...

any ideas?

i also noticed that timings for my monitor look different depending on where i am:
```

fbset --show
mode "640x480-73"
    # D: 30.720 MHz, H: 36.923 kHz, V: 73.260 Hz
    geometry 640 480 640 480 32
    timings 32552 80 32 16 4 80 4
    rgba 8/16,8/8,8/0,0/0
endmode

xorg.conf (get-edid | parse-edid)
    Mode     "1440x900"    # vfreq 59.939Hz, hfreq 54.665kHz
        DotClock    96.210000
        HTimings    1440 1504 1536 1760
        VTimings    900 903 906 912
        Flags    "-HSync" "-VSync"
    EndMode

```

---

