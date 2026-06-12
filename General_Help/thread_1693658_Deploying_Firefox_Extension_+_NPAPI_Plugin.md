---
title: "Deploying Firefox Extension + NPAPI Plugin"
date: 2011-02-23
forum: General Help
---

### Post by o.martin on 2011-02-23
Hello guys,

I have to install on debian / ubuntu distributions a firefox extension (*.xpi) and a npapi plugin (*.so).  I wrote a *.deb Package that install both of them. 
Normaly i install the extension in /usr/lib/firefox-addons/extensions/{CLISD}/<folders> and the npapi plugin in /usr/lib/mozilla/plugins (so that chrome load the plugin too). 

This works fine for the appropiate default browser on each distribution. But when i download a firefox version from the mozilla homepage and untar it to any folder, only the plugin will be loaded and NOT my extension. If i deploy my XPI via "firefox -install-global-extension /path/to/extension.xpi"  my downloaded firefox will not load this extension too, so this command was useless in my case.

i don't know how i can deploy this XPI extension so that all firefox versions will load this extension.

On Windows it was simple, firefox look for registry keys which reference to a extenions (xpi), but on debian/ubuntu i have no idea, anyone know how i can solve my problem.

Best regards,
martin

---

