---
title: "Sibelius for linux?"
date: 2005-02-15
forum: General Help
---

### Post by pilotcp on 2005-02-15
hello all,

is ther any plugin for firefox in linux to read sibelius music? i know windows has scorch...or is there any program for linux that can read sibelius music?


Thanks,
Charlie

---

### Post by turbotuba on 2007-04-08
bump:popcorn:

---

### Post by Grundlefleck on 2007-07-11
I'm currently looking to be able to do this as well. It's one of the (few) things still keeping me tied to XP, but I can't find a workaround.

I installed Firefox under Wine then attempted to download the Scorch plugin for it, but it didn't work. Granted my testing consisted of trying to load one page of sheet music from [www.sheetmusicdirect.com](www.sheetmusicdirect.com), so I don't know that it definitively doesn't work. Looks like it may just be a fault on the MIDI throughput for me.

Might be worth giving it a try though...

~ Grundlefleck

---

### Post by Grundlefleck on 2007-10-11
Got this working. 
Feisty Fawn running Firefox under WINE.

Also happened to come across directions after I got it working:
[https://answers.launchpad.net/ubuntu/+question/2762](https://answers.launchpad.net/ubuntu/+question/2762)

---

### Post by paker on 2007-11-25
Has anyone got this working?
If anyone did, please help me. I must have clicked a wrong button or something. Thanks.

---

### Post by rosencrantz on 2008-03-19
In my case (openSuSE, but that shouldn't make a difference), the Sibelius installer didn't ask for a browser location and put everything in [wine]C:\Program Files\Sibelius Software\Scorch\NetscapePlugin[/wine].

Moving all dlls to [wine]C:\Program Files\Mozilla Firefox\plugins[/wine] worked, though the result is really ugly, there are some serious font problems. Music staves are readable, anyway.

---

### Post by jespdj on 2008-03-19
I don't know what Sibelius can and cannot do and why you want to use it, but if you're looking for a music notation program, there are several options: denemo, mscore, noteedit (a KDE program). I have not tried them all so I don't know how good they are.

Have a look at [http://linux-sound.org/](http://linux-sound.org/) for a list of sound and MIDI software for Linux.

[Rosegarden](http://www.rosegardenmusic.com/) is also a nice music program.

---

### Post by rosencrantz on 2008-05-13
I think _the_ best music typesetter on Linux ist still [Lilypond]("http://lilypond.org") - output quality comparable to LaTeX and a similar philosophy. pilotcp's issue is that quite a lot of free sheet music on the web is in the proprietary Sibelius format and you need the Scorch browser plugin to read it.

---

