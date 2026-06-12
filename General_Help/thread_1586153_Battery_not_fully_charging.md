---
title: "Battery not fully charging"
date: 2010-10-01
forum: General Help
---

### Post by dnr1128 on 2010-10-01
I have an IBM Thinkpad T42 running Lucid.  A couple months ago I bought a new battery and it worked fine for a few weeks.  Not it has stopped charging over 65%, and when the AC is plugged in, the battery icon at the top of the screen shows the lightening bolt but it isn't green.  I've gone into the BIOS and reset it to factory defaults, but that hasn't made any difference.  I've run it down almost to when the system shuts itself off, then turned the machine off and let it charge for 10+  hours, but that hasn't made any difference.  

Right now it is plugged in, and the time until fully charged it increasing, from one hour when I plugged the AC in to now over two hours.  

Any ideas if this is a faulty battery or a software issue?

---

### Post by pricetech on 2010-10-01
See if your BIOS has a battery conditioning feature.  Some laptops do.  I'm not sure what your particular system might call it.

---

### Post by psusi on 2010-10-01
Make sure it has plenty of ventilation and if possible, leave it suspended while charging.  If it gets hot, it could stop charging.  Also some laptops have a little battery icon button on the keyboard you can hit to disable charging.

---

### Post by theozzlives on 2010-10-01
Have you looked into the possibility that it could be the power supply on the cord?

---

### Post by psusi on 2010-10-01
> **theozzlives said:**
> Have you looked into the possibility that it could be the power supply on the cord?

If that weren't working then you wouldn't get the icon or ANY charge.

---

### Post by dnr1128 on 2010-10-01
I don't think it's the power supply.  If that were the case it wouldn't work without the battery, and I can remove the battery completely.  

I restored the BIOS  to default settings, and it's still not working.  

Could it be just a bad battery?

---

### Post by psusi on 2010-10-01
It could be, but as I said before there are other causes you should check for.  Also click on the charge icon and look at the detailed statistics.  Specifically what is the current and voltage.

---

### Post by dnr1128 on 2010-10-01
> **psusi said:**
> It could be, but as I said before there are other causes you should check for.  Also click on the charge icon and look at the detailed statistics.  Specifically what is the current and voltage.

When i click on it it just shows how long till charged and preferences.  Where do I find out current and voltage?

---

### Post by arvevans on 2010-10-01
If one of the diodes in your power supply/battery charger is open, then the charger output could drop to approximately half the design voltage.  This may be enough to run your laptop, but not enough to top-off the battery.  Measure the power supply output voltage under load (i.e. while charging a discharged battery) to see if it meets the stated voltage on the side of your charger.

If one of the internal cells in your battery pack is shorted (common with NiCads) the pack will never reach full voltage, and could be over-charging the remaining good cells.  Measure the battery voltage after charging and without load to see if it comes up to approximately 1.2 volts per cell (you will have to determine just how many cells are inside your battery pack).  If the voltage is low after a full charge cycle then you possibly have a shorted cell(s).

If you have modified the BIOS, then the battery voltage reference value may not be correct for your particular battery pack.

---

### Post by dnr1128 on 2010-10-01
> **arvevans said:**
> If one of the diodes in your power supply/battery charger is open, then the charger output could drop to approximately half the design voltage.  This may be enough to run your laptop, but not enough to top-off the battery.  Measure the power supply output voltage under load (i.e. while charging a discharged battery) to see if it meets the stated voltage on the side of your charger.

If one of the internal cells in your battery pack is shorted (common with NiCads) the pack will never reach full voltage, and could be over-charging the remaining good cells.  Measure the battery voltage after charging and without load to see if it comes up to approximately 1.2 volts per cell (you will have to determine just how many cells are inside your battery pack).  If the voltage is low after a full charge cycle then you possibly have a shorted cell(s).

If you have modified the BIOS, then the battery voltage reference value may not be correct for your particular battery pack.

How do I measure the output while under load?

---

### Post by psusi on 2010-10-01
> **dnr1128 said:**
> When i click on it it just shows how long till charged and preferences.  Where do I find out current and voltage?

That is what you see when you hover the cursor over it.  Click on the icon ( might have been right click ).

> **arvevans said:**
> If one of the diodes in your power supply/battery charger is open, then the charger output could drop to approximately half the design voltage.  This may be enough to run your laptop, but not enough to top-off the battery.  Measure the power supply output voltage under load (i.e. while charging a discharged battery) to see if it meets the stated voltage on the side of your charger.

That could happen if the power supply is just a step down transformer and rectifier bridge, but they haven't made them like that in years.  Modern switching supplies are either working correctly, or not, they can't really get in between.

> **arvevans said:**
> If one of the internal cells in your battery pack is shorted (common with NiCads) the pack will never reach full voltage, and could be over-charging the remaining good cells.  Measure the battery voltage after charging and without load to see if it comes up to approximately 1.2 volts per cell (you will have to determine just how many cells are inside your battery pack).  If the voltage is low after a full charge cycle then you possibly have a shorted cell(s).


Generally when you have a bad cell the pack as a whole does end up reaching full voltage by over charging an individual cell.  Modern packs have protection circuits that detect this and open the circuit.  Also nicads haven't been used in years either.  Modern packs use lithium ion with a voltage around 4.2 volts per cell when charged.

---

### Post by dnr1128 on 2010-10-02
I put in my older battery (the one that I bought the new one to replace cause it says full charge but drains in about an hour under normal load) and it is showing 95% charging and 39.3% capacity.  What is the difference between the two?

If I stick in the new(er) battery, it shows 63.8% charged and 95.5% capacity.  Time to full and time to empty are both on zero.

---

