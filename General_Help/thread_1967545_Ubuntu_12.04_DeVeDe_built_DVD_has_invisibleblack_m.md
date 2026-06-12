---
title: "Ubuntu 12.04: DeVeDe built DVD has invisible/black menu"
date: 2012-04-28
forum: General Help
---

### Post by veroslav on 2012-04-28
Hi,

I am running Ubuntu 12.04 and have built a DVD with a custom menu in DeVeDe (v3.21.0).
Unfortunately, the menu is completely dark. I know it is there because I  can hear the background music and also I can use the menu entries,  because I know where they should appear. The playback of the video is  flawless however.

Burning the iso image and watching it on my dvd player also results in a black menu.

I was using ffmpeg for encoding (standard option in DeVeDe nowdays I believe).

Changing to mencoder instead, produces a DVD where the menu IS displayed  correctly, however, there is a slight stutter throughout the playback  of the DVD that is big enough to render the watching an unpleasant  experience.

Has anybody else experienced the same issue?

Thank you in advance.

Regards.

---

### Post by veroslav on 2012-04-28
I am starting to realize that my topic might be more appropriate for the "Multimedia & Video" subforum. Could anyone of the mods move my thread there?

Thank you in advance.

---

### Post by veroslav on 2012-04-29
bump

---

### Post by habana on 2012-04-29
Have you set a theme in System settings/Appearance? Mine was blank when I installed 12.04 and I had this problem with the terminal.

---

### Post by veroslav on 2012-04-30
Hi habana, thank you for your reply.

I have set a new theme (not from Settings-Appearance but from Ubuntu Tweak, but still) yes.
Do you think this might be a cause? The weird think is that the menu works perfectly when I use mencoder as the backend, weird!

I seem to be experiencing the same problem as described here:

