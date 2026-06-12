---
title: "Update Manager help please!"
date: 2010-03-03
forum: General Help
---

### Post by Eberbachl on 2010-03-03
Hi Everyone,

When I run update manager it returns the following error:

```
E: bsd-mailx: subprocess installed post-installation script returned error exit status 2
E: gettext: subprocess installed post-installation script returned error exit status 2
E: html2text: subprocess installed post-installation script returned error exit status 2
E: libqt3-mt: subprocess installed post-installation script returned error exit status 2
E: libqt4-assistant: subprocess installed post-installation script returned error exit status 2
E: libqt4-gui: dependency problems - leaving unconfigured
E: librpmio0: subprocess installed post-installation script returned error exit status 2
E: librpm0: dependency problems - leaving unconfigured
E: librpmbuild0: dependency problems - leaving unconfigured
E: mailx: dependency problems - leaving unconfigured
E: rpm: dependency problems - leaving unconfigured
E: intltool-debian: dependency problems - leaving unconfigured
E: po-debconf: dependency problems - leaving unconfigured
E: debhelper: dependency problems - leaving unconfigured
E: alien: dependency problems - leaving unconfigured
E: lsb-core: dependency problems - leaving unconfigured

```

Please help...does anyone have any ideas?

Thanks,

Luke.

---

### Post by rgrig on 2010-03-03
Does synaptic work?
If so, try edit->fix broken packages.

---

### Post by Eberbachl on 2010-03-08
Hi rgrig,

Thanks for the suggestion. I've tried that but sadly it doesn't help.

The above problem's still there. Does anyone else have any suggestions?

Thanks,

;)

---

### Post by bumanie on 2010-03-08
Try > sudo apt-get update && sudo apt-get upgrade in terminal. If that doesn't work try > sudo apt-get install --fix-missing

---

### Post by Eberbachl on 2010-03-09
Thanks very much for the suggestion bumanie.

I tried running those commands, and it's still returning the same error.

Any other suggestions?

:D

---

