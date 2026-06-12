---
title: "Internet connection fickle with 11.10, fine with 10.04 live CD"
date: 2011-12-24
forum: General Help
---

### Post by blindley on 2011-12-24
I am having trouble connecting to my wireless network with 11.10.   But when I boot up with my 10.04 live CD, everything works just fine.
  Does anybody have a clue what the problem might be?


  What follows is an exposition explaining the things I've done so far:
  I installed Ubuntu 10.04 from a CD about a week ago.  I entered the  password for my network, and connected flawlessly.  I then went through  the process of upgrading to 11.10, one version at a time.  My internet  was still okay for the rest of the day.

Next day I boot up.  I am prompted for my network password.  I enter  it, then wait.  I'm prompted again, and again and again.  After a while I  decide to reboot with my 10.04 disc.  I enter my password, everything  is fine.  I reboot to 11.10, and things are working again, no problems  for the rest of the day.

The same thing happens every single time.  Sometimes I reboot into 11.10 several times.  It never works until I first boot into up 10.04.


**Details about my system:**

  Here is my pci info: [http://www.pasteall.org/27577/text](http://www.pasteall.org/27577/text)

  I assume the Network card is most relevant here:
  01:09.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)   Here's my usb info, though I don't believe there's anything relevant there: [http://www.pasteall.org/27578/text](http://www.pasteall.org/27578/text)

  The following is the results of dmesg with a filter of grep -i network: [http://www.pasteall.org/27579/text](http://www.pasteall.org/27579/text)

  This is udev with the same filter: [http://www.pasteall.org/27580/text](http://www.pasteall.org/27580/text)

  sudo lshw -class network gives: [http://www.pasteall.org/27581/text](http://www.pasteall.org/27581/text)

---

