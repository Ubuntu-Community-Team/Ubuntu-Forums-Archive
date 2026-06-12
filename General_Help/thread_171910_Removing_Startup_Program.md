---
title: "Removing Startup Program"
date: 2006-05-07
forum: General Help
---

### Post by theshibboleth on 2006-05-07
I followed the instructions at [http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/) for setting up scim as a startup program:

sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup

However, I've now decided that I don't want to launch scim at startup because it launches with every program and makes it impossible for some to run. How do I undo that terminal input?

---

### Post by Ramses de Norre on 2006-05-07
I'm pretty sure you can just do sudo rm /etc/X11/Xsession.d/74custom-scim_startup

---

### Post by theshibboleth on 2006-05-07
[QUOTE=Ramses de Norre]I'm pretty sure you can just do sudo rm /etc/X11/Xsession.d/74custom-scim_startup[/QUOTE]

That didn't do it. The file's no longer there, but scim still launches at startup. I suppose it could be some startup feature in scim independent of what I did.

---

