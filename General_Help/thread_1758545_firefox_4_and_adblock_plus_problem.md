---
title: "firefox 4 and adblock plus problem"
date: 2011-05-14
forum: General Help
---

### Post by joepotter on 2011-05-14
After doing a dist upgrade I discover that I have firefox 4.0 and it has disabled adblock plus 1.3.3 and I can not get the new adblock plus since I can not uninstal the old one. Does anyone know how to fix this short of zaping the entire .mozilla file?

---

### Post by coffeecat on 2011-05-14
From the firefox global menu (in the panel) open the Tools menu > Add-ons. The Add-ons manager will open in a new tab. Click on "Extensions" in the left pane and that should show your old Adblock Plus in the main pane where there is a "Remove" button.

After you have removed it - you may need to restart firefox - open the Add-ons manager again and you can search for and install the latest Adblock Plus under "Get Add-ons". The version of Adblock plus I have in FF4 is 1.3.7 and it seems to be working well.

---

### Post by joepotter on 2011-05-14
Sorry but that does not work. There was a complaint of some file that could not be removed. I have used firefox for years and have never seen a problem like this. I removed No-script just to test it and it removed fine but adblock plus will not leave! (nor can I upgrade)

---

### Post by coffeecat on 2011-05-14
Sorry to hear that.

If you are thinking of removing the .mozilla folder, try removing just the ~/.mozilla/firefox/*random-string*.default/adblockplus folder + contents. I have no idea whether that will help, but it might be worth trying.

---

### Post by joepotter on 2011-05-15
> **coffeecat said:**
>  ... try removing just the ~/.mozilla/firefox/*random-string*.default/adblockplus folder + contents. ...

That did not work so I renamed the .mozilla folder and started fresh. I was able to save bookmarks and passwords so it was not a huge deal, but it was a odd thing. Adblock plus is working fine now and I like firefox 4 just fine.

Thanks for your advice.

---

