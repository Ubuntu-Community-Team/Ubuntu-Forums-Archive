---
title: "Sub-pixel smoothing"
date: 2010-10-29
forum: General Help
---

### Post by JetteV on 2010-10-29
I'm still using Ubuntu 10.04 as I haven't worked up the patience to upgrade just yet:
Linux jette-pv 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64 GNU/Linux

I've been having trouble with subpixel smoothing recently, and I'm beginning to think it may be a bug rather than my own screw-ups.

I can't stand subpixel AA, as I find it too easy to see the colored pixels at the edges of the fonts. I've tried various ways to turn it off, with varying degrees of effectiveness. In some programs (mainly Firefox and Thunderbird), it's remained entirely disabled. On almost everything else, including all the Gnome programs, the terminal and gvim, it's still pretty evident.

My ~/.fonts.conf file contains the following:

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
    <edit name="rgba" mode="assign">
        <const>none</const>
    </edit>
</match>
</fontconfig>

```My /etc/fonts/conf.d folder contains all the following:

```

10-antialias.conf
10-no-sub-pixel.conf
20-fix-globaladvance.conf
20-unhint-small-vera.conf
30-defoma.conf
30-metric-aliases.conf
30-urw-aliases.conf
40-nonlatin.conf
45-latin.conf
49-sansserif.conf
50-user.conf
51-local.conf
60-latin.conf
64-ttf-thai-tlwg.conf
65-fonts-persian.conf
65-khmer.conf
65-nonlatin.conf
69-unifont.conf
70-no-bitmaps.conf
80-delicious.conf
89-ttf-thai-tlwg-synthetic.conf
90-synthetic.conf
90-ttf-bengali-fonts.conf
90-ttf-devanagari-fonts.conf
90-ttf-gujarati-fonts.conf
90-ttf-kannada-fonts.conf
90-ttf-malayalam-fonts.conf
90-ttf-oriya-fonts.conf
90-ttf-punjabi-fonts.conf
90-ttf-tamil-fonts.conf
90-ttf-telugu-fonts.conf
99pdftoopvp.conf
README

```All of them are symlinks to their respective files in ../conf.avail except for 65-khmer, 99pdf and the README file. I didn't create any of those three, so I assume it's set that way for a reason. Most of the ones I haven't placed there don't have anything to do with subpixel smoothing according to the comments.

I've looked through the Ubuntu wiki as well as wikis and forums for other Linux distributions (some quite comprehensive), and have followed any instructions I could find, but as of yet most programs still use sub-pixel rendering, even after restarting X (and later the entire computer). Everything is up to date according to apt-get, except for the linux-generic, linux-headers-generic and linux-image-generic packages, which I'm guessing have to do with the kernel and probably don't affect something as mundane as font settings.

Aside from Firefox and other Mozilla suite apoplications, the only program I've noticed that obeys the sub-pixel settings is XeTeX, which I believe uses something entirely different from FreeType.

Freetype --version says 9.22.3, --ftversion gives 2.3.11.

Any help would be appreciated.

---

