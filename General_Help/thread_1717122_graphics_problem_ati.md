---
title: "graphics problem ati"
date: 2011-03-29
forum: General Help
---

### Post by comeback-of-the-year on 2011-03-29
Hey everyone. I recently tried fixing my desktops graphic driver. It was using the the proprietary -fglrx and use the open source ati one instead. This is for my radeon HD 5450. It was only because with the proprietary driver things like compiz and docky wouldn't work.  

I followed all the instructions on the ubuntu support site but now I cannot boot into my desktop. I get the purple loading screen but then no signal. 

I can however use recovery mode to boot into netroot, so I have some control. 

Anyone know how to fix this issue?

---

### Post by coffeecat on 2011-03-29
I'm not quite clear where you are. It sounds as thought the open source driver was OK but the proprietary fglrx was not. Is the situation that  you tried to uninstall the fglrx driver and now the system will not boot to a GUI? If this is so, it may be because the fglrx driver does not always uninstall properly.

Have a look here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

If you can boot into the recovery console and choose drop to root shell with networking you can run those commands, but you don't need sudo. I suggest you try the full "Problem:  Need to fully remove -fglrx and reinstall -ati from scratch" option.

---

### Post by comeback-of-the-year on 2011-03-29
They were the instructions I originally used. I just reinstalled fglrx (apt-get install fglrx) from the shell and everything seems to be working fine now. I've got compiz and docky running, all going smooth. 

The only niggle I have with it now is the loading screen. The purple screen that displays "ubuntu" and the loading dots, is now pixely and out of proportion.

This isn't a problem as long as it isn't going to affect day to day running of the system. Thanks for the advice coffeecat.

---

