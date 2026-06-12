---
title: "Virtualbox issues"
date: 2009-07-30
forum: General Help
---

### Post by Gameguy411 on 2009-07-30
I'm having some problems with virtualbox that would be awesomely helpful if someone could solve. First off is when I open virtual box I successfully installed windows 2000 os on it, but I can't change the screen size, Even clicking the full screen just creates a black outer box around it and the screen size of the virtualbox stays the same. Second is i'm trying to install a computer game and it keeps saying the game "has generated errors and needs to close." Can I fix this and get this game working? Any help would be appreciated. Thanks.

---

### Post by aesis05401 on 2009-07-30
> **Gameguy411 said:**
> I'm having some problems with virtualbox that would be awesomely helpful if someone could solve. First off is when I open virtual box I successfully installed windows 2000 os on it, but I can't change the screen size, Even clicking the full screen just creates a black outer box around it and the screen size of the virtualbox stays the same. Second is i'm trying to install a computer game and it keeps saying the game "has generated errors and needs to close." Can I fix this and get this game working? Any help would be appreciated. Thanks.

Start by installing the guest additions.  With VM running you should be able to click the 'Devices' menu and choose install guest additions.  

After this, you will have ability to do fullscreen, have mouse treat your VM like any other window (no rt-ctrl to get out), etc.. 

Then post back if game installation still fails.

---

### Post by yabbadabbadont on 2009-07-30
1) Make sure that you install the virtualbox guest additions inside of win2k.  That should help.
2) 3D/DirectX/OpenGL games aren't really supported in virtualbox, although 2D games usually are.

Edit: Too slow...

---

### Post by aesis05401 on 2009-07-30
> **yabbadabbadont said:**
> 1) Make sure that you install the virtualbox guest additions inside of win2k.  That should help.
2) 3D/DirectX/OpenGL games aren't really supported in virtualbox, although 2D games usually are.

Edit: Too slow...

There is experimental 3d acceleration inside VBox now. Not sure how well it works - nethack is about as modern as my gaming gets... Well - that's a lie - I Diku also ;)

---

### Post by Gameguy411 on 2009-08-01
I tried to download it and it keeps telling me it "failed downloading from the internet. Connection has timed out." Also what do the guest additions do?

---

### Post by Gameguy411 on 2009-08-01
Nevermind I got it to download. It works! Thanks guys, and just out of curiosity what does the guest additions do? There's also an option for install wine 3d should I do that if the game is still running really slow? It's an older completely 2d game just trying to see if it'll play.

---

### Post by MelDJ on 2009-08-01
the guest additions lets u use your mouse and usb devices on the virtual system. It installs them into your virtual system. When u go to fullscreen and her a black screen, trying pressing the windows button and c wat happens:popcorn:

---

### Post by Gameguy411 on 2009-08-24
I apologize for taking so long to post, as i've been away from my machine. Most of the bugs are all sorted through, but still no luck loading the game. Gets much farther, but still won't actually play.

---

### Post by P4man on 2009-08-24
does the game support windows 2000 ? It may also need directX or .NET or whatever. Check the game for requirements. Keep in mind, as far as windows and the game is concerned, you now have a (virtual) 15 year old Cirrus Logic videocard.

---

