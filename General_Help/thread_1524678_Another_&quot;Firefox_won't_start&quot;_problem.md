---
title: "Another &quot;Firefox won't start&quot; problem"
date: 2010-07-05
forum: General Help
---

### Post by Achillobator on 2010-07-05
EDIT: Aha, found it on my own! I'd searched quite a few threads but somehow managed to miss [this one]("http://ubuntuforums.org/showthread.php?t=1414429"), and it seems to have fixed everything right up. I've closed and restarted Firefox several times now without having to enter safe mode, perform any workarounds or delete any files/folders first. The trick is apparently to delete Prism (hm, I guess it *is* related to my problems after all!). I don't know why this works, but it does. It's a shame because I do use a few Prism apps fairly regularly, but I can live without--I'll just try Chrome's site-specific browser thing instead. Thanks anyway, and hopefully that link will help anyone else with the same issue. Now let's just hope the grayscreening doesn't come back... all that lag's what started the whole mess in the first place.



I realize that quite a few threads have been posted on this matter (or something similar, anyway) over the past few months, but unfortunately the solutions posted have had little to no effect for me. I thought that maybe, if I provided a few details of my specific situation, someone might be able to point me in the right direction. Thanks in advance.

I'm running Ubuntu Lucid 32-bit (dual-booting with Windows 7 on an Insipiron laptop, on the off chance someone thinks that might be relevant). At first Firefox ran beautifully after the upgrade from Karmic to Lucid, but after a few days it started hanging up and grayscreening constantly, regardless of which pages I'd been viewing. It seemed to be related more to the length of time I had it open than any specific plugins, though I did try to update/fix those just in case. It got to the point where it would hang up every few seconds and I'd have to restart the browser, sometimes even the computer, to make it stop. (My Google Docs Prism was doing the same thing, though I'm not sure whether the two problems were directly related.)

Yesterday I decided to try installing the Mozilla build of 3.6.6 with Ubuntuzilla. I wasn't sure it'd work, but hey, might as well try; if nothing else I would rather have the slightly more up-to-date Mozilla build anyway. Installed it, ran Firefox, it worked, I closed it. Shortly afterward I ran Update Manager, primarily to get my other Mozilla builds up to date through the Ubuntuzilla repositories. I tried opening Firefox again afterward. I saw the icon light up and start bouncing on my AWN dock, but the program never opened--not even any sign of it or any related processes in the system monitor. No errors or messages of any sort in the terminal, either. I tried several times, but it simply refused to start.

So here I am. I've searched for hours, I've tried multiple solutions, and nothing has given me a permanent fix as of yet. I've tried uninstalling one or both of the Firefox versions (Ubuntu build and Mozilla build) and then reinstalling one/the other/both; nothing. I saw [this thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1469038") about libmoon being the issue, but libmoon is not installed on my system and so uninstalling it isn't possible. I found several solutions that looked like they were for problems unlike mine, but since the end result was still that Firefox wouldn't start I tried anyway--still, uninstalling/reinstalling xulrunner and nspluginwrapper, deleting secmod.db from my profile... none of it worked (though I guess I didn't expect it to).

[This thread's problem]("http://swiss.ubuntuforums.org/showthread.php?p=8832779") looks much more like what seems to be going on with me--I could get Firefox to start by deleting my profile (or the entire firefox folder, as recommended by someone else), but it will only run once and I have to delete the profile all over again to run it a second or further time. Deleting compatibility.ini from the profile appears to be all that's necessary rather than deleting an entire folder, but I still need to re-delete it each time I want it to run. (Another user's suggestion, starting safe mode, closing it and then starting normal firefox, also works-but-only-once.) The workaround that user posted, modifying firefox.sh, doesn't change anything for me and Firefox *still* refuses to start normally.

The only thing I can think to try and haven't yet is reverting to an earlier version of Firefox, say 3.5.x, and seeing if that helps. I'll report back if it does, though at this point my hopes aren't high. If that doesn't work then I'm not really sure what else to do other than use the "start safe mode first" trick every single time, and while that's certainly doable it's very annoying.

I don't know if trying the Mozilla build is what broke it, since it was working (albeit with grayscreening) before then and other people seem to have run into the problem with other builds anyway. I also doubt that the grayscreening is related, though I suppose it could be and thought I'd mention it just in case. Does anyone have any idea what the problem could be? I know that was a lot to read through, but I'd really appreciate the help and can provide more info if you need it. Again, thanks.

---

