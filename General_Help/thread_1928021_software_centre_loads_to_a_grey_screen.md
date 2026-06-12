---
title: "software centre loads to a grey screen?"
date: 2012-02-19
forum: General Help
---

### Post by ELD on 2012-02-19
Any idea why software centre loads to a grey screen?

How can i go about re-installing it?

---

### Post by jingaling on 2012-02-19
Go into terminal and type the following command:

```
sudo apt-get remove software-center
```

reboot then in terminal again run:

```
sudo apt-get install software-center
```

Reboot again and the Ubuntu Software Centre will have bee re-installed. See if you can run the software centre. Hope this helps.

Kev

---

### Post by ELD on 2012-02-19
Thanks it works now, but i seem to have two SC launchers in my unity apps?

---

