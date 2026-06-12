---
title: "resolution tiny after restart"
date: 2010-11-23
forum: General Help
---

### Post by a546 on 2010-11-23
So, i just restarted because of some problems and as i booted, the ubuntu logo with the load thing was looking different and errors appeared under the logo. The resolution is 1024x786, but it was way higher before. When i click on System/Preferences/Monitors it says "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead? y/n"
How can i get my graphic card working again?
I have a broken package: sun-java6-jre, is it because of that?

---

### Post by theSuperman on 2010-11-23
My laptop says that because I have proprietary graphics drivers installed. What happens if you run xrandr in the terminal?

---

### Post by Frogs Hair on 2010-11-23
When asked to use the vendors tool select yes and it will take to Nvidia X server settings or the ATI counterpart. which should appear on the administration menu. From there you can make and save settings , proprietary drivers will change the appearance of the splash screen.

---

