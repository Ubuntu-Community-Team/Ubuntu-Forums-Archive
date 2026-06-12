---
title: "Bookmarks don't show up in Gnome Panel..."
date: 2006-02-16
forum: General Help
---

### Post by qyot27 on 2006-02-16
After finding the [Browser Bookmarks Menu](http://www.gnomefiles.org/app.php?soft_id=745) applet on Gnome Files, I tried to install it, following the instructions in the readme file that came with it.  The problem is, even though it registers the menu itself on the Panel, it doesn't show any of the bookmarks themselves, including the sub-menus.

Still looking at the readme, I checked to see if I had the packages listed there, and those checked out as being the latest versions.  I tested the *./browser-bookmarks-menu.py -print* command, and at first it threw an error, but apparently I did something and it works fine now, and lists all my bookmarks, but when I run the *-window* command, it gives me this:

```
Traceback (most recent call last):
  File "./browser-bookmarks-menu.py", line 633, in on_menu_shown
    fill_root_menu(menu)
  File "./browser-bookmarks-menu.py", line 518, in fill_root_menu
    fill_menu(menu, tooltips, bookmarks_tree, favicons)
  File "./browser-bookmarks-menu.py", line 538, in fill_menu
    fill_menu(sub_menu, tooltips, folder, favicons)
  File "./browser-bookmarks-menu.py", line 546, in fill_menu
    if favicons.has_key(href):
AttributeError: 'NoneType' object has no attribute 'has_key'
```

When I use the *-print* command as root, though, I get this (which I believe was the original error I got as well):
```
(browser-bookmarks-menu:20299): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

Am I missing a needed package, or is there something in the Python script that's conflicting, or is it that this particular applet doesn't run on Breezy?  I did follow the guide on the Wiki to install Firefox 1.5.  Would the presence of 1.5 have something to do with it?

---

### Post by eombah on 2007-09-01
A rather old post I am replying to, but I run into the same error.
I installed Browser Bookmarks Menu 0.6 from [http://www.gnomefiles.org/app.php?soft_id=745](http://www.gnomefiles.org/app.php?soft_id=745).
Running 

  ./browser-bookmarks-menu.py -window

gives:


Traceback (most recent call last):
  File "./browser-bookmarks-menu.py", line 633, in on_menu_shown
    fill_root_menu(menu)
  File "./browser-bookmarks-menu.py", line 518, in fill_root_menu
    fill_menu(menu, tooltips, bookmarks_tree, favicons)
  File "./browser-bookmarks-menu.py", line 546, in fill_menu
    if favicons.has_key(href):
AttributeError: 'NoneType' object has no attribute 'has_key'

(browser-bookmarks-menu:7712): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition

any ideas?

cheers Bart.

---

### Post by gtr225 on 2007-09-03
I can't seem to get it working right either.

---

### Post by Jose Catre-Vandis on 2007-09-03
Got most of the functionality going by editing the .py file (means you don't get favicons though)

open the bookmarks py file:

```
sudo nano /usr/lib/browser-bookmarks-menu/browser-bookmarks-menu.py
```

page down eleven times (with a full screen terminal) or until you get to line 546  (Use CTRL+C to find out where you are)

Comment out lines 546 through to and including 552, like so:
>                                         href = href_or_folder
                                        tooltips.set_tip(menu_item, href)
                                        if global_unsupported_url_pattern.search(href):
                                                menu_item.set_sensitive(False)
                                        else:
                                                menu_item.connect("activate", url_show, (name, href))
#                                       if favicons.has_key(href):
#                                               image = gtk.Image()
#                                               image.set_from_pixbuf(favicons[href])
#                                               menu_item.set_image(image)
#                                       elif global_query_url_pattern.search(href):
#                                               image = gtk.image_new_from_stock(gtk.STOCK_FIND, gtk.ICON_SIZE_MENU)
#                                               menu_item.set_image(image)
                        menu.append(menu_item)


Don't mess with the indenting of uncommented lines!

then save the file: CTRL+X, then Y, then Enter

Try Bookmarks again and all should work, not pretty, but functional  :)

---

