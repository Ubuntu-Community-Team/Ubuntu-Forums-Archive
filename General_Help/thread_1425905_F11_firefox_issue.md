---
title: "F11 firefox issue"
date: 2010-03-09
forum: General Help
---

### Post by square_root on 2010-03-09
Hi folks, I've lurked a while and read a lot, done a lot of searching here and with google but haven't found an answer. I have a question I hope you can help me with and I hope I haven't missed anything obvious.

I'm using full ubuntu karmic on an Asus 1008ha, not UNR. In firefox, F11 used to give me full screen all content, but suddenly now for some reason it keeps the toolbars and search panel at the top of the screen. I preferred it the other way, how do I find the option to change it back? And what did I do  to make it like that? I've uninstalled and reinstalled firefox, I've tried all the view menu options.

What am I missing? Is it a firefox issue or a gnome issue?
Thank you in advance for your help.

---

### Post by hhh on 2010-03-09
F11 should still give you toolbars, but they will autohide if you move your cursor off of them. Is that not happening?

---

### Post by square_root on 2010-03-09
Nope they don't autohide. They did before, for some strange reason they don't now. Where do I find an autohide option?

---

### Post by lovinglinux on 2010-03-09
You are looking for **browser.fullscreen.autohide** option. Make sure it is set to **true**. You can access it by typing **about:config** in the address bar.

If you don't like the behavior of Firefox full screen, use the [Full Fullscreen](https://addons.mozilla.org/en-US/firefox/addon/1568) extension, which allows to customize which tool bars are shown when you hit F11.

---

### Post by square_root on 2010-03-09
> You are looking for **browser.fullscreen.autohide** option. Make sure it is set to **true**
That didn't do it.

Full fullscreen add-on does work if I set it to open in fullscreen, but it doesn't do autohide or fullscreen from an already open window. Wish I knew what was going on here, it worked before and then it stopped. Everything else has been incredibly smooth for ubuntu on this brand new netbook.

At least it's only aesthetic and not a major function issue ;)

Thank you for all the suggestions so far, very much appreciated.

---

### Post by lovinglinux on 2010-03-09
> **square_root said:**
> That didn't do it.

Full fullscreen add-on does work if I set it to open in fullscreen, but it doesn't do autohide or fullscreen from an already open window. Wish I knew what was going on here, it worked before and then it stopped. Everything else has been incredibly smooth for ubuntu on this brand new netbook.

At least it's only aesthetic and not a major function issue ;)

Thank you for all the suggestions so far, very much appreciated.

Close Firefox, then make a backup of the file *localstore.rdf* located inside your Firefox profile folder and delete the original. When you start Firefox again it will reset all toolbar customizations and probably fix your problem. If that doesn't work, then restore the file backup to revert the changes and start Firefox in safe mode. To do that, run the following command from a terminal:

```
firefox -safe-mode
```

If it works as it should, then you have an extension messing with the fullscreen mode.

---

### Post by square_root on 2010-03-10
Thank you but still no joy. Those toolbars and search panel are steadfastly refusing to autohide.
Back to the drawing board for me...

---

### Post by square_root on 2010-03-10
What's weird is F11 doesn't do it properly, but if I select fullscreen from the view menu that works. If I then try F11 to come out of full screen, it does, but without the toolbars etc.

---

