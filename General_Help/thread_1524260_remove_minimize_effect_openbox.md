---
title: "remove minimize effect openbox"
date: 2010-07-04
forum: General Help
---

### Post by launchy on 2010-07-04
how do i remove the minimize effect in openbox? thanks

---

### Post by urukrama on 2010-07-05
You can remove the iconify/minimize buttons in the Openbox window decorations (the title bar) using obconf: go the Appearance tab and edit the text after the button order. To remove the iconify button remove the I, as explained below the text box.

You can also do this by editing the rc.xml file manually (in ~/.config/openbox/rc.xml): search for the <titleLayout> section (somewhere in the beginning of the file) and edit it like you would in obconf.

In case you want to keep the iconfy button, but just don't want the iconify animation, untick the "Animate iconfy and restore" in the Appearance tab of obconf or change the     <animateIconify>yes</animateIconify> part in your rc.xml to <animateIconify>no</animateIconify>.

---

### Post by launchy on 2010-07-05
thank you!:popcorn:

---

