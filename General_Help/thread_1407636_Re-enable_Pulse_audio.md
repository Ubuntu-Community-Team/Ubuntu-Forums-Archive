---
title: "Re-enable Pulse audio"
date: 2010-02-15
forum: General Help
---

### Post by Ameades on 2010-02-15
Hello,

I followed these commands to disable pulseaudio in ubuntu 9.10 and now it seems I've broken gnome-volume-control.  How can I go about undoing these changes???

```
touch ~/.pulse-a11y-nostart
echo autospawn = no|tee -a ~/.pulse/client.conf
killall pulseaudio
```

Many thanks.

---

### Post by jocko on 2010-02-15
> **Ameades said:**
> Hello,

I followed these commands to disable pulseaudio in ubuntu 9.10 and now it seems I've broken gnome-volume-control.  How can I go about undoing these changes???

```
touch ~/.pulse-a11y-nostart
echo autospawn = no|tee -a ~/.pulse/client.conf
killall pulseaudio
```Many thanks.

Remove the files you created:
```
rm ~/.pulse-a11y-nostart  ~/.pulse/client.conf
```
Start pulseaudio:
```
pulseaudio -D
```

---

### Post by Ameades on 2010-02-15
Worked like a charm.  Thank you very much :)

---

