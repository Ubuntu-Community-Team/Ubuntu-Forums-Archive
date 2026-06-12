---
title: "Guifications - Gaim plugin"
date: 2005-02-10
forum: General Help
---

### Post by audiored on 2005-02-10
I attempted to install Guifications for gaim and it is not working.  I followed the instructions from this thread: [http://ubuntuforums.org/showthread.php?t=9029](http://ubuntuforums.org/showthread.php?t=9029)

i restarted gaim.  even restarted gnome.  yet the plugin doesn't show up in my preferences dialogue.  

guifications.so is in /usr/lib/gaim however.  

thanks.

---

### Post by Goob2k on 2005-02-11
I didn't have luck with the debian package provided.  I used alien to convert the Fedora Core 2 RPM on the Guifications site and then installed it that way.  It worked for some reason.

---

### Post by audiored on 2005-02-11
[QUOTE=Goob2k]I didn't have luck with the debian package provided.  I used alien to convert the Fedora Core 2 RPM on the Guifications site and then installed it that way.  It worked for some reason.[/QUOTE]

could you explain how to do that?  with as much detail as possible.  i'm new to linux.  =)
thanks

---

### Post by rudiz on 2005-02-11
with alien

alien  <packagename>.rpm
dpkg -i <packagename>.deb


PS: or aliens

---

### Post by macewan on 2005-02-11
per subjectdenied

[http://prdownloads.sourceforge.net/guifications/gaim-guifications_2.6-2_i386.deb?download](http://prdownloads.sourceforge.net/guifications/gaim-guifications_2.6-2_i386.deb?download)

sudo dpkg -i gaim-guifications_2.6-2_i386.deb


just tested it and it works fine

---

### Post by Goob2k on 2005-02-11
[QUOTE=rudiz]with alien

alien  <packagename>.rpm
dpkg -i <packagename>.deb


PS: or aliens[/QUOTE]
Or if you're lazy like me, sudo alien -i <packagename>.rpm   :-)

---

### Post by audiored on 2005-02-11
I've tried several different things now.  all the suggestions above and more.  still nothing.  =(  still doesn't show up under plugin on my pref. dialogue box.  

but thanks for the help..

---

### Post by macewan on 2005-02-16
sudo apt-get install gaim-guifications

---

### Post by Deusiah on 2005-03-12
The fedora core 2 RPM works great, thanks :)

---