[http://groups.google.com/group/devede-forum/browse_thread/thread/8a87b2841c520038](http://groups.google.com/group/devede-forum/browse_thread/thread/8a87b2841c520038)

Any more info on this?

Thanks again!

---

### Post by habana on 2012-04-30
Hi veroslav

If the only appplication giving you this problem is DeVeDe then it is probably as noted on the DeVeDe forum. If it is happening with other programs (for example, try opening a terminal) then I suspect Ubuntu Tweak but I am no expert. I intend to try Ubuntu Tweak so I shall tread carefully!

Good luck!

---

### Post by Daniel_Duparc on 2012-05-04
I had the same issue with ubuntu 12.04. 
Changing Edit -> Preferences from ffmpeg to mencoder
in devede fixed it for me 
ffmpeg in ubuntu 12.04 is very old
and when launching ffmpeg in a terminal, it says that one 
has to change to avconv since ffmpeg is no longer supported. 
It is not true as one can see on the ffmpeg site.

---

### Post by OzzyFrank on 2012-05-05
As odd as it sounds, this DeVeDe-Mencoder "fix" also worked for me after upgrading to 12.04. What I mean by that is since I don't usually use DeVeDe for encoding, just the DVD authoring, I wouldn't have thought switching back to Mencoder would have made a difference (since the authoring is handled by DVDAuthor). And nothing appears wrong with FFMPEG, as I actually use that to encode to DVD-compatible files, via tovidGUI.

PS: I started a bug report thread at the DeVeDe forums:

[http://groups.google.com/group/devede-forum/browse_thread/thread/691869c956963703](http://groups.google.com/group/devede-forum/browse_thread/thread/691869c956963703)

---

### Post by veroslav on 2012-05-07
Thank you for the info and the bug report you posted, OzzyFrank.

I have a question about the mencoder option in DeVeDe:

Are you experiencing any issues whith stuttering video after encoding a DVD with mencoder? I can confirm that switching to mencoder produces a DVD with working menu, but unfortunately, when I play the DVD, the playback stutters significantly (only video not audio). This is not the case when using ffmpeg.

I have tried mencoder on both my laptop and my desktop and I get the same mencoder results on both :(

---

### Post by veroslav on 2012-05-07
I posted a new thread about the mencoder issues I described above, I thought it was a better idea.

The thread can be found here:

[http://ubuntuforums.org/showthread.php?p=11913328#post11913328](http://ubuntuforums.org/showthread.php?p=11913328#post11913328)

---

### Post by OzzyFrank on 2012-05-07
> **veroslav said:**
> Thank you for the info and the bug report you posted, OzzyFrank.

I have a question about the mencoder option in DeVeDe:

Are you experiencing any issues whith stuttering video after encoding a DVD with mencoder? I can confirm that switching to mencoder produces a DVD with working menu, but unfortunately, when I play the DVD, the playback stutters significantly (only video not audio). This is not the case when using ffmpeg.

I have tried mencoder on both my laptop and my desktop and I get the same mencoder results on both :(

OK, I haven't actually done any encoding in DeVeDe since upgrading, just the authoring - but no issues (which there wouldn't be, since I haven't done any encoding - then again, who would have thought changing the encoder would solve an authoring issue). I only use DeVeDe for encoding problem clips FFMPEG can't seem to handle via tovidGUI (so for those instances I use Mencoder in DeVeDe).

OK, unless I am truly mistaken, I am pretty sure I saw a Mencoder update in the last set of updates - and I'm thinking it was after I added the Medibuntu repositories again, so check that out - it could be the answer.

Also, I'd go to the DeVeDe forum and post your woes there - there doesn't seem to be an actual bug report section, so just start a new thread. I don't think you need to be a Launchpad member (though it pays to become one so you can file bug reports for Ubuntu, Nautilus, and other Linux stuff) - I believe you just have to log into Google Groups. It seriously is worth doing so, as filing bug reports at the Ubuntu Forums will only get you so far.

And as for DeVeDe, the more people posting similar problems, the more likely it will be resolved. And as I said, it pays to do so - once I just posted I'd really (I mean REALLY) like the menu margins not to be so far in, as it really messes things up (once you got to adding about 6 titles, there seemed to be no difference between Top, Bottom or Centre!). It didn't seem like anyone else was bothered by this, and I never got a response, yet in the last version, we now have full control over margins.

---

### Post by veroslav on 2012-05-07
Thank you for your detailed response.

I have made an entry on the DeVeDe forum and described my problem there. I have previously added the Medibuntu repository, right after I discovered the black menu problem, in hope that it might fix the issue.

However, except for the original installation of some Medibuntu libraries, I haven't noticed any updates recently from this repository. Will keep a close look on it.

Thanks again, hopefully this issue will soon be resolved, as I am really enjoying Ubuntu 12.04 so far.

Regards,
Veroslav

---

### Post by OzzyFrank on 2012-05-07
At least we're both active in the DeVeDe forum so this will get fixed. I mean, what did I tell ya? A day later and he's already got a beta out in GIT where you can choose one encoder for the actual encoding, and another for the menu creation. Gotta love the open source world!

I'll have to encode something with Mencoder to see if I get the flawed playback you describe. Cheers.

(PS: I edited out the first line of this comment since I hadn't had my first coffee and my brain muddled up Mencoder and FFMPEG into a pile of gibberish, hehe. We both have the same problem - I just haven't experienced any encoding issues with Mencoder as I encode with tovidGUI).

---

### Post by colinpat on 2012-05-09
Hi, I am having same problem with DeVeDe - menu is just black screen.  First 2 DVD's I made 2 weeks ago worked perfectly but any I do now (using exactly same settings) result in black menu screen.
Using Ubuntu 12.04 and DeVeDe 3.21.0

---

### Post by juhevil on 2012-05-09
I experienced the same problem on 12.04, though DeVeDe worked nicely on 11.10. Now DeVeDe 'successfully' created a disk image including two video items. However, when started using VLC, the menu was invisible on PC, but the first tittle could be started by hitting the 'enter key' on keyboard. The second tittle was also playable from the keyboard.

Later after burning the image to a DVD the menu was visible using standard DVD-player, but the subtittles that I had added to translate the foreign language audio were still missing.

regards, 
juhevi

---

### Post by OzzyFrank on 2012-05-09
I must be the only one who couldn't even get playback (though I never tried the Enter key on my PC, as I was trying to get it to work in the lounge). But the workaround is easy enough, and for those who also encode with DeVeDe (I only do the actual DVD authoring with it) and find switching to Mencoder gives you a working menu, but stuttering playback, there is a new version in git that you can manually install that now lets you pick one encoder for the video, and another for the menu (meaning people with that issue can have FFMPEG for the encoding and Mencoder for the menu creation).

Instructions here: [http://groups.google.com/group/devede-forum/browse_thread/thread/149e212d096c8a75?hl=en](http://groups.google.com/group/devede-forum/browse_thread/thread/149e212d096c8a75?hl=en)

Also, I have to stress here that **posting bug reports gets things done** - both Veroslav and I took the time to do so at the DeVeDe forum, and a day later the developer Sergio had a new beta version with the fix, or at least a great workaround. So remember that when it looks like complaining about a faulty program at the Ubuntu Forums doesn't look like it's getting you anywhere, it probably never will, but actually going to the program's site and either filing a bug report (if they have that option) or starting a discussion thread (like with DeVeDe) could see things fixed in a day or two! I love the Open Source world... Cheers.

---

### Post by OzzyFrank on 2012-05-09
> **veroslav said:**
> hopefully this issue will soon be resolved

Hi buddy. Did you install the new beta? I'm guessing that fixed your dilemma. I hope the Mencoder issue with jittery playback is fixed soon though, as when I can't encode certain vids with FFMPEG in tovidGUI, I use Mencoder in DeVeDe.

---

### Post by veroslav on 2012-05-10
Hi OzzyFrank!

The original problem (invisible menu) was solved by upgrading the ffmpeg from the PPA found here:

[http://ubuntuforums.org/showthread.php?t=1971910](http://ubuntuforums.org/showthread.php?t=1971910)

I never had the chance to test the latest DeVeDe beta, but I will when there is a deb available from the official site. Don't want do mess with anything now that everything works :)

Thank you all for your support! I consider my issues as solved.

Kind Regards,
Veroslav

---

### Post by juhevil on 2012-05-10
> **juhevil said:**
> I experienced the same problem on 12.04, though DeVeDe worked nicely on 11.10. Now DeVeDe 'successfully' created a disk image including two video items. However, when started using VLC, the menu was invisible on PC, but the first tittle could be started by hitting the 'enter key' on keyboard. The second tittle was also playable from the keyboard.

Later after burning the image to a DVD the menu was visible using standard DVD-player, but the subtittles that I had added to translate the foreign language audio were still missing.

regards, 
juhevi

My problem was solved by following colin-m 's advice in the parallel thread: 'DeVeDe menu problem' . As adviced, unselecting the 'Use FFMEG instead of Mencoder' in the DeVeDe programs preferences menu, brought back visible DVD menu items and my edited subtitles.

Thanks, colin-m
juhevil

---

### Post by tomdkat on 2012-06-12
> **veroslav said:**
> Hi OzzyFrank!

The original problem (invisible menu) was solved by upgrading the ffmpeg from the PPA found here:

[http://ubuntuforums.org/showthread.php?t=1971910](http://ubuntuforums.org/showthread.php?t=1971910)

I never had the chance to test the latest DeVeDe beta, but I will when there is a deb available from the official site. Don't want do mess with anything now that everything works :)

Thank you all for your support! I consider my issues as solved.

Kind Regards,
VeroslavI just installed this updated version of ffmpeg and mplayer and mencoder stopped working, which led to another DeVeDe issue.  How did you avoid the mplayer/mencoder issue when you upgraded to the newer version of ffmpeg?

Thanks!

EDIT:  I think I answered my own question.  Since your post about your success with the above mentioned FFMPEG PPA, *another* FFMPEG version, 0.11, was released.  This new released changed some shared library names, which cause mplayer and mencoder to break.

Peace...

---

### Post by zak.k on 2012-08-08
I've had exactly the same problem with broken menus, which appear to be due to libav's ffmpeg not handling the deprecated -loop_input option correctly.

This appears to be worked around in the latest devede (3.22, which is in quantal) by passing "-loop 1" to ffmpeg instead.

For me, installing devede 3.22 from quantal seems to fix the menu problem.

See [https://bugs.launchpad.net/ubuntu/+source/devede/+bug/1034457](https://bugs.launchpad.net/ubuntu/+source/devede/+bug/1034457)

---

