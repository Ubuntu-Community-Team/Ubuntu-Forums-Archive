---
title: "Firefox edge of image artefacts"
date: 2011-02-13
forum: General Help
---

### Post by imbjr on 2011-02-13
The attachment shows little black artefacts around the edges of some images.

I don't often see this, but have done since installing Meerkat.

If you visit:

[http://www.texasbeyondhistory.net/kincaid/images/artifacts.jpg](http://www.texasbeyondhistory.net/kincaid/images/artifacts.jpg)

you will see that the first image certainly does not have any black broken edges.

If I step away from the page and return to it, the artefacts does not always disappear.

I've got an ATI X1300 card that I've had to switch modesetting off for, otherwise starting wine apps or totem will cause the screen to flash black briefly.

Any ideas?

---

### Post by anagor_lv on 2011-02-22
Let me try to handle your problem.

I suppose it is not a graphic card issue. Graphic card issues usually affect the screen as a whole, e.g. lines extending over the screen.

I am not sure, but it looks like a software problem, most probably, with your browser. One of the software components or libraries may be outdated or slightly corrupted.

What browser are you using? What plugins and extensions do you have in your browser? Does a similar problem occur in any other application?

I have a couple of ideas. They might or might not help, but they are unlikely to damage your system. Nevertheless, it is always better to backup your important documents.

One thing you can try is upgrade all system packages. If one of them is corrupted, chances are it will be replaced by a newer version. Open the Terminal and issue this command:

```
sudo apt-get update && sudo apt-get upgrade
```

It will take time to upgrade all packages.

If this does not help, try uninstalling your browser and installing it again.
In Ubuntu 10.10, go to Ubuntu Software Center, select "Internet", then "World Wide Web", and find your browser in the list. Select it and click "Remove". After all is completed, select it again and click "Install"

If it does not solve your problem, write about it!

If your problem is solved, mark the thread as solved!

---

