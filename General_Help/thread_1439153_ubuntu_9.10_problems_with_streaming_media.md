---
title: "ubuntu 9.10 problems with streaming media"
date: 2010-03-25
forum: General Help
---

### Post by grimmaster on 2010-03-25
First off I must mention that I am a Newb to linux and ubuntu.

second my computer is single os with ubuntu 9.10

the problem i have is trying to watch any thing streaming media. Movies, music, like from youtube, divx, or even megavideo which seems to work best right now.

what happens is that the video or firefox it self seems to freeze up every 10 minutes or so.

It may be that i need to increase the buffer memory size but i do not know how to. 

I have updated my computer and firefox and installed and updated any possible add-ons that would fix the problem.

so far I can not say i have helped or hurt my cause with my attempts.

What im asking for is either a patch or add-on that will help this problem or how to run windows inside of ubuntu. (Im am tired of windows and ubunu has made my computer work so much faster, when i am sure that i know how to make this computer stable with what i need for internet use i will apply it to my other computer.)

---

### Post by byStanderone on 2010-03-25
...found this guide and it helped me a lot, you can install the needed codec support:
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

---

### Post by imblack on 2010-03-25
For installing windows inside ubuntu, there's an excellent program called virtual box, please search and you will find plenty of tutorials how to install and use it. Its pretty straight forward.

Good luck!

---

### Post by grimmaster on 2010-03-27
OK i think i may have fixed it.

first i got rid of all third party packages. 
[https://help.ubuntu.com/community/CleanUpgrade](https://help.ubuntu.com/community/CleanUpgrade)

then because i downloaded firefox stuff it deleted the root firefox so i had to reinstall it.

1 goto synaptic package manager 
2 search firefox
3 check install on the firefox and installed it.

then to fix the download problem (testing now)

i changed the setting on the flash player 10
 [http://www.macromedia.com/support/do...manager02.html]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html")

found that link in [http://ubuntuforums.org/showthread.php?t=978212&page=2](http://ubuntuforums.org/showthread.php?t=978212&page=2)

like i said im testing right now to see if that fixes the problem..but if it works ill post back again. if not..then maybe there is another way before i use the last resort and use of hard drive space with a virtual os

edit...

forgot to mention that i disabled the xine add-on to firefox and installed/enabled the vlc and vlc for totem add-ons.
now all videos appear to be working: megavideo, youtube, xtshare, and others.

---

