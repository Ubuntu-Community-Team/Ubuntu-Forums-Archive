---
title: "Battery Issue"
date: 2010-01-12
forum: General Help
---

### Post by brandon_h on 2010-01-12
I bought a new battery the other day. i let it fully charge then fully discharge. Since then it hasn't fully charged again, until today

i get this

Product: Laptop battery
Status: Charged
Percentage charge: 0.9%
Vendor: D1520L
Technology: Lithium Ion
Serial number: 24405
Model: DELL 00
Capacity: 100.0% (Excellent)
Current charge: 0.4 Wh
Last full charge: 50.6 Wh
Design charge: 48.8 Wh
Charge rate: 0.0 W


Its saying its fully charged at .9%
any idea how i fix that?

---

### Post by warfacegod on 2010-01-12
First guess, defective battery.

---

### Post by brandon_h on 2010-01-13
Hope thats not the case. Any other ideas?

---

### Post by warfacegod on 2010-01-13
With the battery installed, try this:

```
sudo apt-get purge gnome-power-manager

sudo apt-get install gnome-power-manager
```

---

### Post by brandon_h on 2010-01-14
Thanks for the suggestion but that didn't work either.

---

### Post by warfacegod on 2010-01-14
Is it the same model as your old battery? Is your old battery being read the same way?

---

### Post by brandon_h on 2010-01-14
Old battery went bad. The battery indicator flashed orange continuously. Before that, it eventually got worse and worse till it would only hold a charge for a few minutes.

This battery worked fine for the first charge, or appeared so. 

But i contacted the place i bought it from today. I'm going to send it in and they'll replace it. If  it happens again I'll just return it and buy from Dell.

---

### Post by warfacegod on 2010-01-14
I hope everything works out.

---

### Post by garryknight on 2010-01-14
> **brandon_h said:**
> i let it fully charge then fully discharge. 
...
Technology: Lithium Ion


Not a good idea to fully discharge a LiIon battery.

---

### Post by mister_playboy on 2010-01-14
> **garryknight said:**
> Not a good idea to fully discharge a LiIon battery.

Software should prevent the battery from being discharged too much (<30-35% total charge remaining for LiIon, believe).  It's not actually empty when the software is saying it's empty.  This is assuming he was discharging it by running his laptop and not by trying to jump his car or something... :)

---

### Post by brandon_h on 2010-01-14
I just brought computer into my bedroom and hooked it up to the old AC adapter that came with my computer. its a little worse for wear so i quit carrying with it, just leave it in here. 

But now my battery is starting to charge. its up to 11.5%

I don't understand. Both A/C adapters are the same. 
input 100-240V~
50/60HZ
otuput 19.5V

---

### Post by warfacegod on 2010-01-14
Are the amps the same?

---

