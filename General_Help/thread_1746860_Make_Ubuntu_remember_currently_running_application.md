---
title: "Make Ubuntu remember currently running applications."
date: 2011-05-02
forum: General Help
---

### Post by akshay.sulakhe on 2011-05-02
Hello, i have installed Ubuntu 11.04 i.e Natty Narhwal(m i spelling it right?).. Anyways... i want my Ubuntu system to remember currently running applications even when i shut it down. It was possible in ubuntu 10.10...it was in startup applications(i guess). I cant hibernate. It fails to hibernate. Let me know if anyone knows anything. THanks...Have a nice day. Enjoy. :)

---

### Post by shurkes on 2011-05-02
same problem
i don't see the option to remember th runnunig application in System>preferences>startup applications.

---

### Post by JNieto on 2011-05-02
This seems to be a know bug in 11.04.
I have just seen this [http://askubuntu.com/questions/38517/how-to-add-programs-to-start-up](http://askubuntu.com/questions/38517/how-to-add-programs-to-start-up)
I an going to try the "solution" proposed ...

---

### Post by shurkes on 2011-05-02
didn't help me that solution.

---

### Post by akshay.sulakhe on 2011-05-03
I checked as per the proposed solution...it was checked..but it doesn't work...anyone else with any solution...

---

### Post by htellez on 2011-05-16
Same problem. It was pretty useful. I love to change my ubuntu features and from time to time I screw it up and I need to restart my computer. It is awful to open each application again. If there is someone reading... HELP! T.T

---

### Post by beegary on 2011-05-27
Same problem here, ver annoying. I was enjoying my upgrade to 11.04 up until I realised this option has for some unknown reason been removed. ARRGH

---

### Post by linuxinstalledfromhdd on 2011-05-27
Try using the hibernate feature.  It does pretty much the same thing you want to have done.  :)

---

### Post by Rytron on 2011-06-02
I've got the same problem in Linux Mint 11 (based on Natty). That feature was very handy. I tried Ubuntu Tweak>>Startup>>Session Control setting, does not work.

Hibernate has never worked properly for me with Linux. Saving open applications was one of the first things I set up on Ubuntu.

:( :confused:

---

### Post by Yumi on 2011-07-09
Any new information?

Michael

---

### Post by helloicanseeu on 2011-08-06
no solution? ubuntu 11.04 is sick, and has buggy/nonworking usb 3.0 support

---

### Post by shurkes on 2011-08-06
unfortunately my hard drive broke, it was a good opportunity to go back to 10.10 ...

---

### Post by HobbitTR on 2011-09-15
> **JNieto said:**
> This seems to be a know bug in 11.04.
I have just seen this [http://askubuntu.com/questions/38517/how-to-add-programs-to-start-up](http://askubuntu.com/questions/38517/how-to-add-programs-to-start-up)
I an going to try the "solution" proposed ...

Actually the link is here:
[http://askubuntu.com/questions/30931/how-do-i-make-a-program-auto-start-everytime-i-log-in]("http://askubuntu.com/questions/30931/how-do-i-make-a-program-auto-start-everytime-i-log-in")

---

### Post by andras+ on 2011-09-19
-

---

### Post by andras+ on 2011-09-19
-

---

### Post by akshay.sulakhe on 2011-09-19
Still no fix...tried all the methods mentioned in this forum page... :-)

---

### Post by bittner on 2012-03-10
The feature is **definitely broken** and removed since Natty:

From [http://askubuntu.com/questions/30931/how-do-i-make-a-program-auto-start-everytime-i-log-in]("http://askubuntu.com/questions/30931/how-do-i-make-a-program-auto-start-everytime-i-log-in"):
> The reason this option was removed from its normal spot in Startup Applications, is because it has become "broken" in a way. Although some users still report that it works fine, in your case, it may be the other way around

The feature was dropped in Natty, announced on the [Ubuntu Desktop mailing list]("http://www.linux-archive.org/ubuntu-desktop/478109-gnome-session-saving-dropped-natty.html").

Try watching [bug #773688 on Launchpad]("https://bugs.launchpad.net/ubuntu/+bug/773688") and hope to be notified when the bug is fixed.

---

