---
title: "iTunes 10.1 on 10.10"
date: 2010-12-13
forum: General Help
---

### Post by Stevegfx on 2010-12-13
Hi,

First of all, I'm EXTREMELY new to Ubuntu so bare with me :P

Ok. I downloaded and installed Wine 1.2 on my system in order to run Windows programs (such as office, iTunes and Photoshop). I successfully installed and run Photoshop, so I thought I'd try my luck on itunes.

I downloaded and installed iTunes 10.1 without fail. During the installation process, the screen flashed black but eventually came back (by opening a full-screen application). I opened iTunes and tried to add songs, and it crashed. Following the advice of another website, I restarted in order to fix it.

When I logged in I noticed that everything was flashing. I couldn't click anything, restart etc. I had to manually power off my computer. I restarted and this time I logged in to Safe Mode, everything worked fine.

I tried to uninstall iTunes while in safe mode without any success. It would say it was uninstalled, but it would still be there! So I tried to just delete the files from the c: folder. This too led to the progam coming back all by itself.

So, the issue is: I can't run Ubuntu in 'Normal' mode, only in safe mode, without it flashing an unable to do anything.

PS: By flashing i mean everything (except the background) flash, including the task bar, anything on the desktop etc.

Could anyone help me?

---

### Post by MARP1961 on 2010-12-14
I too experimented with iTunes using Wine! Although it appears to install, it really doesn't work correctly. I have not heard of any Linux user who has managed to use the iTunes store correctly either. I also had trouble deinstalling it and ended up removing Wine completely. Try removing Wine and then reinstalling if you need it to run Photoshop. If you do not need iTunes Store then why not try out Rythmbox or Banshee? If Ubuntu ever gets 'broken' and cannot be easily sorted just back up all your important data files onto CD or USB and do a fresh install. Just be careful not to erase any Windows partition you may be keeping if you are dual booting.

---

### Post by trinitydan on 2010-12-14
I just wanted to suggest that you might try using Rhythymbox for syncing music to your iPod.  It comes with Ubuntu.  While it lacks some of the advanced iPod syncing features of iTunes, it does have at least one great feature absent from iTunes, the ability to sync tracks from the iPod to the computer.  ;)  There are other iPod tools too that are native to linux, such as GPixPod that you can use to sync your photos.  It is a common mistake for new users to get discouraged trying to make their familiar software programs work, when you could possibly do better to work through the learning curve to use new software.

---

### Post by potat on 2010-12-14
If you want to get rid of Wine (it might solve your problem):
```

sudo apt-get remove --purge wine
rm -r ~/.wine

```

First command removes Wine and its configuration files. Second gets rid of the C: drive

Then just
```
 sudo apt-get install wine 
```
again.

I would suggest not reinstalling iTunes. Do you need it because of music you have purchased or because you have an iPod? Either of those problems should be solvable.

---

### Post by Verbeck on 2010-12-14
edited out

---

### Post by Stevegfx on 2010-12-16
Thanks for the replies!

My need for iTunes was simply for an easier move over to Ubuntu. I do not 'need' it and will not be installing it again.

In the stress of the situation, I saved all my installed .deb files from the cache and did a fresh install then reinstalled everything.

For future instance these comments will come in handy.

I don't understand why Wine wouldn't remove anything. Is this a known bug or just how it operates?

Once again, thank you all for the replies!

---

### Post by Spyderkid on 2010-12-16
I'm afraid iTunes doesn't work on ubuntu but...

you can install 'gtkpod iPod manager' from the Software centre which can manage music and apps on your iPod

---

