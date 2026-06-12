---
title: "SuperL key dont work"
date: 2009-09-30
forum: General Help
---

### Post by pjalegria on 2009-09-30
Hi

I have installed Karmic UNR and my SuperL key isnt working anymore, can some one help me please?


Thanks

---

### Post by pjalegria on 2009-10-02
bump...

---

### Post by ad_267 on 2009-10-02
What do you mean by the SuperL key?

Do you mean the left super key? Or the super key + L?

As far as I know, the super key by itself isn't supposed to do anything, and neither is super+L.

Also, since this is a Karmic issue it should really belong in the Karmic forum. If this is a bug then it should be reported.

---

### Post by Aearenda on 2009-10-02
Super_L is the left Windows key. It isn't mapped to anything useful (to me) by default, but I get it to replace ALT+F1 to trigger the menu in Karmic by setting /apps/metacity/global_keybindings/panel_main_menu to Super_L using gconf-editor.

---

### Post by pjalegria on 2009-10-02
On Jaunty UNR SuperL key (left windows key) when pressed hide all open windows and show desketop, only pressing SuperL, on Karmic UNR SuperL key dont do anything, only if maped to SuperL+any onther...:lolflag:...

---

### Post by ad_267 on 2009-10-02
Hmm, well I know that on normal Ubuntu show desktop is mapped to Ctrl+Alt+D. Just change your keyboard shortcuts to set it to SuperL.

---

### Post by pjalegria on 2009-10-02
I cant because my winkey is show as mod4... not as super

---

### Post by WSmart on 2009-10-25
[[COLOR="Blue"]Check this link for a cut and paste solution.[/COLOR]]("http://webupd8.blogspot.com/2009/10/ubuntu-karmic-make-super-key-bring-down.html") 

Hope this helps someone else.  I bet there's there's going to be quite a few people looking for a solution next week.  Wonder what the point of this was/is.

---

### Post by pjalegria on 2009-10-25
thanks, it work...:lolflag:

---

### Post by WSmart on 2009-10-25
Cool beans.   

Wonder if this will be changed before the **** hits the fan next week.  Have to look and see if there's a place to post issues.  Also noticed the Karmic vanilla live CD doesn't show the screen saying remove disc and hit enter, just shows a black screen, when you choose reboot.

This Super_L can also be changed via alt>F2 gconf-editor, go to apps>metacity and find the panel_main_menu line, edit that to say Super_L, no quotes, no arrow markers, just plain Super_L , six characters(edit: make that seven characters). 
Edit:  Looks like this does not work if you use sudo gconf-editor.  

Use it or lose it.  ```
eject -T;  eject -T;  eject -T;  eject -T
```

---

### Post by Sub101 on 2009-10-25
Just wanted to add; after doing a fresh install of Karmic I lost the Super_L key, but the fix you offered has worked.

Oddly there was no issue doing the upgrade process from Karmic Alpha 3 up to the Beta.

---

### Post by pjalegria on 2010-03-23
I fond another way 
> gconftool-2 --set /apps/metacity/global_keybindings/show_desktop --type string "Super_L"

---

