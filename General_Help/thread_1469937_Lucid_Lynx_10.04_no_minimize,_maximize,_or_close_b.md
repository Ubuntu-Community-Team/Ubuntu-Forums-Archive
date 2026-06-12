---
title: "Lucid Lynx 10.04 no minimize, maximize, or close buttons"
date: 2010-05-02
forum: General Help
---

### Post by linuxdualbooter on 2010-05-02
When I launch into any program, the top bar is missing. Also, it will not let me maximize the page even with F11.

---

### Post by dv3500ea on 2010-05-02
Try pressing Alt-F2
and typing:
```
metacity --replace
```
or
```
compiz --replace
```
and see what happens

---

### Post by linuxdualbooter on 2010-05-11
The first one actually did more harm but the second one did help. I ended up rebooting the computer and had to add the applets back on to the top menu bar. However there are some applets that i cannot find.

---

### Post by kio_http on 2010-05-11
> **linuxdualbooter said:**
> The first one actually did more harm but the second one did help. I ended up rebooting the computer and had to add the applets back on to the top menu bar. However there are some applets that i cannot find.

To allow GNOME to reset itself to default settings and recreate all config fresh. (Your documents, software etc will be unchanged)

Applications Menu> Accessories > Terminal

type in and enter

```
rm -rf .gnome
```

---

### Post by Bowlcut3x on 2010-06-14
> **linuxdualbooter said:**
> When I launch into any program, the top bar is missing. Also, it will not let me maximize the page even with F11.

Hello,
I don't know if this is still a question that's been left unanswered or not. I had the same problem and what I did was just go to the Main Menu, System, Preferences, Appearance. In this window go to the last tab on top called "Visual Effects" and select the option at the bottom to enable "Extra Effects." It will ask if you want to keep the new settings, select Yes. The top menu bar should then appear.

---

### Post by gnik1 on 2010-07-10
I had the same issue with the min/max/close window buttons not appearing. Setting none for visual effects fixed my issue.

---

### Post by ecosseman on 2010-09-11
Have same problem now for a week. Only in FIREFOX.
All other windows have m/m/c buttons, which work.
Been running Nvidia 7600GT for months with Compiz, Wobbly & Cube. Still working.
Seems I've exhausted all info out there. Nothing addresses Firefox problem.
Alt F9 and Alt "right click' .... both work.
Anyone?

Update ....
Don't know what happened. Window headers went pale. Lost all control of all windows position. No Wobbly. no Cube.
In despair restarted 10.04. All fixed!!!!  Have all m/m/c buttons including Firefox. Wobbly and Cube restored????
This is odd. Hope the problem stays away.

---

