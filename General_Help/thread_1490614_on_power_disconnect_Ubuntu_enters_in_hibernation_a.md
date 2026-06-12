---
title: "on power disconnect Ubuntu enters in hibernation and switches of wifi"
date: 2010-05-22
forum: General Help
---

### Post by valugi on 2010-05-22
It only happens since I've upgraded to 10.04. Now everytime that I remove the power plug, no matter that the battery is full, and as well when passing connecting the power back, the laptop (HP pavillion dv 1000) enters in hibernation, it closes the power and the wifi. I have to reinitiate and put again my user password. 

This is truly annoying especially as it changed my existing settings. I dont think an update should do that.

In system/preferences/power management I have the settings to NEVER to close it an to hibernate only when the power is critically low and it seems that these settings are not respected.

Any ideas on how to remove this unwanted behaviour?

Thanks

---

### Post by The Cog on 2010-05-22
I thought that problem only affected the MSI Wind. Oh well, the solution for the Wind is:
Press Ctrl-Alt-F2 and use the pop-up to launch **gconf-editor**. 
Navigate to **Apps / gnome-power-manager / general**. 
**De-select** the option **use_time_for_policy**.

---

### Post by valugi on 2010-05-22
Thanks. It makes a black screen but at least is not entering hibernation anymore.

---

### Post by The Cog on 2010-05-23
You're welcome. But that's slightly different. On the wind, it's a complete fix. The screen dims as it should, and a message says you're now on batteries. 
<rhetorical>
Don't you just wish the manufacturers would stick to the standards?
</rhetorical>

---

