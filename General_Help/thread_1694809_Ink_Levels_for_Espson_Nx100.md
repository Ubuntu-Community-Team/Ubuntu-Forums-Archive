---
title: "Ink Levels for Espson Nx100"
date: 2011-02-24
forum: General Help
---

### Post by Bangulo on 2011-02-24
***I was wondering if there is any kind of tool that i could use to check the ink levels in the printer. It is blinking that one of the carts is out but there is 4 in this printer. Its a pain in the **** having to hook it up and install it to a windows computer just so i can see what cart i need to replace. I went to System>Administration>Printing***> ***Right clicked on the printer then went to Properties>Ink/toner levels> In the box it says ***"Marker levels are not reported for this printer" ***Hmm so basically i shouldn't use this printer? ***

[I][B]Thanks for anyone who helps
Bangulo
[/B][/I]

---

### Post by anglican on 2011-02-25
> **Bangulo said:**
> ***I was wondering if there is any kind of tool that i could use to check the ink levels in the printer. It is blinking that one of the carts is out but there is 4 in this printer. Its a pain in the **** having to hook it up and install it to a windows computer just so i can see what cart i need to replace. I went to System>Administration>Printing***> ***Right clicked on the printer then went to Properties>Ink/toner levels> In the box it says ***"Marker levels are not reported for this printer" ***Hmm so basically i shouldn't use this printer? ***

[I][B]Thanks for anyone who helps
Bangulo
[/B][/I]Try:
```
sudo apt-get install escputil
sudo escputil -i -r /dev/usb/lp0
```obviously, if your printer is attached somewhere other than /dev/usb/lp0 then use that instead. There is also mtink (also in the repos) but I don't think that works for an NX100 (it probably can be added but that may be complicated).

H

---

### Post by Bangulo on 2011-02-28
> **anglican said:**
> Try:
```
sudo apt-get install escputil
sudo escputil -i -r /dev/usb/lp0
```obviously, if your printer is attached somewhere other than /dev/usb/lp0 then use that instead. There is also mtink (also in the repos) but I don't think that works for an NX100 (it probably can be added but that may be complicated).

H


You're amazing Thank you very much.

---

