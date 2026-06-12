---
title: "Need Help !!"
date: 2010-09-17
forum: General Help
---

### Post by xdweaver on 2010-09-17
My husband partictioned our hard drive Ubuntu/Windows. I use Itunes and Lime Wire a lot. When I am using Ubuntu I cant find the files we used on windows. Can anyone tell me how to access these music and pic files so I can view them and listen to them while on Ubuntu?

---

### Post by flick on 2010-09-17
The tool described at : [http://www.hackourlives.com/auto-mount-windows-partitions-in-ubuntu-10-04-lucid/](http://www.hackourlives.com/auto-mount-windows-partitions-in-ubuntu-10-04-lucid/)

sounds like it might help you out.

---

### Post by themusicalduck on 2010-09-17
If you know what folder the music files are saved in then you can navigate to them with the Ubuntu file browser.

The partition for Windows should be listed on the left in the file browser under Places, or just by clicking the Places menu in the top left and clicking your Windows partition. If it is Vista or 7, go to Users > yourusername to find familiar folders. I can't remember what it is for XP but might be something similar (Documents and Settings?)..

You could make a link to the folder by right clicking on it and selecting Make Link. Then copy the newly created file to your Desktop.

I don't think you can play music bought on Itunes in Ubuntu though.. I don't know for sure as I've never used it, but I was under the impression that music bought in Itunes only plays in Itunes.

---

### Post by Jesus_Valdez on 2010-09-17
I can confirm that you can play music bought on Itunes in Ubuntu without problems.

Apple drop DRM a year ago.

[http://www.macworld.com/article/138000/2009/01/drm_faq.html](http://www.macworld.com/article/138000/2009/01/drm_faq.html)

---

### Post by 3rdalbum on 2010-09-18
> **Jesus_Valdez said:**
> I can confirm that you can play music bought on Itunes in Ubuntu without problems.

Apple drop DRM a year ago.

[http://www.macworld.com/article/138000/2009/01/drm_faq.html](http://www.macworld.com/article/138000/2009/01/drm_faq.html)

Only on new purchases. Downloads from a year ago are still encrypted.

If he didn't actually partition (if he used the Windows based installer) then your Windows drive is at /host (within Filesystem).

---

