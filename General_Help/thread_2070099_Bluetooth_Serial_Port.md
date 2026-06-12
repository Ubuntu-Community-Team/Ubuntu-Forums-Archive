---
title: "Bluetooth Serial Port"
date: 2012-10-12
forum: General Help
---

### Post by Commander_Bob on 2012-10-12
I am trying to connect to a bluetooth module I have (this one [https://www.sparkfun.com/products/9358](https://www.sparkfun.com/products/9358)) and I am having some trouble. I am using Ubuntu 12.04 x64.

Ubuntu fails to connect when I try to go though the normal bluetooth interface. It gives me a pin number even when I choose do not pair and I have no way to enter the pin on the device.

However, if I use 
```
sudo rfcomm bind /dev/rfcomm0 00:06:66:04:A5:14

```
and then open the port with minicom then my bluetooth device shows that it has been connected to. Sadly, it does not work still. If I send data to it it does not output the data. 

In Windows I followed this guide ([http://jondontdoit.blogspot.com/2011/11/bluetooth-mate-tutorial.html](http://jondontdoit.blogspot.com/2011/11/bluetooth-mate-tutorial.html)) and it worked perfectly. 

Randomly when working on this too my computer will lock up and I have to restart. It usually happens when I am trying to connect to the device.

Any ideas on what might be going wrong and how I can fix it?

Thanks,
Justin

---

### Post by Commander_Bob on 2012-10-12
I got this to work by installing blueman and using that to set up the serial port. Works like a charm now.

---

### Post by dcstar on 2012-10-12
> **Commander_Bob said:**
> I got this to work by installing blueman and using that to set up the serial port. Works like a charm now.

Thank you for marking your thread. Not only is there now an answer for future forums users but everyone knows that it works.

---

### Post by infirmus on 2012-10-12
Cheers, I was stuffing around for ages with the command line trying to get a BT serial port working in 12.04. This worked first time.

---

