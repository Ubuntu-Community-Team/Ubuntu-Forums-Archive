---
title: "SynCE not available on Lucid?"
date: 2010-07-23
forum: General Help
---

### Post by rebeltaz on 2010-07-23
I am trying to sync a WM2300 pocket pc to Ubuntu using the instructions on: [http://www.synce.org/moin/LegacyDevices/Ubuntu](http://www.synce.org/moin/LegacyDevices/Ubuntu) 

I am supposed to install multisync-tools opensync-plugin-evolution opensync-plugin-synce-legacy, but apt says they are not available. 

Is there somewhere I can get those for 10.4 or is there a better way?

---

### Post by ubunterooster on 2010-07-23
Try to sudo apt-get install the following: ```
opensync-plugin-synce

``````
multisync-tools

``````
opensync-plugin-evolution

```

---

