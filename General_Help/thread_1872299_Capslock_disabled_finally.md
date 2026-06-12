---
title: "Capslock disabled finally"
date: 2011-10-30
forum: General Help
---

### Post by mike555 on 2011-10-30
To stop CapsLock in Xubuntu   11.10   (changing it to Shift without lock)

   open leafpad , put in;

      !
! Swap Caps_Lock and Shift_L
!
remove Lock = Caps_Lock
keysym Caps_Lock = Shift_L


 then save as "   .nocaps   " in your home folder (notice the dot)   then open Settings Manager and  then Sessions and startup, Application Autostart tab, click add ,  name it "nocaps " or what ever you want, then in Command box type ;  
    "  xmodmap /home/mike/.nocaps  " without the quote marks  (changing mike for your user name) make sure your new startup is checked and log out and back in ..........

---

