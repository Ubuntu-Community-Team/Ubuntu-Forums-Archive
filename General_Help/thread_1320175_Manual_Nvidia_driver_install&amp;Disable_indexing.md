---
title: "Manual Nvidia driver install&amp;Disable indexing"
date: 2009-11-09
forum: General Help
---

### Post by 133794m3r on 2009-11-09
For some reason i cannot install my own nvidia driver which is the 190 release ones. Ubuntu only has 185 and 173. Also when i attempt to do it from the Ctrl+Alt+F1 terminal, i cannot stop the GDM or the x server. It seems completely impossible to do.

Also i cannot find a way to stop indexing. As i'm someone who never searches for anything on my own hdd i find this service as a pointless waste of resources.

---

### Post by Dark_Stang on 2009-11-09
To stop GDM and X.
```
sudo /etc/init.d/gdm stop
```

For indexing, you could uninstall Tracker if you'll never use indexing. I don't search for my own files either, so it isn't installed on mine.

---

### Post by 133794m3r on 2009-11-09
> **Dark_Stang said:**
> To stop GDM and X.
```
sudo /etc/init.d/gdm stop
```

For indexing, you could uninstall Tracker if you'll never use indexing. I don't search for my own files either, so it isn't installed on mine.

that doesn't work... i tried it and sudo /etc/init.d/gdm stop doesn't do it for me.

I get an error saying that 
Gnome.Display Manager (some random text) 
GDM (random text) warning error

then i try to install it and it tells me x hasn't exited. So it's not working for me on ubuntu 9.10

---

### Post by praveenthivari on 2009-11-09
> **133794m3r said:**
> that doesn't work... i tried it and sudo /etc/init.d/gdm stop doesn't do it for me.

I get an error saying that 
Gnome.Display Manager (some random text) 
GDM (random text) warning error

then i try to install it and it tells me x hasn't exited. So it's not working for me on ubuntu 9.10

Try this:
[FONT=Courier New]sudo stop gdm[/FONT]

---

### Post by Arup on 2009-11-09
It should be sudo service stop gdm and you will get a message gdm/waiting which confirms that gdm has been stopped.

---

### Post by cariboo on 2009-11-09
If you are running Karmic /etc/init.d/gdm stop doesn't work any more. try:

```
sudo service gdm stop
```

**Edit:** Arup beat me to it. :)

---

### Post by 133794m3r on 2009-11-09
that worked thankfully. Now all i need to do is restart my pc to finish it all. That is including all the updates.

---

### Post by praveenthivari on 2009-11-09
> **Arup said:**
> It should be sudo service stop gdm and you will get a message gdm/waiting which confirms that gdm has been stopped.

Even just '[FONT=Courier New]sudo stop gdm[/FONT]' works. Try it.

---

### Post by Arup on 2009-11-09
> **praveenthivari said:**
> Even just '[FONT=Courier New]sudo stop gdm[/FONT]' works. Try it.

Yes it does.

---

