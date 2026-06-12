---
title: "Youtube is not displayed correctly by Firefox"
date: 2010-04-08
forum: General Help
---

### Post by Randypan on 2010-04-08
This is probably the case with other sites I log on to as well, but Youtube is where the issue is most noticeable. The youtube homepage is displayed with some buttons having white/grayish text over a white background.
[ATTACH]152702[/ATTACH]
[ATTACH]152703[/ATTACH]
As you can see in the images the titles of the 'search', 'comment', 'subscribe', 'options' and other buttons are barely visible.
Moreover whenever I log on to youtube, Firefox's error console fills up with warning messages.
[ATTACH]152706[/ATTACH]

_What I've tried out to fix this:_
-I fiddled with the Fonts and Colours options in the Preferences menu. I tried disabling and enabling 'use system colours' or the option of letting webpages use their own colours and fonts and nothing happened.
-I then found somewhere in the forums that I could fix it by editing about:config, more specificaly the gfx.color_management.mode option. When I opened about:config this line was nowhere to be found. 

I use Jaunty with the latest updates and the only extra firefox extension I've got is Greasemonkey which currently has one userscript installed. I uninstalled and reinstalled both the userscript and Greasemonkey itself, but these actions had no effect on the Youtube issue.
 
The problem first showed up when Youtube went under its latest interface modification untill the date of this post.

---

### Post by Vaphell on 2010-04-08
maybe some broken css is cached? force reload (ctrl+f5 or ctrl+shift+r)?

---

### Post by Randypan on 2010-04-08
> **Vaphell said:**
> maybe some broken css is cached? force reload (ctrl+f5 or ctrl+shift+r)?

Force-reload didn't fix it.

---

### Post by lovinglinux on 2010-04-08
Start firefox in safe mode:

```
firefox -safe-mode
```

If it works, then is probably an extension causing the problem.

You could also try to start firefox with a clean profile and see if the problem persists. This way you would be able to determine if it is a Firefox profile issue or not.

See [COLOR="Sienna"]**Troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Randypan on 2010-04-09
> **lovinglinux said:**
> Start firefox in safe mode:

```
firefox -safe-mode
```If it works, then is probably an extension causing the problem.

You could also try to start firefox with a clean profile and see if the problem persists. This way you would be able to determine if it is a Firefox profile issue or not.

See [COLOR=Sienna]**Troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").
   
I run Firefox in safe mode and it didn't work.
I also created a clean Profile and it didn't work either. A strange thing is that when I log in as root and use Firefox, the page is displayed correctly. I copied the contents of the root's Firefox Profile directory over my own but the problem persisted. This led me to assume that some process that's running in my personal account and not in root conflicts with firefox. The prime suspect seems to be this script:
[http://blog.nachtarbeiter.net/2009/08/19/choppy-flash-video-in-full-screen-mode-on-ubuntu/](http://blog.nachtarbeiter.net/2009/08/19/choppy-flash-video-in-full-screen-mode-on-ubuntu/)

Note that the script actually fixes flash video -it works. Could it be that it also messes up the way webpages are displayed in the process?

I worked around this assumption and nothing came up.
I removed the link of the bash script from init.d to prevent it from running at the next startup and rebooted. ...Same old results...

---

### Post by lovinglinux on 2010-04-09
Is not a good idea to login as root. The root password is disable on Ubuntu for a reason.

Perhaps you have a permission issue.

Run this command:

```
sudo chown -R $USER:$USER ~/.mozilla
```

Don't change anything. Run it as it is.

---

### Post by Randypan on 2010-04-09
I ran the command as it was given and nothing changed. I don't thing it has to do with permissions. All I did while logged in as root was run Firefox. And I didn't touch any of the files in the root directory.I just copied the contents of the root Firefox Profile directory over to my own user's and changed the copied files' permissions to my user. The original files were not altered in any way. Also all major changes and tweaking I've done in Firefox were performed while I was logged in as a regular user, occasionally using the sudo command of course. Messing with root didn't make things take a turn for the worse, it just had no effect on anything.

---

### Post by Randypan on 2010-04-12
...I made a fool of my self again. It was the selected gtk theme's fault. I found that using a dark theme may cause problems with fonts, because most of them are rendered in white. I switched to a theme that uses mostly black fonts and everything turned out fine. As a side note I have to say that GNOME ColorChooser is a really nice tweaking tool. Please don't misjudge me, I'm still learning. Thanks

---

### Post by moshebagelfresser on 2011-03-08
Adobe has a newer beta version that does work 10-3_b1_lin_03811.tar.gz

get it here:
[http://labs.adobe.com/downloads/flashplayer10-3.html]("http://labs.adobe.com/downloads/flashplayer10-3.html")

use gksudo nautilus and copy and merge files if necessary to the respective folders. 

Moshe

---

