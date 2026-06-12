---
title: "Lubuntu wireless networks firmware missing"
date: 2011-06-02
forum: General Help
---

### Post by coolbuntukid on 2011-06-02
I'm posting from my thinkpad with windows 7 now which is connected to wifi. 

I installed lubuntu 11.04 on my old dell but I can't connect to the internet on it. I went to additional drivers to download the missing firmware but the irony of it is that you can't download the drivers if you aren't online. I plugged the ethernet cable on the back of the dell but it won't accept wired connections either so I don't know what to do. 

can I download the missing firmware on my thinkpad, put it on a usb stick, and then transfer it to my dell and install it there?  where can I download the missing firmware?  I googled so much but still can't find it.

---

### Post by kerry_s on 2011-06-02
you don't even say what the firmware is.
we need the name to point you to it.
yes, you can grab the deb & double click on it, gdebi will do the rest.

---

### Post by coolbuntukid on 2011-06-02
> **kerry_s said:**
> you don't even say what the firmware is.
we need the name to point you to it.
yes, you can grab the deb & double click on it, gdebi will do the rest.

I don't know what firmware. All it says is "wireless firmware missing" :(

---

### Post by coolbuntukid on 2011-06-02
bump

---

### Post by kerry_s on 2011-06-02
> **coolbuntukid said:**
> I don't know what firmware. All it says is "wireless firmware missing" :(

it don't say in "additional drivers", there should be something there.

---

### Post by cavalier911 on 2011-06-03
This will identify the adapter so I can advise you on firmware.
Post output of this command in terminal:
_Internal wireless: _
```
lspci -nn | grep -i net
```
_USB wireless:_
```
lsusb
```
Post output of **lsmod** between code tags.

---

### Post by dFlyer on 2011-06-03
Post some information on your system. Dell wireless just doesn't help much. they this command using the terminal lspci and post your output.

---

