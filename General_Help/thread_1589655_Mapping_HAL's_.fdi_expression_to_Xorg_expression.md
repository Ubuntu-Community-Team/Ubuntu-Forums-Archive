---
title: "Mapping HAL's .fdi expression to Xorg expression"
date: 2010-10-06
forum: General Help
---

### Post by zefew on 2010-10-06
I want to translate this .fdi clause

> <match key="info.product" string="PS/2 Generic Mouse">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
 <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
 <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
</match> 


into its Xorg equivalent. What does it look like?

---

### Post by zefew on 2010-10-06
Never mind. I solved it myself before you guys could respond.

---

