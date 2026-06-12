---
title: "PDF printing creates 'blank' docs"
date: 2006-05-04
forum: General Help
---

### Post by bsmith1051 on 2006-05-04
I followed the instructions in this HOW-TO,
  [http://www.ubuntuforums.org/showthread.php?t=140815](http://www.ubuntuforums.org/showthread.php?t=140815)
and I now have a printer selection available.  But I have a couple of problems which make it unusable:

1. the built-in PDF reader shows blank, or corrupted-looking, results.  I tried emailing one of them to a Windows machine, though, and it looks fine.  So there's something wrong with the built-in viewer?  Clearly, it doesn't help me with my own machine.

2. it doesn't prompt me where or how to save the file, and I haven't been able to find a HOW-TO that fixes it.  Is this even possible?  I'm accustomed to the 'real' Acrobat on Windows, which prompts for a file/path every time you print.

Any suggestions are appreciated!

---

### Post by WrathofthePenguin on 2006-05-05
[QUOTE=bsmith1051]I followed the instructions in this HOW-TO,
  [http://www.ubuntuforums.org/showthread.php?t=140815](http://www.ubuntuforums.org/showthread.php?t=140815)
and I now have a printer selection available.  But I have a couple of problems which make it unusable:

1. the built-in PDF reader shows blank, or corrupted-looking, results.  I tried emailing one of them to a Windows machine, though, and it looks fine.  So there's something wrong with the built-in viewer?  Clearly, it doesn't help me with my own machine.

2. it doesn't prompt me where or how to save the file, and I haven't been able to find a HOW-TO that fixes it.  Is this even possible?  I'm accustomed to the 'real' Acrobat on Windows, which prompts for a file/path every time you print.

Any suggestions are appreciated![/QUOTE]


Ok, I've been dealing with something very similar. I set up the pdf printer and found that Evince (the built-in pdf viewer) didn't display the pdf file correctly. I found what you found - when I moved the pdf file over to my windows machine and used Adobe Acrobat Reader to open it, it looked fine. So, my solution was to install the Linux version of Adobe Acrobat. I tried downloading it directly from Adobe (because I like to make my own life difficult and learn), installed it, but found that it wouldn't run. The banner would come up and disappear, but the actual viewer wouldn't come up. So I took somebody's suggestion and installed it from Synaptic (I did not use Automatix, which installs a lot more than I really want). It's called acroread, but it's the actual Adobe program. It opens fine now, and the pdfs view correctly.

---

