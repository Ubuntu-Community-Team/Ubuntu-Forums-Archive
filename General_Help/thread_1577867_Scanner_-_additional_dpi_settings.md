---
title: "Scanner - additional dpi settings?"
date: 2010-09-19
forum: General Help
---

### Post by 2CV67 on 2010-09-19
I have an Epson V200 scanner.

The Epson Avasys Iscan application for this scanner offers a bewildering selection of dpi settings:
50/72/96/150/200/240/266/300/350/360/400/600/720/800/1200/1600/2400/3200!

I haven't tested all of them, but the extremes & the useful ones in between seem to really work.

The Ubuntu scanner applications don't offer an adequate selection of dpi's.
XSane - 300/2400/4800
AcquireImages - 300/2400/4800
Simple Scan offers 75/150/300/600/1200/2400 but whatever I select I get the same result!

So:
1. Is there any way of getting a bigger choice of dpi's in XSane & AcquireImages?
2. Any idea why Simple Scan dpi selections don't work?

Thanks for any clues!

---

### Post by 2CV67 on 2011-04-29
Bump...

Anybody know where XSane finds/keeps its dpi settings?
Can I get at that source & maybe modify it?

Thanks for any suggestions!

---

### Post by 2CV67 on 2011-07-18
Just upgraded to 11.04 & rechecked my scanner options.
- Acquire Images
- Simple Scan
- XSane
- Iscan
None of which is really satisfactory.

XSane now offers me more dpi's:
X: 75-300-600-1200-2400-4800
Y: 100-200-300-400-600-800-1200-1800-3600-4800-6600-9600

Much better than last year, but still strange.
To keep 1:1 aspect ratio, that only leaves 300-600-1200-4800.

Sure, I can live with that.
And I know I can re-scale the image back to 1:1 but what a fiddle!
For casual use, I would like a bit more 1:1 choice in the 100-150-200 dpi range.

Is there any way I can change or create dpi's in XSane?
Knowing Iscan offers me 1:1 scanning at 50-72-96-150-200-240-300-360-400-600-720-800-1200-1600-2400-3200-4800-6400-9600dpi with the same scanner in the same Ubuntu...

Thanks for any suggestion!

---

### Post by 2CV67 on 2011-08-12
Bump...
> **2CV67 said:**
> XSane now offers me more dpi's:
X: 75-300-600-1200-2400-4800
Y: 100-200-300-400-600-800-1200-1800-3600-4800-6600-9600

Is there any way I can change or create dpi's in XSane?

Or, to remove another minor irritation; Is there any way to get XSane to remember my preference for 300x300dpi instead of opening every time with 75x100dpi?

If I could just find where XSane keeps its list...

Thanks for any clues!

---

### Post by demonipuch on 2011-08-14
> **2CV67 said:**
> Bump...


Or, to remove another minor irritation; Is there any way to get XSane to remember my preference for 300x300dpi instead of opening every time with 75x100dpi?

If I could just find where XSane keeps its list...

Thanks for any clues!

Hello

Launch xsane. Change the scanner resolution and make ctrl+P to save the settings. 

The preferences file for your scanner is located in /home/user/.sane/xsane

---

### Post by 2CV67 on 2011-08-14
Thanks very much for that suggestion, demonipuch, but it is not working yet...

I went to .sane/xsane & found a file "Epson:PerfectionV200.drc" which has these lines:
"x-resolution"
75
"y-resolution"
100

In XSane Preferences, I selected 300x300 & "Save device settings" (=Ctr+P).
The V200.drc file then showed 300x300 & I thought the job was done.

On closing & re-opening XSane to check, I was surprised to find it back to 75x100!

Further playing showed the following:
Every time I close XSane, then the V200.drc file is updated to the current dpi settings, even when I do not save anything.
Every time I open XSane, it comes up with 75x100, whatever the V200.drc file says at that time!

Puzzled...

---

### Post by demonipuch on 2011-08-16
I fail to see what's wrong...This should be working...At least it is, for me...
Good luck

---

### Post by 2CV67 on 2011-08-16
I also fail to see what's wrong!

I just tried completely removing & re-installing XSane & XSane-common (same versions) with SynApt, but nothing changed.

I really need some expert advice!

---

