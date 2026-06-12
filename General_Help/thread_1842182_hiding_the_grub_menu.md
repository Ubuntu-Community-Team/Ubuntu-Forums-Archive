---
title: "hiding the grub menu"
date: 2011-09-10
forum: General Help
---

### Post by hotshot247 on 2011-09-10
i'm dual booting ubuntu and windows 7 and what i was wanting to know is how do i hide the grub menu even though i'm dual booting? my default OS is ubuntu so i just want it to automatically boot ubuntu and not even show the grub menu unless i press the shift key. thanks in advance for the help.

---

### Post by drs305 on 2011-09-10
You can edit the Grub2 files manually by setting the GRUB_TIMEOUT in /etc/default/grub to 0 (and then running 'sudo update-grub') or even better install Grub Customizer and let it set the timeout to 0. 

Grub Customizer can do a lot of Grub2 tweaking. Click the Customizer link in my signature line for more information.

---

### Post by drs305 on 2011-09-10
You can edit the Grub2 files manually and set the GRUB_TIMEOUT in /etc/default/grub to 0 (and then running 'sudo update-grub') or even better install Grub Customizer and let it set the timeout to 0. 

Grub Customizer can do a lot of Grub2 tweaking. Click the Customizer link in my signature line for more information.

---

### Post by hotshot247 on 2011-09-10
if i set the timeout to 0, can i still press the shift key if i want to boot windows 7?

---

### Post by raja.genupula on 2011-09-10
yes by pressing shift key you can get grub menu while booting

---

### Post by hotshot247 on 2011-09-11
i just set the timeout to 0 and when i hold shift to get into the grub menu, it says "Grub Loading..." and then it boots the default OS anyways and skips the grub menu so that's telling me that setting the timeout to 0, it won't even let me see the grub menu because it selects the default OS so fast even by pressing the shift key. do you know any other way i can hide the menu when i'm dual booting?

---

### Post by drs305 on 2011-09-11
What's happened is that the keystatus check hasn't been added to your Grub menu, so it's not checking to see if the SHIFT key is not working.

The easiest 'solution' is to see if pressing ESC repeatedly during boot brings up the menu. If it doesn't, there are a couple of other options. 

One method would be to make the timeout 1 (or more) seconds. That won't significantly increase the boot time and unless you are watching the screen you probably wouldn't see it anyway. If you want to boot another OS you could press any key as the menu appears.

If you *really* don't want to see the menu and the ESC key isn't a desirable option, you can add the keystatus check to your Grub menu. Paste the following below the existing lines in /etc/grub.d/40_custom:

> 
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi

Save the file and run 'sudo update-grub'.  On the next boot see if holding down the SHIFT key during boot brings up the menu.

---

