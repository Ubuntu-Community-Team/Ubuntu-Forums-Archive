---
title: "Broke Update Manager"
date: 2009-10-11
forum: General Help
---

### Post by slackadjuster on 2009-10-11
Help with update manager. I was updating Ubuntu 9.10 beta and all was going good. I went to another work space and started working on something else and the screen went black. The only thing I could do was manually shut down and restart computer in the middle of updating. After restart I went back to update manager but now it wont show up after I click in the System-Administrator-Update Manager. None of the programs in System-Administrator will open now. 

Thanks for any help.

---

### Post by misfitpierce on 2009-10-11
Did you try restarting computer? Something may have crashed that you need to run those. Try a restart if you have not.

---

### Post by Geoff918 on 2009-10-11
I believe you may be interested in trying the following from the CLI:

dpkg -a (run as sudo)

I am pretty sure that command will fix any install issue. I might be forgetting a switch in there, but I believe that's it.

---

