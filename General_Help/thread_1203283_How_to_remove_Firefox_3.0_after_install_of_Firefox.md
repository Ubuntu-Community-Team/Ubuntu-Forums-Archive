---
title: "How to remove Firefox 3.0 after install of Firefox 3.5?"
date: 2009-07-03
forum: General Help
---

### Post by abcuser on 2009-07-03
Hi,
on Ubuntu 9.04 I have installed Firefox 3.5. I would like to uninstlal Firefox 3.0 to preserve disk space. I did the following in Terminal:
sudo apt-get --purge remove firefox
sudo apt-get autoremove
sudo rm -rf ~/.mozilla

But writting firefox to terminal Firefox 3.0 still appears. It looks like it wasn't removed from my system. How to uninstall Firefox 3.0 from my computer?
Regards

---

### Post by Legace on 2009-07-03
Leave it installed. You can't be that low on disk space. The official Firefox might get updated to 3.5 and you'll need it then.

---

### Post by ajgreeny on 2009-07-03
If you have already done it, you will already have lost all your configuration, cookies, bookmarks and history, etc etc, as you deleted the ~./mozilla folder.  That could be a problem, unless you copied all of them over to the 3.5 config, wherever that is kept.  However, often, it is not only suggested, but required, that the old firefox remains until the final version of the new comes out.  Perhaps I'm behind the times and the final of 3.5 is already here for ubuntu, but if so, I'm not aware of the fact.

---

### Post by abcuser on 2009-07-03
Hi,
from Firefox 3.5 Help | About there is info: "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.1pre) Gecko/20090701 Ubuntu/9.04 (jaunty) Shiretoko/3.5" Does this mean it is not official version yet? Where is this official/unofficial info hidden?
Regards

---

### Post by ajgreeny on 2009-07-03
OK, having just looked in synaptic, I see FF3.5 is now available.  I was not aware of that and assume that as update notifyer does not flag it that FF3.0.11 is not going to be overtaken automatically by FF3.5.

Will the two versions live side by side with FF3.5 using other config files or will it automatically use the config in ~/.mozilla that is used by FF3.0.11?  I will have a search of any stickies about this in the meantime, but would like to hear from anyone who has got 3.5 and has had no problems with it.

---

### Post by utkjamie on 2009-07-03
> **abcuser said:**
> Hi,
from Firefox 3.5 Help | About there is info: "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.1pre) Gecko/20090701 Ubuntu/9.04 (jaunty) Shiretoko/3.5" Does this mean it is not official version yet? Where is this official/unofficial info hidden?
Regards

Same question. Firefox 3.5 shows up as "Shiretoko" and I sometimes get warnings on websites telling me that my browser is not supported and that I should use Internet Explorer or Firefox. Strange.

I installed 3.5 from the Karmic repos, by the way.

---

### Post by Soul-Sing on 2009-07-03
I really prefere a site by site install: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
It does not effect the ubuntu desktop, if there are issue's with the new release/version you can use the "old" one.
Jaunty comes with firefox 3.5 beta.

---

### Post by ajgreeny on 2009-07-03
> **leoquant said:**
> I really prefere a site by site install: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
It does not effect the ubuntu desktop, if there are issue's with the new release/version you can use the "old" one.
Jaunty comes with firefox 3.5 beta.
Actually, to be more correct FF3.5 is available for jaunty, but I don't think it comes with it automatically.

Also to answer my own question in post #5, I have tried it on a test install of ubuntu I keep on a separate partition, and have found that the executable is called /usr/bin/firefox-3.5 so it will run separately from FF3.0.11.  It also adds a sub-folder to the ~/.mozilla folder called firefox-3.5 which appears to be an almost exact copy of the original firefox sub-folder.  My look at FF3.5 so far suggests that it is stable and works well, but I will keep of it for now for my working OS, just in case it should go wrong and mess upthe whole ~/.mozila folder.

---

### Post by Soul-Sing on 2009-07-03
Indeed jaunty proposed comes with the "real" 3.5. Correct?
Or maybe the 3.6 alfa? (Just curious..)

---

### Post by ajgreeny on 2009-07-03
Yes, jaunty proposed has 3.5 final, but the standard security and recommended have the beta4.  I don't know how different they are, but at the moment some extensions for 3.0.11 will not work on 3.5, so I shall stick with 3.0.11 for the moment.

---

### Post by GSam on 2009-07-03
I have wondered if I were to export all of my bookmarks from FF and then remove everything related to Firefox and reinstall 3.5 and import my bookmarks back. Would this be a bad idea? I don't have any problems with 3,0, but like the idea of having the "latest and greatest". I'm running 8.04 and 3.5 doesn't show up in Synaptic.

---

