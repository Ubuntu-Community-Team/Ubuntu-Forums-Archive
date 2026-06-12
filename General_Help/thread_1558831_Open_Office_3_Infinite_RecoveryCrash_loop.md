---
title: "Open Office 3 Infinite Recovery/Crash loop"
date: 2010-08-22
forum: General Help
---

### Post by tiggsy on 2010-08-22
Whenever I try to open an existing spreadsheet (of which I have around a dozen or so I use regularly), I get a recovery screen for Untitled and when I say to recover it, the system crashes.

I have tried using the fix here [http://ubuntuforums.org/showthread.php?t=830508](http://ubuntuforums.org/showthread.php?t=830508) (deleting Recovery.xcu)

I have tried removing the .openoffice.org folder in my home folder as described here: [http://ubuntuforums.org/showthread.php?t=948294](http://ubuntuforums.org/showthread.php?t=948294) but I can't install oo 3.2 as a fix, as I'm already running 3.2

I tried opening a spreadsheet using the terminal as described here: [http://ubuntuforums.org/showthread.php?t=1158409](http://ubuntuforums.org/showthread.php?t=1158409) but got the recovery screen prompt again. I ran the recovery, got a "success" screen, followed by the usual crash notification. There were no errors shown in the terminal.

Then I removed the ~lock file and the Recovery.xcu file again - ran the same command in the terminal and got a message that the system had crashed and next time "the following files will be recovered" but there were no files listed at all! And still no error messages in termainal.

So then I tried reinstalling OO, then I opened it, tried to open an existing spreadhseet - crash!

I tried everything discussed here: [http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=12426](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=12426) but no effect. One point though. I renamed the userprofile from user to olduser, but I was not prompted whether to transfer personal data, and when I looked, there was no new "user" folder, just the "olduser" which I guess it must have been using. So i moved it elsewhere, and tried that again, and although it created a new "user" folder this time, I was still not asked if i wanted to transfer personal data as described.

I don't have any extensions installed, so far as I can recall. I use Open Office Calc every day, so if this was a problem with anything installed long enough ago to have forgotten, I think it would have happened long before this.

The instructions here: [http://www.oooforum.org/forum/viewtopic.phtml?p=156335#156335](http://www.oooforum.org/forum/viewtopic.phtml?p=156335#156335) were similar to some I've done before. My backup folder was empty in any case, and I can't find a file Recovery.dat but I have deleted Recovery.xcu very many times

---

### Post by williamson389 on 2010-09-20
This same problem happens to me. I am able to get by using hotkeys, such as s for start, then enter for finish.  hopefully this will be worked out.

---

