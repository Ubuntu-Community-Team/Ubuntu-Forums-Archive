---
title: "Fn key + Super key no longer works"
date: 2010-11-30
forum: General Help
---

### Post by myk02k on 2010-11-30
Hey guys. Long story short, I thought my Super key was not working to dim my notebook screen, thinking that it was a driver problem. However, I also noticed that my Super key no longer works. I read somewhere that in order to fix the Super key, you would have to use Keyboard Preferences and change 'Alt/Win Behavior' so that 'Super is mapped to Win-Keys'. There is no option like this for me to select. Moreover, this will not fix my function key issue and my eyes are beginning to strain from my screen being at max brightness all the time. Any solutions to this odd problem?

---

### Post by myk02k on 2010-11-30
xev does not recognize the key presses & dmesg is not picking up any errors. Both keys work just fine when I boot Windows 7.  ](*,)

---

### Post by myk02k on 2010-12-01
Problem solved. Another thread recommended adding "acpi_osi=Linux" in the grub cfg for Toshiba's A505 laptops. Once I removed that option, my super & FN keys came back. Just posting to let anyone else know if they run into a the same issue.

---

