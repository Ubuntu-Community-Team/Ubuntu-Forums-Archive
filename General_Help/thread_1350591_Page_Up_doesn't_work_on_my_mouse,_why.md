---
title: "Page Up doesn't work on my mouse, why?"
date: 2009-12-09
forum: General Help
---

### Post by expxe on 2009-12-09
i followed this guide 

[http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/howto_logitech_mx_revolution_on_ubuntu#button_assignments_for_the_mx_revolution](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/howto_logitech_mx_revolution_on_ubuntu#button_assignments_for_the_mx_revolution)

and here is what is written when i type gedit ~/.xbindkeysrc in terminal



> #Thumb Scroll Wheel Press Down
"/usr/bin/xte 'key F5' &"
  b:17

#Thumb Scroll Wheel Press Forward
"/usr/bin/xte 'key Page Up' &"
#"firefox &"
  b:13

#Thumb Scroll Wheel Press Back
"/usr/bin/xte 'key Page Down' &"
  b:15
 

now page up doesn't work, when i thrumb press forward it doesn't go page down, the button is fine because if i uncomment the firefox entry and try again the thumb press forward will open firefox. so how can i get page up on my mouse?

---

### Post by expxe on 2009-12-09
ok, now none of the customized buttons work except for the thumb press down

---

### Post by expxe on 2009-12-09
no replies? this should be an easy problem to solve right?

---

### Post by expxe on 2009-12-09
ok, i think it might be because 'page up' and 'page down' are not the correct ways to register the button to the mouse. what should i enter in their place? is there a list of keys? im also interested in the home and end keys

---

### Post by expxe on 2009-12-09
keycode 110/115/112/117 are for home/end/pageup/pagedown

how can i map this to my mouse?

---

