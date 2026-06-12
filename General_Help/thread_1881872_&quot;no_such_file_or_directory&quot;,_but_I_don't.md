---
title: "&quot;no such file or directory&quot;, but I don't want it anyway"
date: 2011-11-16
forum: General Help
---

### Post by TZed on 2011-11-16
Hi all,

I'm new to Ubuntu, so any help will be much appreciated! I recently installed 32-bit Ubuntu  10.04 beside 64-bit 10.04 (because I installed 64-bit, but actually needed 32-bit for a project and didn't realize for a while). I kept the 64-bit around in case something went awry. I followed the instructions [here]("http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/")[]("http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/").

However, I now get this line every time I start terminal:
bash: /opt/ros/electric/setup.bash: No such file or directory

The easy fix, I think, would be to grab that folder from the other partition and put it in opt/, right? However, I do not want nor need ros anymore, so is there a line or a setting I can change so bash stops looking for this file at startup?

Thanks!

---

### Post by dethorpe on 2011-11-16
Thats probably just being called from your .bashrc file (in your home dir). You can just edit it and remove the line.

---

### Post by MG&amp;TL on 2011-11-16
```
gedit ~/.bashrc
```

Then look for /opt lines. Just to clarify.

---

### Post by TZed on 2011-11-16
Thanks for the reply. Unfortunately, I didn't find anything specifically reting to opt. I did find "shopt", though. Is that equivalent?

---

### Post by MG&amp;TL on 2011-11-17
Can you post your .bashrc, obviously removing anything sensitive?

---

