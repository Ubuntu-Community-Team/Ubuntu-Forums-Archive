---
title: "Fatal error using update-alternatives x-cursor-theme"
date: 2010-11-02
forum: General Help
---

### Post by Vegaxus on 2010-11-02
Hi everyone.

I was fixing the ubuntu's cursor bug (no change the local one) when i found another bug in using the "Update-alternative" cmd on terminal.

When i try to change the x-cursor-theme, show me this messege:

```
  
-$ sudo update-alternatives --config x-cursor-theme
-$ (i pick an option)

**update-alternatives: error:  It cannot install /etc/alternatives/x-cursor-theme.dpkg-tmp as /etc/alternatives/x-cursor-theme: There is not the file or folder**
```

In the same time, the file x-cursor-theme at /etc/alternatives is corrupt and only let me delete it and the index.theme at /usr/share/icons/default/ is corrupt as well.

I did:

$sudo update-alternatives --remove-all x-cursor-theme

Trying to restore the files but is impossible, i think i lost those files above and broke the update-files, now, the group x-cursor-theme do not have any alternatives.

Anyone could help me to fix this problem before i ended tearing down the all the operative system? 

Regards

---

### Post by hellblazer on 2010-11-04
hehehe, I've also broken mine but not as bad as you have ;)

I'm not getting new pointer themes to show on the list, but I might be able to help you fix you're issue.

Open System > Administration > Synaptic Package Manager and search for dmz-cursor-theme. It should be installed. Right click and select Mark for Reinstallation.

If my theory is correct this will restore your defaults.

If not, please report back and we'll try something else. :)

---

### Post by Vegaxus on 2010-11-17
Good afternoon.

It has been a long time i was around here. This mess i made is fully solved, i just had to remove manually the "index.theme" file from the /usr/share/icons/default/ folder and also remove the "x-cursor-theme" file from the /etc/alternatives folder. 

Then i made a "$ sudo update-alternatives --auto x-cursor-theme" and all work fine again so far. :D

---

### Post by hellblazer on 2010-11-17
A much better solution than the one I suggested!

You might want to mark this thread as solved so others with the same problem can benefit from your suffering ;)

---

