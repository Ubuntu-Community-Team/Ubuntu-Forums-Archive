---
title: "First character of every line is missing"
date: 2009-06-26
forum: General Help
---

### Post by Palu on 2009-06-26
Hello :popcorn:

**Issue:** I installed Ubuntu 9.04 server edition on my computer and cannot see the first column of text. If a message starts with "The server is..." I will only see "he server is..." and I cannot simply adjust the monitor to correct this. When I had desktop edition, this was the same, but the GUI interface corrected the issue. This is also true for when I had Windows. The bootup featured first character truncation on each line, and in the Windows GUI, it was normal. I also ran gOS for a while, and this monitor had no issues in the GUI. I don't remember using the console there.

**Hardware:** The monitor is a Kogi. The model number seems to be L7EH TA. I can't find any text problems when Googling that model number. My graphics are from an integrated VIA UniChrome Pro. The machine details are here: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3511118&sku=E80-TC2502](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3511118&sku=E80-TC2502)

**Suspicion:** It sounds like it's a case of needing a driver. I probably also need it to load during bootup somehow. Please help me understand how to do both. Thank you very much. :)

**Suspicion #2:** Perhaps it's my Everex bios... how does one attempt to change bios? I'm not particularly attached to my bios and would love to try upgrading them if I knew how.

---

### Post by ad_267 on 2009-06-26
This might help: [http://ubuntuforums.org/showthread.php?t=122936](http://ubuntuforums.org/showthread.php?t=122936)

Have a look at the table in the 7th post and set the vga option in grub based on that.

Also see the section here on working with consoles: [http://urukrama.wordpress.com/2008/10/26/giving-new-life-to-an-old-computer/](http://urukrama.wordpress.com/2008/10/26/giving-new-life-to-an-old-computer/)

---

### Post by Palu on 2009-06-26
Thanks... so... I adjusted my monitor, and is seems to have worked. I have never had to adjust it in the past AND I thought I tried it already just in case. Not sure how this happened like this. I appreciate the help though! :D

---

### Post by ad_267 on 2009-06-26
Oh well, glad you got it working!

If you're going to be working on the terminal directly from that computer you might want to have a look at that last link anyway, it explains how to change your terminal font and increase the resolution in ttys.

---