### Post by poldie on 2009-07-03
> **GSam said:**
> I have wondered if I were to export all of my bookmarks from FF and then remove everything related to Firefox and reinstall 3.5 and import my bookmarks back. Would this be a bad idea? I don't have any problems with 3,0, but like the idea of having the "latest and greatest". I'm running 8.04 and 3.5 doesn't show up in Synaptic.

If you're bothered about your bookmarks you could get the addon 'foxmarks'. It lets you store your bookmarks on a central server somewhere, and then wherever you install foxmarks you have access to them. Great if you have a windows/ubuntu dual boot system, or want to access your bookmarks from your work/mates PC.  You can create folders like work/home etc so your co-workers aren't upset by your gut-wrenching pornography links...

---

### Post by lovinglinux on 2009-07-04
First of all, most of these questions are answered in the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

> **abcuser said:**
> Hi,
on Ubuntu 9.04 I have installed Firefox 3.5. I would like to uninstlal Firefox 3.0 to preserve disk space. I did the following in Terminal:
sudo apt-get --purge remove firefox
sudo apt-get autoremove
sudo rm -rf ~/.mozilla

But writting firefox to terminal Firefox 3.0 still appears. It looks like it wasn't removed from my system. How to uninstall Firefox 3.0 from my computer?
Regards

You should not remove Firefox 3.0.11

About the deletion of ~/.mozilla:

> **[color=#CC0000]Note:[/color]** I don't know why everyone recommends moving, renaming or deleting ~/.mozilla folder to solve Firefox issues. The ~/.mozilla folder is also the place where other Mozilla applications stores their profiles (Thunderbird, Sunbird, etc), so deleting this folder will delete their settings too. 

Firefox profiles are stored under ~/.mozilla/firefox folder. So if you need to remove a Firefox profile to fix a problem, then delete, rename or move ~/.mozilla/firefox not ~/.mozilla. Nevertheless, removing an entire profile is usually unnecessary and must be avoided, since just a few profile files are the usual culprits, otherwise you will remove all Firefox settings, extensions, themes, bookmarks and so on.


> **ajgreeny said:**
> If you have already done it, you will already have lost all your configuration, cookies, bookmarks and history, etc etc, as you deleted the ~./mozilla folder.  That could be a problem, unless you copied all of them over to the 3.5 config, wherever that is kept.  However, often, it is not only suggested, but required, that the old firefox remains until the final version of the new comes out.  Perhaps I'm behind the times and the final of 3.5 is already here for ubuntu, but if so, I'm not aware of the fact.

When you install Firefox 3.5 it copies the profiles from ~/.mozilla/firefox/ to ~/.mozilla/firefox-3.5/. But since the OP deleted the ~/.mozilla/ folder, then all profiles are gone. 

> **ajgreeny said:**
> OK, having just looked in synaptic, I see FF3.5 is now available.  I was not aware of that and assume that as update notifyer does not flag it that FF3.0.11 is not going to be overtaken automatically by FF3.5.

Will the two versions live side by side with FF3.5 using other config files or will it automatically use the config in ~/.mozilla that is used by FF3.0.11?  I will have a search of any stickies about this in the meantime, but would like to hear from anyone who has got 3.5 and has had no problems with it.

Currently, Firefox 3.5 is installed side-by-side and it imports the profiles as explained above. Nevertheless, it seems that Firefox 3.0.11 will indeed be updated to 3.5 soon.

> **ajgreeny said:**
> Yes, jaunty proposed has 3.5 final, but the standard security and recommended have the beta4.  I don't know how different they are, but at the moment some extensions for 3.0.11 will not work on 3.5, so I shall stick with 3.0.11 for the moment.

You can disable the extension checking. Refer to the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for instructions.


> **GSam said:**
> I have wondered if I were to export all of my bookmarks from FF and then remove everything related to Firefox and reinstall 3.5 and import my bookmarks back. Would this be a bad idea? I don't have any problems with 3,0, but like the idea of having the "latest and greatest". I'm running 8.04 and 3.5 doesn't show up in Synaptic.

You can export all your settings, including bookmarks, using FEBE extension (see Backup section of [my tutorial](http://ubuntuforums.org/showthread.php?t=1193567)) then import back to any Firefox installation. This is not only possible, but highly recommended, because Firefox profiles can easily become corrupted. However, removing Firefox is not a good idea. Besides, as explained above, Firefox 3.5 will automatically copy your Firefox 3.0.11 profiles from ~/.mozilla/firefox/ to ~/mozilla/firefox-3.5/. You can use Firefox 3.5 sise-by-side with 3.0.11, because once you profiles are copied to the 3.5 folder, any changes to it won't affect the 3.0.11 profiles.

---

