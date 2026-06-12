---
title: "How to close &quot;5900/tcp open  vnc&quot;"
date: 2011-10-01
forum: General Help
---

### Post by khaos1 on 2011-10-01
Hi guys. I have portscanned my localhost and I found that 5900 is open (only in lan level) and I want to close it. I have changed the config in krfb but with no luck. Where I must find the setting to deactivate the vnc daemon?

---

### Post by khaos1 on 2011-10-02
anyone? thanks

---

### Post by spiky001 on 2011-10-02
If you go system/preferences/remote desktop you should be able to unselect remote desktop

---

### Post by khaos1 on 2011-10-02
I can't find remote desktop disable setting. Im using Kubuntu 11.04.

---

### Post by spiky001 on 2011-10-02
Have a look in internet/krfb. here is a link to set it up [http://www.geekyard.com/os/linux-os/enable-remote-desktop-vnc-on-kubuntu/](http://www.geekyard.com/os/linux-os/enable-remote-desktop-vnc-on-kubuntu/) if you untick the boxes it should disconnect it

---

### Post by khaos1 on 2011-10-02
I have all the settings unticked. But when I make a portscan to localhost I see open the vnc port! Why?

---

### Post by spiky001 on 2011-10-02
Have you tried scanning from outside, [http://nmap-online.com/](http://nmap-online.com/)  [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)  see if it visible from outside

---

### Post by khaos1 on 2011-10-03
The port is not forwarded and its not shown from outside. I want to close it localy and I can't. Is there any way to disable the daemon? I can't find the disable feature in the settings

Thanks

---

### Post by Dangertux on 2011-10-03
You can try the following

```

gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false

```

if that doesn't work

```

sudo ufw deny from any to any port 5900 proto tcp

```

---

### Post by khaos1 on 2011-10-04
Thanks but I'm not using gnome. I use KDE (Kubuntu 11.04 as I said) and the gconftool command is not working

---

