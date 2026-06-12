---
title: "SDCard there but not there?"
date: 2010-03-22
forum: General Help
---

### Post by chris.willis on 2010-03-22
Hi there, I don't know how to explain this correctly but let's try!

I have an Acer Aspire One and permanently have a SDHC card in to make frequent backups. It used to be the other way around, which I prefer because my files go from computer to computer.

I've recently installed Kubuntu and when I try access the SD Card, it says it isn't there, but if I click the "Recent Devices" widget, it is there. So when I click 'Sandisk', it appears, and only then can I access the files.

ie, let's say I just rebooted. I have Notes.odt on Sandisk drive and go into OpenOffice to open. Sandisk does not exist. If I go into Dolphin or "Recent Devices" and click on Sandisk, I can then go back to OpenOffice and open the document. If I want to re-access that document or any other document on Sandisk, there's no problem. If I reboot, the problem's there again!

Any idea how I can access Sandisk files without going through the above procedure?

---

### Post by Pirolocito on 2010-03-22
I had a similar trouble.

Try this:

Stop udev:

sudo stop udev

Start udev again:

sudo start udev

After a while that should work...

See more about udev
[http://en.wikipedia.org/wiki/Udev]("http://en.wikipedia.org/wiki/Udev")

Linux is easy....

---

### Post by chris.willis on 2010-03-25
No, it doesn't kick in when I boot up again.

---

### Post by chris.willis on 2010-04-16
Any other ideas?

---

