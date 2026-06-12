---
title: "Cairo Dock themes"
date: 2009-10-29
forum: General Help
---

### Post by lacktorium on 2009-10-29
Cairo dock is unable to resolve host address "themes.cairo-dock.org"
resulting in not being able to change themes and images like dustbin not loading.

i have no proxy's and can connect to the host using firefox any idea's?

---

### Post by fabounet on 2009-10-30
can you try to do 
wget [http://themes.cairo-dock.org/liste.txt](http://themes.cairo-dock.org/liste.txt)
in a terminal ?
this is roughly the command used by the dock.

also, what if you start the dock manually ? maybe the connection is not established immediately on startup. In this case, you can start the dock with a delay, with a command like
sleep 10 && cairo-dock -o
or 
sleep 10 && cairo-dock -c

---

### Post by greentico on 2009-10-31
that command line worked but still no themes.  also i've noticed that it says that it cannot connect to the internet when trying to load other icon packages and the weather.  

I just did a fresh install of karmic 9.10.

---

### Post by lacktorium on 2009-10-31
Terminal connects and gets file just fine, but still nothing on the dock. i was able to solve a few issues by manuly downloading and adding the the theme to /home/username/.config/cairo-dock/themes but that dosn't fix the script issues like dustbin and weather apps that it pulls from the site.

I also just did a fresh install of karmic

edit. 

i ran *cair-dock -l debug* instead of *cairo-dock -l debug > debug.txt* and found this is the following when opening theme manager.
```

(cairo-dock-themes-manager.c:cairo_dock_list_net_themes:362)  
  listing net themes on http://themes.cairo-dock.org/themes ...
 wget "http://themes.cairo-dock.org/themes/liste.txt" -O "/tmp/cairo-dock-net-file.WDY6eR" -t 2 -T 5
--2009-10-31 11:02:44--  http://themes.cairo-dock.org/themes/liste.txt
Resolving themes.cairo-dock.org... failed: Connection timed out.
wget: unable to resolve host address `themes.cairo-dock.org'
warning :  (cairo-dock-themes-manager.c:cairo_dock_download_file:281)  
  an error occured while executing ' wget "http://themes.cairo-dock.org/themes/liste.txt" -O "/tmp/cairo-dock-net-file.WDY6eR" -t 2 -T 5'
warning :  (cairo-dock-themes-manager.c:cairo_dock_list_net_themes:368)  
  couldn't retrieve themes on http://themes.cairo-dock.org (check that your connection is alive, or retry later)
warning :  (cairo-dock-themes-manager.c:cairo_dock_list_themes:482)  
  while loading distant themes in 'http://themes.cairo-dock.org/themes' : couldn't get distant file liste.txt
s_pThemeManager:0
cairo_dock_list_local_themes (/usr/share/cairo-dock/themes)
cairo_dock_list_local_themes (/home/lacktorium/.config/cairo-dock/extras/../themes)

```

---

### Post by fabounet on 2009-11-03
could you please run the command 
```
wget "http://themes.cairo-dock.org/themes/liste.txt" -O "/tmp/cairo-dock-net-file.WDY6eR" -t 2 -T 5
```
inside a terminal, and see if it works ?
thanks.

---

### Post by lacktorium on 2009-11-03
It says connection failed, timed out. 
trying just ```
wget "http://themes.cairo-dock.org/themes/liste.txt" 
``` it gets it just fine

edit.
Thx for replying

---

### Post by fabounet on 2009-11-04
ok, there is a bug in the latest wget (don't know if it's a package problem or a real bug inside wget).
anyway, Cairo-Dock now uses curl to download the themes, it's currently available on bzr and soon on our PPA and our repository.

---

### Post by matttbe on 2009-11-06
> **fabounet said:**
> ok, there is a bug in the latest wget (don't know if it's a package problem or a real bug inside wget).
anyway, Cairo-Dock now uses curl to download the themes, it's currently available on bzr and soon on our PPA and our repository.
Hello,
It's fixed on our repository but in fact the timeout is just longer. But try to force the use of IPv4 in order to start your download faster.

---

### Post by lacktorium on 2009-11-12
thx for the help, now just have to sort out the problems with ttf-mscorefonts-installer and the public keys not being avalible.

---

