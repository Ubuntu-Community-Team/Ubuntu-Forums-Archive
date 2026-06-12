---
title: "Web Kiosk"
date: 2011-12-05
forum: General Help
---

### Post by coolguy918 on 2011-12-05
Hi,

I'm attempting to set up a web kiosk for a public user scenario (on Lucid if that makes a difference). My ultimate goal is to allow users access to the Internet using Firefox 8 while allowing them no customization whatsoever. My original thought was to make the kiosk user's whole home directory and its contents read-only, but I realized that method would be very rough-around-the-edges and probably cause problems, so I did some Googling and came up with a better way. So far I did the following:

[LIST]
[*]Remove all panel items except a Firefox launcher, a window list, and a button to show the desktop
[*]Lock down said panel with Pessulus
[*]Use lshell as the user's shell (simply an obsessive, added security measure; the users can't get to the terminal or execute custom commands anyway, but should anybody hack it they'll only have access to the most basic commands (like ```
ls
```))
[*]Disable keyboard shortcuts (except the most basic ones)
[*]Lock down Firefox using a variety of different settings and extensions (Public Fox, two different menu editors, a keyboard shortcut editor (with a rather creative way of disabling certain shortcuts), always-on private browsing, among others)
[*]Disable background change using command ```
gconftool-2 -t bool -s /apps/nautilus/preferences/show_desktop false
```
[/LIST]
During my testing, I've found two places for customization that need to be fixed:

[LIST]
[*]While Firefox toolbars themselves cannot be customized, their visibility can be toggled by right-clicking and checking/unchecking the toolbar name
[*]Right-clicking on the panel, there's an "about" option which opens the Ubuntu help dialog...which contains bookmarks and preferences
[/LIST]
I know these aren't *major* problems, but I'm OCD about this sorta stuff and need to lock those two settings (along with any others if anyone can think of something I missed). If I were to make only certain config files read-only, which ones would I lock to prevent those settings from being changed. I don't care if the users can change the settings as long as they don't "stick," for lack of a better word.

---

### Post by lykwydchykyn on 2011-12-05
I've made many a web kiosk on Linux, and just recently documented my method.  Here's a link:

[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

basically, instead of locking down a big desktop environment, I just build a simple one from scratch that doesn't do much.

I'll also add that firefox has become increasingly difficult to use in kiosk situations since version 2.  There used to be some really good plugins, but few of them work anymore.

Chromium has a decent (if limited) kiosk mode, and opera's is very powerful and flexible.  For my kiosks, I ended up coding my own browser in python with QtWebkit -- just another extension of the idea that it's sometimes easier to build a minimal environment from scratch than to lock down something fully-featured.  

Of course nowadays there are things like luakit and jumanji if you want a customizable, minimally-featured browser.

---

### Post by oldfred on 2011-12-05
I have not done it but some others have discussed kiosks.

Kiosk discusions:
[http://ubuntuforums.org/showthread.php?t=1872560](http://ubuntuforums.org/showthread.php?t=1872560)
[http://ubuntuforums.org/showthread.php?t=1881141](http://ubuntuforums.org/showthread.php?t=1881141)
[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/)
chromium kiosk using Tiny Core Linux. Talk about small and light!

---

### Post by coolguy918 on 2011-12-06
Thank you all for the suggestions...and I think I might implement the rsync idea to some extent. Problem is, these computers are all thin clients and we have to run them off an existing server that's loaded with Lucid, Firefox 8, and GNOME. Personally I think it would look unprofessional for the setting just to run a browser in a loop, so I'm wanting a really locked-down GNOME desktop with a custom wallpaper that contains our organization's logo and where Firefox uses our website as the homepage. I've used the Webconverger LiveCD in the past and didn't like it. Can you guys please just let me know which configs to lock down?

Also, to add to my question: Say I were to set up an rsync when the server reboots (we're gonna have it REALLY locked down anyway and they'll only have access to the Internet, they won't even be able to download anything or use their own removable media to transfer files, but this is just an extra security measure to refresh the profiles with a clean copy once in a while) or clone my setup on a new user account by copying files manually. I don't wanna copy the whole home folder, just the Firefox profile, custom wallpaper, GNOME panel layout, and pessulus settings. Which files/folders would I copy?

---

### Post by lykwydchykyn on 2011-12-06
> **coolguy918 said:**
> Thank you all for the suggestions...and I think I might implement the rsync idea to some extent. Problem is, these computers are all thin clients and we have to run them off an existing server that's loaded with Lucid, Firefox 8, and GNOME. Personally I think it would look unprofessional for the setting just to run a browser in a loop, so I'm wanting a really locked-down GNOME desktop with a custom wallpaper that contains our organization's logo and where Firefox uses our website as the homepage. I've used the Webconverger LiveCD in the past and didn't like it. Can you guys please just let me know which configs to lock down?

I'm afraid I cannot, since I don't use that method and haven't worked with Pesselus.  Other than looking pretty, what's the purpose of the GNOME desktop?

> 
Also, to add to my question: Say I were to set up an rsync when the server reboots (we're gonna have it REALLY locked down anyway and they'll only have access to the Internet, they won't even be able to download anything or use their own removable media to transfer files, but this is just an extra security measure to refresh the profiles with a clean copy once in a while) or clone my setup on a new user account by copying files manually. I don't wanna copy the whole home folder, just the Firefox profile, custom wallpaper, GNOME panel layout, and pessulus settings. Which files/folders would I copy?

Rsync only copies files that have changed; it's very fast if little or nothing has changed.  Unless there's something you specifically want to persist between sessions, there's no reason not to simply rsync the whole folder.  If there is something you want to persist, it's likely easier to exclude those directories using rsync's --exclude switch.

---

### Post by oldfred on 2011-12-06
I move my Thunderbird & Firefox to another location and use profile.ini to find the new location.
All of Firefox is normally in .mozilla/firefox

In one of the discussions of backups it was suggested not to back this up, but in your case you may want to houseclean it regularly.

/home/*/.mozilla/firefox/*.default/Cache/**

---

