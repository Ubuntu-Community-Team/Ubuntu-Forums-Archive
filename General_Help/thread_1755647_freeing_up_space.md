---
title: "freeing up space"
date: 2011-05-11
forum: General Help
---

### Post by vikceo on 2011-05-11
hi i used a 4gb usb to install ubuntu and kept on running it from usb from months. I used to upgrade or install new packages every day. finally today it shows no space left on device. I am unable to run package manager etc as it shows broken index error.

I do not have any personal data as well on this usb. So how do i free up some space?

---

### Post by snowpine on 2011-05-11
According to the [Ubuntu System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements"), the "recommended minimum" hard drive space is 8gb.

That being said, you can try freeing up space with the following commands:

```
sudo apt-get clean
sudo apt-get autoremove
```

This will remove cached packages and packages that are no longer needed to satisfy dependencies.

---

