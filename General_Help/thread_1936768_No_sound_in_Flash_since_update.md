---
title: "No sound in Flash since update"
date: 2012-03-06
forum: General Help
---

### Post by cyrus_the_virus on 2012-03-06
About two weeks ago there was an update for adobe flash in the update manager. Since this update is installed, flash content do not play sound anymore. When I look in the sound settings menu, there is no entry in the application tab for flash which use to be the case. This problem occurs on my two computers, both running Ubuntu 11.10 64bit, with flash installed from the software center. 

I have noticed there are other people having (other) problems with flash since that same update (though no reports of problems with sound). See the comments in the software center or [this]("http://ubuntuforums.org/showthread.php?p=11695919#post11695919") topic on the ubuntu forum.

I have tried the following to fix the problem:
[LIST]
[*]I tried various browsers: Chrome, Firefox and Opera
[*]Uninstall and reinstall flash in the software center
[*]Manually install flash by downloading the latest libflashplayer.so and move it to /usr/lib/mozilla/plugins
[*]Manually install an older version of the flash player (11.1.102.55)
[*]Install flash with Flash-Aid (see [https://addons.mozilla.org/nl/firefox/addon/flash-aid/]("https://addons.mozilla.org/nl/firefox/addon/flash-aid/"))
[/LIST]

When I manually install version 10.3, it works (with sound) in Opera but not in other browsers. I think this is because Opera uses its own version of nspluginwrapper. Other browser cannot detect flash 10.3 when it is manually installed. So I use this as a workaround. However I would like it to work with other browsers too as Opera is not my primary browser.

Any ideas how to solve this?

---

### Post by DrNJF on 2012-03-06
Hi,
I'm having the exact same issue... and have tried all the same solutions that you have - with no success. When I search the system files for 'Flash', i get several versions of the adobe flash plugin installer, plus other flash plugins, all of which are not in the mozilla/plugins folder.

Perhaps these different versions are causing the issue? i would delete them but the files are locked, and being a total novice i have no idea how to delete these files...and if the deletion could actually be detrimental to the system.

I hope someone can help...

Thanks

---

### Post by cyrus_the_virus on 2012-03-06
> **DrNJF said:**
> Hi,
I'm having the exact same issue... and have tried all the same solutions that you have - with no success. When I search the system files for 'Flash', i get several versions of the adobe flash plugin installer, plus other flash plugins, all of which are not in the mozilla/plugins folder.

Perhaps these different versions are causing the issue? i would delete them but the files are locked, and being a total novice i have no idea how to delete these files...and if the deletion could actually be detrimental to the system.

I hope someone can help...

Thanks

Good to know I'm not the only one having this problem. I think all browsers use the flash installed in the folder */usr/lib/mozilla/plugins*. I only have one flash plugin in that folder.

---

