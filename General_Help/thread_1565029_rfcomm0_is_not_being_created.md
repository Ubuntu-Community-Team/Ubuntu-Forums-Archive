---
title: "rfcomm0 is not being created"
date: 2010-08-31
forum: General Help
---

### Post by illingd on 2010-08-31
I have the "EasyPeasy" version of Ubuntu on my Acer Aspire One - I believe this is basically UNR 10.04

I want to use my mobile phone as a modem via bluetooth. I managed to get it working, BUT ...

I have to manually create /dev/rfcomm0 every time, using "sudo rfcomm bind 0"

Can anyone suggest why this is necessary? Shouldn't the device be created automatically on boot-up, once /etc/bluetooth/rfcomm.conf has been set up?

---

