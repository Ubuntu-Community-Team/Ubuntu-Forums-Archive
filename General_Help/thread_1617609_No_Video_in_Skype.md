---
title: "No Video in Skype"
date: 2010-11-09
forum: General Help
---

### Post by kernelles on 2010-11-09
I can't get video to work in Skype on Maverick. The sound works, and the correct device (Logitech Quickcam Communicate STX) is selected in skype, but when I click on "Test" in the video box in Skype, nothing happens. My webcam works fine with Cheese, just not in Skype. My computer is a desktop Gateway DX4820.

---

### Post by sohlinux on 2010-11-09
did you enable the video check box in skype settings and does it show Camera on /dev/video0?

---

### Post by kernelles on 2010-11-09
> **sohlinux said:**
> did you enable the video check box in skype settings and does it show Camera on /dev/video0?

Yes. See screenshot, attached.

---

### Post by sohlinux on 2010-11-09
sounds like you have a missing lib, I would remove skype with sudo apt-get remove skype and re install it from [http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/)

if it still doesnt work try removing it again and installing from the ubuntu software centre

---

### Post by kernelles on 2010-11-09
> **sohlinux said:**
> sounds like you have a missing lib, I would remove skype with sudo apt-get remove skype and re install it from [http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/)

if it still doesnt work try removing it again and installing from the ubuntu software centre

Reinstalling it from Skype's website did not fix the problem, but reinstalling from Ubuntu Software Centre did, although I had to enable the partners repository. You must have been right about the dependency issue.

Thanks!

---

### Post by sohlinux on 2010-11-09
> **kernelles said:**
> Reinstalling it from Skype's website did not fix the problem, but reinstalling from Ubuntu Software Centre did, although I had to enable the partners repository. You must have been right about the dependency issue.

Thanks!

yep must have been one of the libs missing, glad its fixed it for you.

---

