---
title: "A solution to the mobile phone bluetooth browse problem"
date: 2009-11-02
forum: General Help
---

### Post by akaAndrew on 2009-11-02
This was a problem that occurred after the upgrade to 8.10. Prior to that, browsing my mobile phone via bluetooth worked.

After the upgrade, the following message displayed whenever I wanted to browse the phone... 

> Could not display "obex://[MAC_ADDESS]/" 
 Error: Connection refused
 Please select another viewer and try again.

This solution assumes you are able to discover and pair correctly. It doesn't correct any problems you might be having there. I have not tested it on distros other than 9.04 UNR... though I suspect it would work on 8.10 & 9.04. Perhaps someone can test and confirm? 

First, a bit of preamble. I used the Blueman bluetooth manager to pair, control browsing, etc. That is not because it is necessarily better than other apps but because it had an essential feature enabling scripting/configuration of the browse. That's what this fix depends upon. The script I borrowed used konqueror to browse... and therefore required you to load kde. That's a bit of an overhead just to browse your mobile! So I tweaked it to use nautilus and, much to my surprise, it worked. Here's the steps....

1.[ Install Blueman]("http://bigbrovar.wordpress.com/2009/02/14/blueman-an-awesome-bluetooth-manager-for-ubuntu/")

2. [Download this script]("http://www.kde-apps.org/content/show.php/kde4+bluetooth+files+open-bs6q/?content=108869"), follow the instructions, load obexfs (sudo apt-get install obexfs) but ignore konqueror!

3. Amend the script as follows; 

   - change "kdialog --passivepopup"  to  "zenity --text --info". There are 4 occurrences of that, they are just pop windows that we're changing from the kde to gnome environment.

  -  change "out=`konqueror $dir 2>&1`" to "out=`nautilus $dir 2>&1`". That's the important change! We use nautilus and the gnome environment and not konqueror & kde.

All going well, that's all you'll need. Browsing your mobile should now work.

There is probably a more elegant solution, and I'm not entirely sure what I'm doing in there ;) So please please please feel free to make suggestions and amendments to any of the above. Particularly the use of zenity, as these pop ups require you to hit 'enter'. I don't think that the kdialog pop-ups did. I'm no scripter, merely a hacker and borrower. What I have done is a quick and dirty 'proof of concept' sort of thing. I fully acknowledge that it needs polishing, if not re-working!

Good luck!! :D

---

