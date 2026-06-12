---
title: "Restore the original Ubuntu 9.10 splash screen (white logo when booting/shutting down"
date: 2009-12-13
forum: General Help
---

### Post by TadasN on 2009-12-13
Hello,
I tried to change the splash screen and finally it looks like the splash screen disappeared...:( Instead of white Ubuntu logo only many letters are shown. How could I make that the white Ubuntu logo (default) would be shown again? This is how that logo I want to back looks: [http://cdn.cbsi.com.au/story_media/339299234/ubuntu-910-karmic-koala_1.jpg](http://cdn.cbsi.com.au/story_media/339299234/ubuntu-910-karmic-koala_1.jpg)

Thank you in advance for your help.

Tadas

P.S. sorry, my English isn't brilliant...

---

### Post by listerofsmeg1 on 2009-12-20
You can try just reinstalling it.  That worked for me after I installed the Kubuntu desktop, but wanted the Ubuntu splash back.

Reinstall with:
```
sudo apt-get install ubuntu-xsplash-artwork
```

Hope this helps :)

---

### Post by neu5eeCh on 2009-12-31
I just posted a request for help on this same issue (over at absolute beginners before I saw this thread).  I tried your command but Ubuntu responded that the relevant applications were already installed - 0 changed. The white logo is still gone - replaced by the Kubuntu logo.  Just figured it out (for the next beginner) - Installed USplash using Ubuntu Software Center. USplash installs the Startup Manager. Opening that, I found the option allowing me to restore the original Gnome Logo.

---

