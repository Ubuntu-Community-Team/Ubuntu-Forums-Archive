---
title: "fast user switch applet loads but is unusable"
date: 2009-09-23
forum: General Help
---

### Post by GPJ on 2009-09-23
Fast-user-switch-applet ("FUSA") loads cause I can see it at system monitor's proccess table, but it became a thin line at the panel, similar to a separator. It does not show the username or the icon. In other words it lost its visual area in the panel, except for that thin line I mentioned.

This makes it absolutely unusable, cause I cant click on it.

I tried many actions that didn't work: 
1) reinstall it; 
2) remove it from the panel (the only way to do this is to kill it, cause I cant select it with mouse click) and then add it again by right clicking in the panel + add action; 
3) check out for any wrong configuration in the conf-editor keys, comparing them to the ones within my laptop where FUSA is working fine - note: I use version 9.04 in both desktop (32bit) and laptop (64bit); 
4) restarted the panel, the FUSA itself and the system many times to see if the changes I made took effect, but no way.

I believe that 3 prior actions might have caused this problem, but I am not sure and don't know why:
1) I also have Kubuntu desktop on my system to use some KDE applications, but I had never used a KDE session before yesterday, when the problem occurred; 
2) Evolution crashed when I tried to change some events in the Calendar application, right before I first became aware of the "missing" FUSA;
3) I made some updates suggested by the notification applet.

Please note that another problem occurred at the same time and possibly by the same reason. All itens from my Desktop area disappeared, but I still could see them at the folder Desktop using Nautilus. I solved this last issue partialy by using conf-editor. I dont know why "/apps/nautilus/preferences/show desktop" key checkbox became unchecked. The problem is that event checked, I must star Nautilus everytime I want to see my icons on Desktop cause they do not load automaticaly as it would be expected. Unfortunatelly, as previously said, I didn't have any luck with FUSA in the conf-editor.

Could anyone have any idea?

Thanks.

---

### Post by GPJ on 2009-09-27
I solve it myself. In a terminal (or with Alt+F2) type gconf-editor.

1) To enable FUSA: browse to the /desktop/gnome/lockdown key and uncheck "disable_user_switching" option. Then add FUSA to the panel such as any other applet (by right clicking an empty area in the panel and choosing add to the panel).

2) To enable desktop icons: browse to /desktop/gnome/sessions "required_components_list" key and add value "filemanager". Also verify if the value "nautilus" apears in the /desktop/gnome/sessions/required_components_list "filemanager" key. If not edit it and add nautilus. Browse to /apps/nautilus/preferences and check the "show_desktop" checkbox option. Finally, browse to /apps/nautilus/desktop key and check the corresponding checkbox of the itens you would like to see in your desktop. You can also name the icons by adding values to the corresponding fields.

As I mentioned in my previous post, I dont know what exactly causes this mess in my gconf-editor default options, when everything was working fine, but I strongly suspect of my KDE session's first use.

I hope it helps someone else.

Regards.

---

### Post by cyroul on 2009-10-10
Thanks for that, I had the same issue for some reasons but now fixed

---

### Post by heryatmadja on 2010-02-11
Thanks so much.  This is the solution that I've been searching for.

---

