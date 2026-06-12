---
title: "Keep root theme the same as normal theme"
date: 2006-05-08
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-05-08
How can I do this ? The root theme is ugly :(

My other question: Can I make kde any faster ? Thanks :)

---

### Post by manicka on 2006-05-08
copy the themes folder from /home/user/.themes to /usr/share/themes

---

### Post by ComplexNumber on 2006-05-08
[quote=MasterChief1234]

My other question: Can I make kde any faster ? Thanks :)[/quote]
switch of all multimedia (eg superkaramba, transparancy, bouncing cursors, system sounds, etc) and switch off services that you don't use. for example, switch off the bluetooth daemon if you don't use bluetooth etc.

---

### Post by aysiu on 2006-05-08
[QUOTE=MasterChief1234]How can I do this ? The root theme is ugly :([/quote] Go to a terminal and type ```
sudo ln -s ~/.kde /root/.kde
```

> 
My other question: Can I make kde any faster ? Thanks :) ```
sudo apt-get update
sudo apt-get install kpersonalizer bum
gksudo bum
kpersonalizer
``` In BUM, uncheck the boxes you don't want. In KPersonalizer, select "fewer effects" except you should leave "desktop wallpaper" and "image previews" checked.

---

### Post by xXx 0wn3d xXx on 2006-05-09
That command didn't work. It still has the root theme. :(

---

### Post by aysiu on 2006-05-09
[QUOTE=MasterChief1234]That command didn't work. It still has the root theme. :([/QUOTE] Hm. Maybe it won't make the symlink if the /root/.kde folder already exists. Let's try this, then: ```
sudo rm -rf /root/.kde
sudo ln -s ~/.kde /root/.kde
```

---

### Post by xXx 0wn3d xXx on 2006-05-09
[QUOTE=aysiu]Hm. Maybe it won't make the symlink if the /root/.kde folder already exists. Let's try this, then: ```
sudo rm -rf /root/.kde
sudo ln -s ~/.kde /root/.kde
```[/QUOTE]
No, :( that didn't work...

---

### Post by Harold P on 2006-05-09
Restart your GUI?

CTRL + ALT + Backspace

*Make sure you save/close anything before you do that.

---

### Post by aysiu on 2006-05-09
[QUOTE=MasterChief1234]No, :( that didn't work...[/QUOTE] Hm. Maybe I'm not using the *ln* command properly. Can you try this?

Press Alt-F2
Type ```
konqueror
```
Go to your /home/masterchief folder
Press Alt-V
Press H
This will show your hidden folders.

Type ```
kdesu konqueror
```
Go to the /root folder

Then select the /home/masterchief/.kde folder and drag it to the /root folder. Select **link here**. If it asks if you want to replace the old folder, say "yes."

That's what I was trying to do with the *ln* command, but maybe my syntax was wrong.

---

### Post by xXx 0wn3d xXx on 2006-05-09
[QUOTE=aysiu]Hm. Maybe I'm not using the *ln* command properly. Can you try this?

Press Alt-F2
Type ```
konqueror
```
Go to your /home/masterchief folder
Press Alt-V
Press H
This will show your hidden folders.

Type ```
kdesu konqueror
```
Go to the /root folder

Then select the /home/masterchief/.kde folder and drag it to the /root folder. Select **link here**. If it asks if you want to replace the old folder, say "yes."

That's what I was trying to do with the *ln* command, but maybe my syntax was wrong.[/QUOTE]
I don't know why it's not working :mad: I dragged my .kde folder from my /home/chris folder into the /root folder and selected "link here." Then I restarted x but it still won't work :(

---

### Post by aysiu on 2006-05-09
This won't *keep* your root theme the same as your normal theme, but you can at least *make* your root theme the same.

Try Alt-F2 ```
kdesu kcontrol
``` Then change the theme in root's Control Center to be the same as your user's theme.

---

### Post by xXx 0wn3d xXx on 2006-05-09
[QUOTE=aysiu]This won't *keep* your root theme the same as your normal theme, but you can at least *make* your root theme the same.

Try Alt-F2 ```
kdesu kcontrol
``` Then change the theme in root's Control Center to be the same as your user's theme.[/QUOTE]
I don't know why it's not working but I appreciate your help aysiu.

---

