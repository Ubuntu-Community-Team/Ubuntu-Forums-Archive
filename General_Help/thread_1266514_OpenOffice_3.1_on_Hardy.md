---
title: "OpenOffice 3.1 on Hardy?"
date: 2009-09-14
forum: General Help
---

### Post by geoffree on 2009-09-14
Can I install and run Open Office 3.1 on Hardy 8.04?  How?

Thank you

Geoffrey

---

### Post by hal10000 on 2009-09-14
Put the OpenOffice repository into your /etc/apt/sources.list:

```

sudo -s
echo "deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main" | cat >>/etc/apt/sources.list
gpg --keyserver subkeys.pgp.net --recv 247D1CFF && gpg --export --armor 247D1CFF | apt-key add
apt-get update
exit

```

Then open your package-manager (synaptic) and upgrade your openoffice.org package.

Don't wonder if you start your new openoffice 3.1 and you get a somehow "damaged" entry-screen and missing toolbar-icons; then you just have to (re)install your [COLOR="Red"]openoffice.org-style packages[/COLOR]. There are several style-packages from which you should choose the ones you like.

Have fun

---

