---
title: "Network-manager &quot;left click&quot; menu gone after upgrade to 12.04"
date: 2012-04-26
forum: General Help
---

### Post by Melpomene on 2012-04-26
I just upgraded to 12.04 LTS and now I can no logner "left-click" on my Network-manager icon (it only shows the "rightclick" dropdown). This stops me from connecting to my VPN and changing wifi networks. 

How can I get the menu back? Or is there another way for me to connect to my VPN saved in the network-manger?

---

### Post by gennatolls on 2012-04-26
This fixed many of the problems I was having similar to yours. It does lose some of your settings so I recommend copying the two folders to a safe location where you can restore them if necessary. I just upgraded and it caused my system to turn into chaos, this fixed it though:

```
rm -r ~/.config/ ~/.cache/
```

---

### Post by Melpomene on 2012-04-26
Thank you, that solved it! 
It is not a very clean fix and I had to shuffle around the config files I needed afterwards. 
Hopefully this will be fixed in the release! :)

---

