---
title: "Bad skin messed up VLC Media Player"
date: 2011-10-12
forum: General Help
---

### Post by huggs on 2011-10-12
I changed skins in my VLC media player, as I have a few different skins for it. I have never had a problem before when changing skins, but this time, I changed skins while a movie was playing in VLC. 
The video disappeared, but the sound continued. When I tried to bring up the preferences menu to change back to another skin, I discovered that I couldn't click on anything anywhere. I couldn't click on launchers, my main menu icon, I couldn't right-click, nothing.
So I restarted my computer, went into Synaptic, uninstalled VLC, and reinstalled it in the hopes that it would be reverted back to the default skin. But no luck, the behavior remains the same.

Can someone please tell me where the data or config file or whatever is stored for VLC? I assume I would just have to delete it and then VLC should go back to default config right?
Thanks for any help guys

---

### Post by mc4man on 2011-10-12
It's typically in ~/.config/vlc, or just delete the vlc folder itself
Otherwise you should be able to start vlc from terminal with this, then set back to default interface (qt4
```
vlc -Iqt4
```

---

### Post by huggs on 2011-10-12
> **mc4man said:**
> It's typically in ~/.config/vlc, or just delete the vlc folder itself
Otherwise you should be able to start vlc from terminal with this, then set back to default interface (qt4
```
vlc -Iqt4
```

Thanks, deleting ~/.config/vlc did it for me
Back to my movie now:p

---

