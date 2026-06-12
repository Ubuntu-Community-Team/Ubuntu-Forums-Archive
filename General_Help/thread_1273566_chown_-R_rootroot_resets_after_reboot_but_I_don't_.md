---
title: "chown -R root:root resets after reboot but I don't want it to!"
date: 2009-09-23
forum: General Help
---

### Post by drewsus on 2009-09-23
Hello,
So, I am trying to make a custom distro using Remastersys and have been following this guide: 

[http://crunchbanglinux.org/forums/topic/2859/remastersys-guide-create-your-own-ubuntubased-distro/](http://crunchbanglinux.org/forums/topic/2859/remastersys-guide-create-your-own-ubuntubased-distro/)

Everything goes well and I have virtually no problems except for Themes. 
I want my themes to be available on the live CD as well as when the installation is complete. 
I have copied all my themes to /usr/share/themes and they are there  when I boot from the live CD, but they do not show up in Appearances.
so, I attempted to chown -R root:root on the usr/share/themes folder and all went well. The ownerships were changed to that of what I needed (what the other themes are that show up in the Live CD) but when I make a new live CD or reboot my system the permissions are returned to what they were before chown -R root:root and as such when I make a new distro Live CD they don't show up in Appearances!
And, fyi, I put my wallpapers in /usr/share/backgrounds and they show up fine on the live CD. 
So, does anyone have any suggestions or help with this issue I am having?! 
Thanks in advance,
dRewsus

ps- I am using Ubuntu Jaunty on my Acer Aspire One

---

### Post by drewsus on 2009-09-24
anyone have any suggestions?

---

