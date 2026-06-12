---
title: "conky help !?"
date: 2010-03-13
forum: General Help
---

### Post by nos09 on 2010-03-13
[http://www.junauza.com/2009/09/15-really-awesome-conky-configurations.html]("http://www.junauza.com/2009/09/15-really-awesome-conky-configurations.html")

go to this site and see the all great conky files can somebody tell me how to get this.these are two different problems



i how to install conky scripts given on this site ?


2  and while running conky in simple mode and clicking the desktop the conky window disappiars.. how do i fix this. it happens before but somehow i fixed it. but i dont know how to fix it now ! ;)

---

### Post by nos09 on 2010-03-13
can anybody help please ???

---

### Post by stinkeye on 2010-03-14
First of all check your conky version
```
conky -v
```
and at the bottom you should have
```
 Lua bindings:
   * Cairo
   * Imlib2

```
if you don't have this un-install conky and through synaptic install the```
conky-all
```package
conky-all has been compiled with image and cairo options

The download links on the page you were looking at, should contain any scripts you need and a setup guide.
You would need to look through the conky config and check that 
*paths to scripts are correct for you
*you have all the fonts 

You may need to install other stuff like conkyforecast
[**_[COLOR="DarkRed"]Conky Hardcore PPA[/COLOR]_**]("https://launchpad.net/~conkyhardcore/+archive/ppa")

You can run any conky config with
```
conky -c /path/to/config
```
If you just enter conky in the terminal it will load **~/.conkyrc**
If you have no **~/.conkyrc** file it will load **/etc/conky/conky.conf**

As for the conky window disappearing that can usually be solved by changing own_window_type in your config.
**own_window_type normal** works fine for me
but for different video cards and drivers you could try
**own_window_type override** or
**own_window_type desktop**

From man conky
```
own_window_type
              if own_window is yes, you  may  specify  type  normal,  desktop,
              dock,  panel or override (default: normal).  Desktop windows are
              special windows that have no window decorations; are always vis&#8208;
              ible  on  your  desktop; do not appear in your pager or taskbar;
              and are sticky across  all  workspaces.  Panel  windows  reserve
              space  along a desktop edge, just like panels and taskbars, pre&#8208;
              venting maximized windows from overlapping  them.  The  edge  is
              chosen  based  on the alignment option. Override windows are not
              under the control of the window manager. Hints are ignored. This
              type of window can be useful for certain situations.

```

If your conky is disappearing when you show the desktop, untick
in CCSM > general options > Hide Skip Taskbar Windows

---

