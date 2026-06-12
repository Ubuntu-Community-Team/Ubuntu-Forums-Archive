---
title: "Menu buttons (close, maximise, minimise) sometimes greys out even when at front"
date: 2011-11-20
forum: General Help
---

### Post by bastones on 2011-11-20
I don't know to describe the problem properly, but sometimes some windows, even when they are active and at the front the menu buttons for close, minimise and maximise turn to default gray colours compared to the ordinary orange colour of the close button, for example.

To illustrate, I have attached a screenshot showing the problem occurring. I have an ATI Radeon 6450 Graphics Card with the proprietary drivers from the AMD ATI website.

Thanks,
bastones.

Edit: Realised it was due to the AMD ATI driver. In my experience the open source drivers behave much better than the proprietary fglrx drivers. You can uninstall the proprietary drivers using [FONT="Courier New"]aticonfig --uninstall[/FONT] and then replacing the current [FONT="Courier New"]xorg.conf[/FONT] file with the original one from [FONT="Courier New"]/etc/X11[/FONT]. Such as:

```
cd /etc/X11
cp xorg.conf.original-0 xorg.conf
```

To see what the original configuration file is called, use:

```
ls
```

(That's an L, not an I)

Hope this helps.

If you experienced freezing issues with ATI Radeon 6450, this is fixed in Linux Kernel 3.0.x. Simply use Update Manager until all updates are applied, ensure you have the newest 3.0.x kernel with [FONT="Courier New"]uname -r[/FONT] via a Terminal window. Then uninstall as per instructions above. You don't need to reboot after uninstalling fglrx until you have restored the [FONT="Courier New"]xorg.conf[/FONT] file.

---

### Post by bastones on 2011-11-22
Anyone?

---

### Post by bastones on 2011-11-30
Anyone?

---

