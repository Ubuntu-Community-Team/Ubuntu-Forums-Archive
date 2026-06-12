---
title: "Disable F Lock"
date: 2006-06-11
forum: General Help
---

### Post by funnyguyfunnyguy on 2006-06-11
I found this page [http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix](http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix) which details how to disable F Lock using a script. I created the script "/usr/bin/f_lock_fix," ran "sudo chmod 755 /usr/bin/f_lock_fix" to give it the correct permissions, and then added the script to System -> Preferences -> Sessions -> Startup, yet it does not solve my problem. Any ideas?

Any help would be appreciated

---

### Post by Apple 101 on 2006-06-11
Run this command to make f_lock_fix run when you login to X:
echo 'f_lock_fix' >> ~/.xinitrc

---

### Post by funnyguyfunnyguy on 2006-06-11
Tried that by typing it into the terminal. No errors, but still doesn't work on restart. Any other ideas?

---

### Post by Apple 101 on 2006-06-11
I'm just trying out a possible fix...

---

