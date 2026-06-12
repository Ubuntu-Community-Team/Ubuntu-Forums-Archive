---
title: "query ATI drivers for info"
date: 2012-02-07
forum: General Help
---

### Post by gamblor01 on 2012-02-07
I'm migrating from a desktop to a laptop at work.  I installed Ubuntu and have been getting everything setup, but one thing that isn't complete is my conky setup.  My desktop system has an nvidia card in it, but the laptop is (unfortunately) an ATI card.

With the nvidia drivers you can use nvidia-settings to retrieve information.  For example, I can monitor the current GPU temperature like this:

```

nvidia-settings -q gpucoretemp |grep '):' | cut -d ' ' -f 6,6 | sed -e 's/.\{1\}$//'

```

Is there any sort of command line equivalent for ATI drivers?

---

