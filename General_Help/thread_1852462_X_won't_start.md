---
title: "X won't start"
date: 2011-09-30
forum: General Help
---

### Post by fadey on 2011-09-30
Hello everyone,

I'm using Kubuntu. The problem I'm facing is that system startup gets stuck... After the grub menu, I see "kubuntu" on blue screen and flashing dots for a while. Then there is a blink and system goes to text mode. I can see some startup messages (The last one is something about the battery). Then it just stops and does nothing... I can press Alt+Print_Screen+K and then there is another blink after which the system enters the graphic mode again. I see NVidia logo for a couple of seconds and then the kdm login screen. I can login and use system as usually.

Does anyone know a way to solve the problem?

---

### Post by seawolf167 on 2011-09-30
When it 'stops', can you enter tty1 normally? [CTRL][ALT][F1]

Once there can you startx or gdm normally?

```
startx
sudo service gdm start
```

---

### Post by fadey on 2011-10-07
Thanks for your reply.

When I press Alt+Ctl+F1 (I've tried Alt+F1 as well) nothing changes on screen. However I can tell I'm in the new tty, because Alt+PrScr+K won't work there. Only when I switch back to Alt+F7, I can get into graphic mode by pressing Alt+PrScr+K.

---

### Post by seawolf167 on 2011-10-08
If you know your in tty1, you can try it blind, the order of the commands should be

```
*username*
*password*
sudo service gdm restart
```

You may find [this page ]("http://en.wikipedia.org/wiki/Magic_SysRq_key")on the magic sys keys helpful as well

---

