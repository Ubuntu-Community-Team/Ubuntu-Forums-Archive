---
title: "cannot remove package"
date: 2009-10-05
forum: General Help
---

### Post by bvidinli on 2009-10-05
problem was:
<code>
# dpkg --remove --force-all adobe-flashplugin
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 200274 files and directories currently installed.)
adobe-flashplugin kald&#305;r&#305;l&#305;yor ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 installed pre-removal script alt i&#351;lemi ç&#305;k&#305;&#351; durumunda hata döndürdü : 2
postinst called with argument `abort-remove'
dpkg: temizleme esnas&#305;nda hata olu&#351;tu:
 installed post-installation script alt i&#351;lemi ç&#305;k&#305;&#351; durumunda hata döndürdü : 1
Errors were encountered while processing:
 adobe-flashplugin

</code>

solution: (really bad but working solution, i found no else.. )
<code>

rm /var/lib/dpkg/info/adobe-flashplugin.prerm
</code>

I found that solution in: 
[https://lists.ubuntu.com/archives/ubuntu-users/2007-January/103602.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-January/103602.html)

---

