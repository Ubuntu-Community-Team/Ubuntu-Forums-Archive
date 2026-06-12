---
title: "Re: Problem Booting Ubuntu"
date: 2011-02-02
forum: General Help
---

### Post by chitoo on 2011-02-02
I install ubuntu 10.1 on my laptop. And then reboot the machine.
I already installed winxp. When I reboot my laptop, I choose linux at advanced bios setting and then there is a problem. Problem is my laptop run only winxp. Why I don't know.
How can I solve this, please. I'm beginner user of ubuntu.

---

### Post by s.fox on 2011-02-02
Thread hijacking is not encouraged on this forum.  Please create your own thread for a problem.

Thank you.

---

### Post by Rubi1200 on 2011-02-02
Hi and welcome to the forums chitoo :-)

This is what you need to do please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Once we have this information it will be easier to help you.

Thanks.

---

