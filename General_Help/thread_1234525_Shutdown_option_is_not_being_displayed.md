---
title: "Shutdown option is not being displayed"
date: 2009-08-08
forum: General Help
---

### Post by atmjeet on 2009-08-08
When I press the power button all options like log out, switch user, hibernate etc are showing except the shutdown option. Even when I try to logout and then look for this option i see only things like change session. Can anyone provide a solution?
thanks
adam

---

### Post by rudihawk on 2009-08-08
If you need to shutdown and that option is not there you can try:

```
sudo poweroff -n
``` Which will turn off your PC. The poweroff is the command for Ubuntu to shutdown and the -n specifies when it must occur, i.e in this case "now".

Hope you can find a solution to your problem!

---

