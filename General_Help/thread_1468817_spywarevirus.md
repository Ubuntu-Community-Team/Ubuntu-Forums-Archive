---
title: "spyware/virus?"
date: 2010-05-01
forum: General Help
---

### Post by brampt1 on 2010-05-01
When I try to access [www.ubuntuguide.net](www.ubuntuguide.net) a get a pop up warning to run a scan.  Firefox is locked until I close it under processes. Should I be concerned? What can I scan my system with?  I installed Lucid yesterday.

---

### Post by Darkdelusions on 2010-05-01
I tested the site and it appears to be a virus\malware site. If you are looking for ubuntu guide your going to the wrong site. the Correct URL for Ubuntu guide is[http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by GSF1200S on 2010-05-01
> **brampt1 said:**
> When I try to access [www.ubuntuguide.net](www.ubuntuguide.net) a get a pop up warning to run a scan.  Firefox is locked until I close it under processes. Should I be considered? What can I scan my system with?  I installed Lucid yesterday.

You dont need to scan it with anything. While I suppose it is possible viruses exist in the wild for Linux, I have yet to see a virus take down a Linux box. This has a lot to do with how Linux handles permissions, and the fact that security holes are often patched very soon after they are found. Just ignore that site- all it did was some HTML trickery to make you think you are infected. This is one of the positives of using Linux. At least currently (and I suspect probably always), Linux doesnt deal with the dangers of viruses.

Certain rootkits have been designed to work on Linux, but these are mostly made in lab environments and are often patched out of effectiveness. To double check to ensure you dont have a rootkit, checkout rkhunter and chkrootkit, both of which are available in the repos.

---

### Post by 2hot6ft2 on 2010-05-01
> **Darkdelusions said:**
> I tested the site and it appears to be a virus\malware site. If you are looking for ubuntu guide your going to the wrong site. Ubuntu guide is url is [http://ubuntuguide.org](http://ubuntuguide.org)
+1
Reported it here:
[http://www.google.com/safebrowsing/report_badware/](http://www.google.com/safebrowsing/report_badware/)

Here are some more guides

[Karmic Koala Bible AND so much more good info.]("http://www.makeuseof.com/tech-fun/search/?cx=009717636731598800244%3Aqhe4rh7wuxs&cof=FORID%3A11&q=Ubuntu+Karmic+Koala+Bible&sa=%C2%A0#288")
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)

A couple cheat sheets you can print out
[http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/)
[http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/)

---

### Post by Darkdelusions on 2010-05-01
Don't report Ubuntuguide.org it is the right url for ubuntuguide the url that op posted is the malware one. I apologize for the confusion there

---

### Post by sendblink23 on 2010-05-01
> **2hot6ft2 said:**
> +1
Reported it here:
[http://www.google.com/safebrowsing/report_badware/](http://www.google.com/safebrowsing/report_badware/)

Here are some more guides

[Karmic Koala Bible AND so much more good info.]("http://www.makeuseof.com/tech-fun/search/?cx=009717636731598800244%3Aqhe4rh7wuxs&cof=FORID%3A11&q=Ubuntu+Karmic+Koala+Bible&sa=%C2%A0#288")
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)

A couple cheat sheets you can print out
[http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/)
[http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/)


you reported the wrong site

BAD: [http://ubuntuguide.net](http://ubuntuguide.net)

GOOD: [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by 2hot6ft2 on 2010-05-01
> **Darkdelusions said:**
> Don't report Ubuntuguide.org it is the right url for ubuntuguide the url that op posted is the malware one. I apologize for the confusion there
I reported the right one,:lolflag: Grabbed the url from the original post.

Also the attack site is using java script so if you install the NoScript firefox add-on it will stop those
Tools > Add-ons > Get Add-ons
search for NoScript and install it.

---

### Post by The Thunder Chimp on 2010-05-01
Yeah it crashes GNU IceCat too. It's really fishy when you see Windows borders under Ubuntu...

---

### Post by brampt1 on 2010-05-01
Ran a scan with rkhunter, nothing found. Thanks :)

---

