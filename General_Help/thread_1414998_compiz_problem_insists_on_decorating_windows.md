---
title: "compiz problem: insists on decorating windows"
date: 2010-02-24
forum: General Help
---

### Post by cong06 on 2010-02-24
So I don't have a very strong graphics card, and I'm trying to set up a transparent terminal.

I've been following the guide on [Tombuntu.com's site](http://tombuntu.com/index.php/2007/08/27/transparent-terminal-on-your-desktop/).

Unfortunetly, There must be a problem with compiz, because the window for the terminal is still getting decorated, still showing up in tray, etc. It's as if the settings in ccsm are being ignored.

Is there aditional software I need?
```

root@kimende-s:~# aptitude search compiz
i   compiz                                                         - OpenGL window and compositing manager                                   
i   compiz-core                                                    - OpenGL window and compositing manager                                   
p   compiz-dev                                                     - OpenGL window and compositing manager - development files               
p   compiz-fusion-bcop                                             - Compiz option code generator                                            
i   compiz-fusion-plugins-extra                                    - Collection of extra plugins from OpenCompositing for Compiz             
i   compiz-fusion-plugins-main                                     - Collection of plugins from OpenCompositing for Compiz                   
p   compiz-fusion-plugins-unsupported                              - Compiz Fusion plugins - "unsupported" collection                        
i   compiz-gnome                                                   - OpenGL window and compositing manager - GNOME window decorator          
p   compiz-kde                                                     - OpenGL window and compositing manager - KDE window decorator            
i   compiz-plugins                                                 - OpenGL window and compositing manager - plugins                         
i   compiz-wrapper                                                 - OpenGL window and compositing manager, wrapper script                   
i   compizconfig-backend-gconf                                     - Settings library for plugins - OpenCompositing Project                  
p   compizconfig-backend-kconfig                                   - KConfig Settings library for plugins - OpenCompositing Project          
i   compizconfig-settings-manager                                  - Compiz configuration settings manager                                   
v   gcompizthemer                                                  -                                                                         
i   libcompizconfig0                                               - Settings library for plugins - OpenCompositing Project                  
p   libcompizconfig0-dev                                           - Development file for plugin settings - OpenCompositing Project          
i A python-compizconfig                                            - Compiz configuration system bindings        

```

---

### Post by cong06 on 2010-03-03
If you were follow the instructions on Tombuntu's Site, here's the fix:

Install devilspie
```

apt-get install devilspie

```

create a file:
~/.devilspie/trans.ds
and fill it with:
```

(if
    (matches (window_name) "trans")
    (begin
        (pin)
        (below)
        (undecorate)
        (skip_pager)
        (skip_tasklist)
        (wintype "desktop")
        (geometry "+0+0")
        (geometry "700x750")
        (maximize_vertically)
    )   
)

```
Which I think works... Was having some problems getting geometry to work

More rules for devilspie at the bottom of: [http://ubuntuforums.org/showpost.php?p=409863&postcount=1](http://ubuntuforums.org/showpost.php?p=409863&postcount=1)
Or better, check out the man page.

---

### Post by dragonboss on 2010-03-03
I did a similar thing just yesterday to display cmatrix. The decoration can be disabled in System > Preferences > CompizConfig Settings Manager > Window Decoration and you can remove it by typing this into the Decoration Windows box:

(any) & !(title=whateverthewindownameis)

Or alternatively you can click the + button and select type as window title, then click grab and click on the terminal for transparency then check the invert box then add

---

### Post by cong06 on 2010-03-03
The problem was compiz wasn't working (maybe a problem with my video card/driver?)
In anycase, devilspie is an alternative.

---

