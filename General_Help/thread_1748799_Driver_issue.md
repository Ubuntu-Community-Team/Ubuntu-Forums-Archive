---
title: "Driver issue"
date: 2011-05-03
forum: General Help
---

### Post by gufide on 2011-05-03
It must be user error... This is my case, I got a nvidia geforce 4 mx with nouveau driver 3d. But, for a wine game, I tried to install NV proprietary downloaded from nvidia website, because is was not in jockey-gtk. It tried to install it, it say that there's not something for my distribution, but me, like an idiot, I continue. It asking to disable nouveau, I continue, the installation was successful. But X stop working. I deleted NV, create a new xorg.cong using recovery boot option. I reinstall nouveau, but 3d don't seems to work again. I just killed my 3d... How can I solve this?

*EDIT:*

this is my compiz output: ```
compiz --replaceBackend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected
Compiz (bailer) - Info: Ensuring a shell for your session
guillaume@Bureau:~$ damage_screen (XSR): 1 rects, bounds: 0,0 (1280,1024)
expose_area (XSR): 1 rects, bounds: 0,1000 (1280,24)
expose_area (XSR): 1 rects, bounds: 0,0 (1280,24)
expose_area (XSR): 1 rects, bounds: 0,24 (1280,976)
repair_win (XSR): 1 rects, bounds: -109,-107 (19,19)
repair_win (XSR): 1 rects, bounds: 0,0 (1280,1024)
repair_win (XSR): 1 rects, bounds: -9,993 (1298,42)
repair_win (XSR): 1 rects, bounds: -9,-7 (1298,42)
configure notify 0 0 1
    extents (XSR): null
    xy (0 24), wh (1280 976)
no extents to damage !
resize_win (XSR): 1 rects, bounds: -9,17 (1298,994)
configure notify 0 0 1
    extents (XSR): 1 rects, bounds: -9,17 (1298,994)
    xy (0 24), wh (1280 976)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,17 (1298,994)
repair_win (XSR): 1 rects, bounds: -109,-107 (19,19)
configure notify 0 1 1
    extents (XSR): null
    xy (0 24), wh (657 431)
no extents to damage !
resize_win (XSR): 1 rects, bounds: -9,17 (675,449)
configure notify 0 1 1
    extents (XSR): 1 rects, bounds: -9,17 (675,449)
    xy (0 24), wh (657 431)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,17 (675,449)
configure notify 0 1 1
    extents (XSR): 1 rects, bounds: -9,17 (675,449)
    xy (0 24), wh (657 431)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,17 (675,449)
configure notify 0 1 1
    extents (XSR): 1 rects, bounds: -9,17 (675,449)
    xy (0 24), wh (657 431)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,17 (675,449)
paint_all (XSR): 2 rects, bounds: -109,-107 (1398,1142)
    -9,-7 (1298,1042)
repair_win (XSR): 2 rects, bounds: 24,1000 (1230,24)
    230,1000 (1024,24)
repair_win (XSR): 1 rects, bounds: 34,1000 (391,24)
paint_all (XSR): 1 rects, bounds: 24,1000 (1230,24)
expose_area (XSR): 1 rects, bounds: 5,24 (647,1)
expose_area (XSR): 1 rects, bounds: 3,25 (651,1)
expose_area (XSR): 1 rects, bounds: 2,26 (653,1)
expose_area (XSR): 1 rects, bounds: 1,27 (655,2)
expose_area (XSR): 1 rects, bounds: 0,29 (657,426)
repair_win (XSR): 1 rects, bounds: -9,17 (675,449)
determine_mode (XSR): 1 rects, bounds: -9,17 (675,449)
resize_win (XSR): 1 rects, bounds: -15,9 (693,467)
expose_area (XSR): 1 rects, bounds: 0,24 (1280,29)
repair_win (XSR): 1 rects, bounds: 1,53 (655,401)
repair_win (XSR): 2 rects, bounds: 229,1000 (1025,24)
    1141,1000 (113,24)
repair_win (XSR): 1 rects, bounds: -9,17 (1298,994)
paint_all (XSR): 5 rects, bounds: -15,9 (1304,1015)
    -15,17 (1304,459)
    -9,476 (1298,535)
    229,1011 (196,13)
    1141,1011 (113,13)
repair_win (XSR): 1 rects, bounds: 1,78 (655,376)
paint_all (XSR): 1 rects, bounds: 1,78 (655,376)
repair_win (XSR): 2 rects, bounds: 1,78 (655,376)
    1,438 (642,16)
paint_all (XSR): 2 rects, bounds: 1,78 (655,376)
    1,438 (642,16)
repair_win (XSR): 2 rects, bounds: 1,78 (655,376)
    1,438 (642,16)
paint_all (XSR): 2 rects, bounds: 1,78 (655,376)
    1,438 (642,16)
repair_win (XSR): 2 rects, bounds: 1,78 (655,376)
    1,438 (642,16)
paint_all (XSR): 2 rects, bounds: 1,78 (655,376)
    1,438 (642,16)
repair_win (XSR): 2 rects, bounds: 1,78 (655,376)
    1,438 (642,16)
paint_all (XSR): 2 rects, bounds: 1,78 (655,376)
    1,438 (642,16)
repair_win (XSR): 2 rects, bounds: 1,78 (655,376)
    1,438 (642,16)
paint_all (XSR): 2 rects, bounds: 1,78 (655,376)
    1,438 (642,16)
repair_win (XSR): 2 rects, bounds: 1,78 (655,376)
    1,438 (642,16)
paint_all (XSR): 2 rects, bounds: 1,78 (655,376)
    1,438 (642,16)
repair_win (XSR): 2 rects, bounds: 1,78 (655,376)
    1,438 (642,16)


```Then I tried again and I get: ```
compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected
Compiz (bailer) - Info: Ensuring a shell for your session

```

---

