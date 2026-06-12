---
title: "After 11.10 Update USB Mic in Virtualbox Guest stopped working"
date: 2011-10-27
forum: General Help
---

### Post by togakangaroo on 2011-10-27
I have [cross posted this on the virtualbox]("https://forums.virtualbox.org/viewtopic.php?f=7&t=45650&sid=95a9553a8b667f8a204fabf0d6e29204") forums but they're being rather unresponsive so perhaps you guys can help me get started on the issue.

I regularly use LiveMeeting and gotomeeting which do not offer Linux clients so I am consigned to running them inside my Windows VM. Since I upgraded to 11.10 I have been unable to get my headset microphone to work within the virtualbox. No matter what I try, the VM will only use the onboard mic which frankly sucks. A lot. I still get audio to my headset just fine from the VM, it is only the headset mic. Also, this worked just fine before the 11.10 upgrade. The headset mic still works just fine in my Host OS whenever I use Skype.

I have no idea where to even begin with fixing this. Oh Linux gods I beseech you, what to do?


Host OS: Ubuntu 11.10 64 bit installed via wubi
Guest OS: Windows 7 Enterprise 64 bit
Headset: Microsoft LifeChat LX-3000 with a USB connection

---

### Post by Myoldmopar on 2011-11-10
Any chance you've gotten anywhere on this?  I am in the *exact* same boat you are in, same host and guest, but with a logitech usb headset.  I can get audio out to my headset, but the mic doesn't work...and also like you I can talk through the laptop built-in mic.

Thanks, off to continue searching...

---

### Post by togakangaroo on 2011-11-10
Yes (sort of).

First thing that I realized that my Virtualbox Guest Additions were out of sync with my vbox version. Upgrading them was more difficult than usual since the link inside of vbox's self-install apparently pointed at a URL which does not exist. I had to download them manually on the host as an iso file. I can't remember where I found it, I think it was here: [http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

That did not fix the issue though, but it was necessary. I then looked at my virtual machine's settings and under 'USB Devices', 'USB 2.0 controllers' was disabled. I tried to enable it but could not without first installing the extension pack (also available from the link above). This allowed me to enable USB 2.0 and get the microphone working.

Sort of. It doesn't always work. The best that I can tell is that I have to shut down the VM, make sure the headset is plugged in, make sure the headset mic is selected under Ubuntu sound settings, then double check that USB 2.0 Controllers are enabled (they turn off by themselves sometimes), then start the VM.

I *think* it works then.

---

