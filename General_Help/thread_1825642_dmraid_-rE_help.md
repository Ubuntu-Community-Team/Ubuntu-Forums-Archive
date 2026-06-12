---
title: "dmraid -rE help"
date: 2011-08-15
forum: General Help
---

### Post by Gabriel Aquino on 2011-08-15
Hi everybody.
I removed all my metadata using dmraid -rE, and now my hard drivers won't boot.
How can I fix it?

---

### Post by Quackers on 2011-08-15
Were you using a raid array? Do you have bios-set raid (like Intel Matrix or Nvidia)?

---

### Post by Gabriel Aquino on 2011-08-15
I was using two disks in raid 0. My bios set raid is intel matrix.

---

### Post by Quackers on 2011-08-15
Why did you try to delete the raid metadata? It is probable that you have damaged your raid array.
If you go into your bios (you may have to press ctrl + I to access the details) you may see that the raid array is deleted/damaged/degraded or failed. If this is the case you should have a look for options to repair it, althought there may be none.
If the raid array is gone then so is your old system, I'm afraid.

It's a chance to start again though - with or without raid (i have a similar system and chose to delete the raid array and just have 2 seperate discs). This works well for me and there is no reduction in usability or speed.

---

### Post by YesWeCan on 2011-08-15
I just Googled "recover raid0" and this is the first thing that came up. Hope it helps.
[http://spench.net/drupal/resources/raid0](http://spench.net/drupal/resources/raid0)

---

### Post by Gabriel Aquino on 2011-08-15
Thank you very much!
I guess I might have to format and start again

---

### Post by Quackers on 2011-08-15
Very interesting. Thanks YesWeCan :-)
Bookmarked.

---

### Post by Quackers on 2011-08-15
Gabriel Aquine, did you see post #5?

If you decide to re-install using non-raid I would advise that you delete the raid array from your bios first.

---

### Post by Gabriel Aquino on 2011-08-15
I saw post number 5, but I didn`t understand how to do that...
I also can`t access raid configuration tool by pressing ctrl-i...

But anyway thank you all very much!

---

### Post by Quackers on 2011-08-15
You may have to access your bios first and enable (or make visible) the raid array settings. There should be an option for that.
Once that is enabled you can press ctrl + I to access it.

---

