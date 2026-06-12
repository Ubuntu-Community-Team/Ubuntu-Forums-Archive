---
title: "Missing windows menus with minimize/restore/close buttons"
date: 2011-04-30
forum: General Help
---

### Post by Vahagn_IV on 2011-04-30
Hi all.

I have just upgraded my ubuntu to 11.04. Then I tried to remove the gnome panel and removed the key desktop->gnome->session->required components-> panel. After restart the panel disappeared. However, together with gnome top panel all the menus with minimize/restor/close buttons vanished. 
See the screenshot.
[IMG]http://ubuntuone.com/p/pdy/[/IMG]
Some searching in the internet prompted to type in terminal
```
metacity --replace
```
Although this returns the menus back, it leads to some strange appearance. See screenshot

[IMG]http://ubuntuone.com/p/pe2/[/IMG]

Please, help me to return the menus back without contributing the half of desktop.

Thanks in advance.

P.S.

Don't remember when but I also typed 
```
compiz --replace
```
in terminal.

---

### Post by Vahagn_IV on 2011-05-01
:shock: No one knows? :shock:

---

### Post by Krytarik on 2011-05-01
Check the setting "CompizConfig Settings Manager -> Window  Decoration", it should be "/usr/bin/compiz-decorator".
Also make sure that those  plugin is enabled.

Also, do the window decorations come up if you run "gtk-window-decorator --replace" through the Alt+F2 dialog?

Greetings.

---

### Post by Vahagn_IV on 2011-05-02
**Krytarik**, thanks for reply. 
Please, take a look on [the screenshot]("http://ubuntuone.com/p/pwh/") of CompizConfig Settings Manager's Windows Management Tab. Nothing happens when I run 
```
gtk-window-decorator --replace
```

---

### Post by Krytarik on 2011-05-02
> **Vahagn_IV said:**
> 
Please, take a look on [the screenshot]("http://ubuntuone.com/p/pwh/") of CompizConfig Settings Manager's Windows Management Tab.
I said "Window Decoration". However, since you are most probably missing some packages, run this first:
```
sudo apt-get install --reinstall compiz
```

---

### Post by Vahagn_IV on 2011-05-02
> **Krytarik said:**
> I said "Window Decoration".
I can't find it in the settings manager menu. Should it be on the left side of the Compiz Settings manager? 
Nothing changed after reinstall(I did it before via synaptic package manager). 
However, I have noticed the following:
When I run Gconf cleaner everything disappears from the Desktop, so that I need to force restart my laptop. After loading the titlebar appears. However, in the CompizConfig Settings manager the Desktop Cube effect appears to be disabled. Enabling that leads to the same issue as in the initial post.

---

### Post by Krytarik on 2011-05-02
"Window Decoration" is
- in the main page, right when you launch CCSM, or section "All"
- under the subsection "Effects"
- of course, you can also just search for the name

Enabling "Desktop Cube" may disable "Window Decoration", check if any more plugins were disabled when you enabled it.

Btw., what exactly do you mean by "Gconf cleaner"?

---

### Post by Vahagn_IV on 2011-05-02
> **Krytarik said:**
> 
Enabling "Desktop Cube" may disable "Window Decoration", check if any more plugins were disabled when you enabled it.

Thank you very much!!!
It was disabled.
> **Krytarik said:**
> 
Btw., what exactly do you mean by "Gconf cleaner"?
Just type
```
gconf-cleaner
```
in terminal. You'll see it.

Thanks again.

---

