---
title: "Subtitling by DVDStyler makes Japanese characters garbled"
date: 2011-06-14
forum: General Help
---

### Post by japboy on 2011-06-14
Hello.

I'm now creating a slideshow DVD by DVDStyler. It's a quite good software to create DVD-Video!

However, I have a problem about subtitle. DVDStyler just doesn't allow me to put Japanese subtitle. It actually works without errors, though the the DVD always shows the subtitle with garbled Japanese characters.

I guess it is caused by *spumux* because DVDStyler log always shows something like this:

```
INFO: font name "TakaoPGothic.ttf" matches font file /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
```

I certainly chose a Japanese font for Japanese subtitle, but *spumux* somehow switches to an English font to generate the subtitle...

Anyone got the same or similar problem? Is everyone able to draw non-English subtitle with DVDStyler?

Any helps are appreciated! Thanks in advance.

**UPDATE:**

I'm creating the subtitle file with Aegisub, and I export the file as SRT, then I load it from DVDStyler 1.8.3 with my slideshow VOB file created by Imagination 3.0.

**UPDATE #2:**

Thanks to Rattus Norvegicus, problem's solved.

Just make sure if preferred fonts you've chosen in DVDStyler are existed in both of *~/.fonts* and *~/.spumux* directories. I've confirmed this solved my problem!

---

### Post by Rattus Norvegicus on 2011-10-08
Did You ever find a solution to this?

I have the same problem, no matter what font I select, it's always using the DejaVuSans.ttf, wich i a really ugly font for subtitles.

---

### Post by japboy on 2011-10-08
Not really. I just gave up to put Japanese subtitle into a DVD.
Maybe we should wait for spumux updates...

---

### Post by Rattus Norvegicus on 2011-10-08
Shortly after I made my post, I've managed to solve my problem.

The fonts I want to use was already in the .spumux folder, but they where missing in the .fonts folder (in my home-folder), so after I copied the files to the .fonts folder, DVDStyler used my selected font and not just the DejaVuSans :D

Try see if youre TakaoPGothic.ttf is in the /home/user/.fonts folder.

EDIT:
I've just found out that the font has to be in both the .spumux AND the .fonts folder.

---

