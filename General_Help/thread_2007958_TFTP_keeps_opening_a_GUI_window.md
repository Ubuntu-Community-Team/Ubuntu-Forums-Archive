---
title: "TFTP keeps opening a GUI window"
date: 2012-06-21
forum: General Help
---

### Post by ki4jgt on 2012-06-21
I'm currently running Windows as there are no router specific instructions for Linux. I wish to flash my router with DD-WRT but every time I get to the point of using the commandline to flash ( per [http://dd-wrt.com/wiki/index.php/Belkin_F5D7230-4_v2xxx_and_Lower](http://dd-wrt.com/wiki/index.php/Belkin_F5D7230-4_v2xxx_and_Lower) ) TFTP brings up a GUI instead of flashing the router like the instructions say.

---

### Post by alphacrucis2 on 2012-06-21
> **ki4jgt said:**
> I'm currently running Windows as there are no router specific instructions for Linux. I wish to flash my router with DD-WRT but every time I get to the point of using the commandline to flash ( per [http://dd-wrt.com/wiki/index.php/Belkin_F5D7230-4_v2xxx_and_Lower](http://dd-wrt.com/wiki/index.php/Belkin_F5D7230-4_v2xxx_and_Lower) ) TFTP brings up a GUI instead of flashing the router like the instructions say.

The windows instructions should work under linux (just adjust which directory is being used. It's just using tftp to copy a file. No idea why windows is opening a gui when you type in tftp. Did you get tftp under Windows by enabling it via Programs and Features or did you install some third party tftp client? If that later then that may be why because I tested the Windows supplied tftp and it doesn't open any gui.

---

### Post by ki4jgt on 2012-06-21
> **alphacrucis2 said:**
> The windows instructions should work under linux (just adjust which directory is being used. It's just using tftp to copy a file. No idea why windows is opening a gui when you type in tftp. Did you get tftp under Windows by enabling it via Programs and Features or did you install some third party tftp client? If that later then that may be why because I tested the Windows supplied tftp and it doesn't open any gui.

I downloaded it directly from the dd-wrt website. Upon reading further into it (further down the page) I realized that there was a tutorial on the GUI application as well. I was wanting to use CLI but hey I'll take what I can get. All that was required for the GUI though was simply browsing to the .bin, typing the address of the router in and then clicking a button. I'm currently using my new DD-WRT router to repeat a public wifi hotspot I've been wanting to have in my home for months. :) I love the power of open source. I have the freedom to move from room to room now with my laptop typing away as I please.

---

