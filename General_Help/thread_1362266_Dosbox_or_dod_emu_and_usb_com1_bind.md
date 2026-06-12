---
title: "Dosbox or dod emu and usb com1 bind?"
date: 2009-12-22
forum: General Help
---

### Post by brettybaby on 2009-12-22
can I use a com1 usb port with a dos program in  linux?

Do I need to bind com1 or usb to the dosbox?

does anyone know?

---

### Post by rCXer on 2009-12-23
Which program are you trying to run? Are you trying to use a mouse with a COM connector?

---

### Post by brettybaby on 2009-12-26
i found this

[directserial]
# directserial -- Enable serial passthrough support.
# comport -- COM Port inside DOSBox.
# realport -- COM Port on the Host.
# defaultbps -- Default BPS.
# parity -- Parity of the packets. This can be N, E or O.
# bytesize -- Size of each packet. This can be 5 or 8.
# stopbit -- The number of stopbits. This can be 1 or 2.

directserial=false
comport=1
realport=COM1
defaultbps=1200
parity=N
bytesize=8
stopbit=1

---

