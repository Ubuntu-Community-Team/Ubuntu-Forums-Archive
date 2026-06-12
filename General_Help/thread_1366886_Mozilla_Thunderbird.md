---
title: "Mozilla Thunderbird?"
date: 2009-12-28
forum: General Help
---

### Post by Cityscape on 2009-12-28
How do I install the latest version of Mozilla Thunderbird (3) on Ubuntu 9.04?

The mozilla website only has a .tar file avaiable for download ([http://www.mozillamessaging.com/en-US/thunderbird/](http://www.mozillamessaging.com/en-US/thunderbird/)) and Synaptic only has version 2.

---

### Post by The Secret on 2009-12-28
Move the folder ( thunderbird ) to the /opt directory and create a symlink for the launcher. Nothing really needs to be installed or compiled.

---

### Post by Cityscape on 2009-12-28
> **The Secret said:**
> Move the folder ( thunderbird ) to the /opt directory and create a symlink for the launcher. Nothing really needs to be installed or compiled.
I haven't been using Linux very long at all. I don't really understand what you mean.

---

### Post by The Secret on 2009-12-28
```
sudo mv thunderbird /opt && sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird

```

---

