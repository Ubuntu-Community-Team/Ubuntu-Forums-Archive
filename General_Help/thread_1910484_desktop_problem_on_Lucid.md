---
title: "desktop problem on Lucid"
date: 2012-01-17
forum: General Help
---

### Post by pc.maint on 2012-01-17
Desktop is misbehaving after re-boot...

        No icons on desktop. (They are there when I browse the Desktop folder)
        No right click. (No response from any clicks on desktop)
        No background image. (Gone from /usr/share/backgrounds folder. Can change image in gconf-editor)

Everything else appears to be working OK.


Was working fine except after installing Abiword, Nautilus appearance changed...

Re-booted to see if Nautilus appearance would revert, it did.

What have I done and how can I undo it?

}:-)>

-------------------------------------
Release 10.04 (lucid) 64-bit
Kernel Linux 2.6.32.37-generic
GNOME 2.30.2

---

### Post by BC59 on 2012-01-17
Try reinstalling the desktop:

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by pc.maint on 2012-01-17
Thanks for the prompt response.

Done that, re-booted, no change...

Any other ideas?

---

### Post by pc.maint on 2012-01-17
Further adventures in 'Misbehaving Desktop'...

If I open nautilus as root (Alt-F2 gksu nautilus), the desktop flips to root's desktop and remains when nautilus is then closed. This desktop then behaves as one would expect, but it belongs to root, not the user who is logged in...

I get the feeling that I have seriously screwed something but having tried all the suggestions I can find, the problem still persists.

Everything else seems to be working perfectly, I just have no access to my own desktop...

I think I will try setting up a new user and see what that does.

If anyone has any ideas, please don't be shy. I must have done some stupid, I just want to know what so that I don't do it again.

Thanks for any help forthcoming.

}:-)>

---

### Post by pc.maint on 2012-01-17
The plot thickens...

Set up new user. Everything for that user behaves as expected. Except...

The appearance, by default should be Ambiance. The window borders are correct, however, window contents and menus (and the panels top and bottom of screen) are from another theme. Changing the theme only changes the window borders nothing else. This was the reason for the re-boot in the first place. I did something that screwed up the appearance. I think it happened when I installed and used AbiWord but not sure.

I will keep twiddling, but the next LTS is out soon so I think a clean install in April is on the cards.

Keep watching for the next exciting episode.....

}:-)>

---

### Post by pc.maint on 2012-01-17
OK.

Re-installed everything to do with nautilus. Didn't seem to do anything until I opened the Rubbish Bin to see what I had been deleting. BINGO! Desktop back. Everything back to normal. Now, how do I flag this as solved?

Thanks for the help. So long till next problem.....

---

