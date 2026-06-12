---
title: "Icon Theme resets on logon"
date: 2010-01-02
forum: General Help
---

### Post by bala1979 on 2010-01-02
Hi All
I am newbie to Ubuntu. Very recently I installed Karmic Koala and I am dual booting with Windows Vista. Everything works fine. I just have one minor issue. My custom icon theme (Mac4Lin) doesn't get applied automatically when I logon. Because of this I am not able to control volume through the laptop volume control buttons. All my icons are defaulted to the Gnome theme. But as soon as I click on Appearances or right click and click on Change Background, the icon theme gets applied. First I thought it is an issue with Mac4Lin but this issue exists even if I use other Ubuntu themese like Human or Clearlooks etc. 
I have attached images of my Desktop immediately after logon (with the icon theme not applied) and then with the theme applied(after I click on Appearances). My settings for the theme and icon theme seem to be ok. Check the theme and icon them images in the attachment. 
The issue reported in this thread [http://ubuntuforums.org/showthread.php?t=1045426](http://ubuntuforums.org/showthread.php?t=1045426) is exactly the same as mine but the poster hasn't explained in detail how he solved the issue. He has mentioned something about gnome-settings-daemon which I am not familiar with. Please let me know if there is a solution to this.

Thanks
Bala S

---

### Post by bala1979 on 2010-01-03
Solved the issue... It was indeed the Gnome Settings Daemon .. it was disabled in the list of startup applications(not sure how it was disabled, maybe I did it without knowing what it was for)....After enabling it, the custom icon theme gets applied without any issues..

---

