---
title: "How to deactivate logging entirely?"
date: 2012-06-11
forum: General Help
---

### Post by codell on 2012-06-11
How can I turn off all logs?

I really need this, I am about to upload an image and it should not contain information about my machine.

---

### Post by dargaud on 2012-06-11
Images created on your computer shoudn't contain info about your computer, unless you plaied with the exif fields to add info. Some cameras or graphic software do that, but unless you specifically configured it so, it's unlikely to happen.
Now the web _server_ gets info about your browser when you connect to upload the image, but it's not contained in the image. It contains info such as which browser you use, which language, which OS, etc... [More info here](http://whatsmyuseragent.com/)

---

### Post by codell on 2012-06-11
Image = hdd image.

For example /var/log/kern.log or /var/lib/dhcp/ contains lots of information.

---

