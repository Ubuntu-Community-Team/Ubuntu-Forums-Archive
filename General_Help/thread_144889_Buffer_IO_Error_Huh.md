---
title: "Buffer I/O Error? Huh?"
date: 2006-03-15
forum: General Help
---

### Post by aspenbus on 2006-03-15
I turned on my other computer a few minutes ago and during the startup process, it said something about something being mounted 30 times and forcing a check, and then I got screensful of this:
("x" = random number)

[xxxxxxx.xxxxxx] Buffer I/O error on device dm-0, logical block xxxxxx1
[xxxxxxx.xxxxxx] Buffer I/O error on device dm-0, logical block xxxxxx2
[xxxxxxx.xxxxxx] Buffer I/O error on device dm-0, logical block xxxxxx3
[xxxxxxx.xxxxxx] Buffer I/O error on device dm-0, logical block xxxxxx4[xxxxxxx.xxxxxx] Buffer I/O error on device dm-0, logical block xxxxxx5
[xxxxxxx.xxxxxx] Buffer I/O error on device dm-0, logical block xxxxxx6
etc., etc.

I left the room to come online on the other computer (the comp with Ubuntu won't recognize my network card, and I don't know how to fix that), and I just went back into that room to see if the errors had ended, and the screen was completely black (not a screensaver). Should I be worried? What is this?

(As usual, please assume I'm an idiot and use small words - I don't really "get" Ubuntu, I've been using Windows for thirteen years :mrgreen: )

---

### Post by JustRandomName on 2006-03-15
After mounting your root partion 30 times, there is a forced scan to check that everything is ok.

This could be a sign of dead/dieing hard drive.

Have you got DMA enabled? DMA sometimes causes I/O errors, try disabling

To check if you have DMA enabled try:
```
$ sudo hdparm /dev/hda 
```

If it returns that it is enabled then the following command will disable it:

```
$ sudo hdparm -d0 /dev/hda
```

NOTE: Disabling DMA usually means your system will take a huge performance drop

---

### Post by aspenbus on 2006-03-15
I did have DMA enabled, and have disabled it... hopefully that'll fix it. Thank you very much!

---

