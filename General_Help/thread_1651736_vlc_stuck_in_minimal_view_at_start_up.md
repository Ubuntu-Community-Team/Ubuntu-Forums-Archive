---
title: "vlc stuck in minimal view at start up"
date: 2010-12-23
forum: General Help
---

### Post by Dex73 on 2010-12-23
I can't get vlc to stop starting up in minimal view. I clicked the minimal option in view to try it out and can click it again to fix it via right click/view/minimal view. However, this doesn't stop it from starting up in minimal view.(For some reason pressing control+H doesn't work either, even though that's what is listed as the shortcut right beside the option)

I've even gone as far as to uninstall and reinstall vlc using ubuntu software center, which I thought would reset everything. Now when I start videos or a just try to start vlc, I don't have access to my buttons without changing the view setting. This is crap for me. I use the slider all the time!

Can someone please help me figure this one out. I've tried to search for a solution online and checked the pages under help in vlc, but have yet to find a solution.

---

### Post by oarion7 on 2010-12-23
> **Dex73 said:**
> I can't get vlc to stop starting up in minimal view. I clicked the minimal option in view to try it out and can click it again to fix it via right click/view/minimal view. However, this doesn't stop it from starting up in minimal view.(For some reason pressing control+H doesn't work either, even though that's what is listed as the shortcut right beside the option)

I've even gone as far as to uninstall and reinstall vlc using ubuntu software center, which I thought would reset everything. Now when I start videos or a just try to start vlc, I don't have access to my buttons without changing the view setting. This is crap for me. I use the slider all the time!

Can someone please help me figure this one out. I've tried to search for a solution online and checked the pages under help in vlc, but have yet to find a solution.

VLC preferences are stored in the **vlcrc** file in **~/.config/vlc**. If you uninstalled and reinstalled VLC, those settings would probably have been retained. You could delete that file, and have it regenerated next time you run VLC. But then you'll lose any other preferences or settings you might have configured in VLC.

I have noticed today that there are some issues with the Ctrl+H feature in VLC. That keyboard command doesn't seem to work when the video is displaying in minimal mode, and it only seems to switch from minimal mode to full control mode if the last thing I clicked on was the empty space next to the control buttons. If I click on the video and then try to do it, it doesn't work.

---

### Post by Dex73 on 2010-12-23
I wiped out the file then started vlc and it worked. Luckily I had very few customizations to it, so I had little to fix. Thanks for all the help. Now we just have to wait for ctrl+H to work. But that is of little concern to me.

---

