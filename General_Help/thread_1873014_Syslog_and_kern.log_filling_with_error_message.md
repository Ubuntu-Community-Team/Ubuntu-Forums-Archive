---
title: "Syslog and kern.log filling with error message"
date: 2011-10-31
forum: General Help
---

### Post by JoeDesertrat on 2011-10-31
Both my syslog and my kern.log keep repeating this message (GB's worth) over and over:

[drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times

My hard drive starts at around 69% full at the start of a session but fills up to 100%. If I delete the older syslogs and kern.log I gain temporary space but the problem recurs.

Any idea what this error is and what I can do to solve the issue?

---

### Post by JoeDesertrat on 2011-12-21
OK, I found a solution to this a few days ago. My kern.log and syslog are now remaining at normal sizes instead of filling up to GB's in size.  Unfortunately, I forgot to save the link where the discussion was but here's what I found. Simply create a text file named .drirc in your home directory. The file should contain the following text:


<driconf>
    <device screen="0" driver="dri2">
        <application name="Default">
            <option name="vblank_mode" value="0" />
        </application>
    </device>
</driconf>

---

