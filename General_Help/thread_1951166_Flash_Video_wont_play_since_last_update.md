---
title: "Flash Video wont play since last update"
date: 2012-04-02
forum: General Help
---

### Post by noalternative on 2012-04-02
I updated my software today through apt-get.  It updated opera and adobe flash plugin.   Now I can not play youtube and vimeo videos anymore in opera.  I tried firefox, but it crashes whenever I tried to play videos, so I assume it is a problem with the latest flash update.  Is there a way to roll it back to the previous version.  I am using lucid lts!

---

### Post by pootan on 2012-04-02
Install the add-on in this thread:

[http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)



 restart Firefox. Click on the Flash Aid button somewhere in the top right (you may have to drag it there from customise first) and choose check update. Install the beta version with only Override Gpu Validation ticked. That's worked for me on 3 different installs so far.

---

### Post by Shadius on 2012-04-02
> **noalternative said:**
> I updated my software today through apt-get.  It updated opera and adobe flash plugin.   Now I can not play youtube and vimeo videos anymore in opera.  I tried firefox, but it crashes whenever I tried to play videos, so I assume it is a problem with the latest flash update.  Is there a way to roll it back to the previous version.  I am using lucid lts!

I had this problem and this thread helped me fix it. I don't know if it'll work for Opera, but it worked for Firefox. Flash-Aid didn't work for me. 

[http://ubuntuforums.org/showthread.php?t=1948626&highlight=flash&page=2]("http://ubuntuforums.org/showthread.php?t=1948626&highlight=flash&page=2")

Good luck.

---

### Post by Bucky Ball on 2012-04-02
I just used this. It was easy.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

I am using Flash plugin version 11.2 r202 on 10.10. I had updated Firefox and flash no longer worked.

---

### Post by Bucky Ball on 2012-04-02
> **Bucky Ball said:**
> I just used this. It was easy.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

I am using Flash plugin version 11.2 r202 on 10.10. I had updated Firefox and flash no longer worked.

(PS: The link in your signature doesn't seem to be working.)

---

### Post by ajgreeny on 2012-04-02
This whole mess is a result of the newest flash version 11.2.202.228 either causing big problems with all flash videos or in certain cases just causing colour problems in them.

See [http://ubuntuforums.org/showthread.php?t=1948626&highlight=flash](http://ubuntuforums.org/showthread.php?t=1948626&highlight=flash) for a lot of discussion of the problem, and the best way to solve it, in my opinion, by going back to version 11.1r102.  You need to get the older version first from [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml](http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml) then extract the libflashplayer.so from the tar version. not the rpm version, and replace the current libflashplayer.so.  You can find your current location from firefox by typing ```
about:plugins
``` in the addressbar.

Using the flash-aid add-on for firefox, which I normally recommend to everyone, did not help at all, as it gave me the same version as the normal updates from the repos.

---

### Post by lovinglinux on 2012-04-02
> **ajgreeny said:**
> Using the flash-aid add-on for firefox, which I normally recommend to everyone, did not help at all, as it gave me the same version as the normal updates from the repos.

If you use the Beta option, which is suggested by default, it will install 11.2.202.221 and not 11.2.202.228. However, I am not running a nVidia machine, so cannot test if that version fixes the problem.

---

### Post by cetag on 2012-04-02
Using Beta version, via Flash-Aid wizard, as in the post above, hasn't worked for me. 
 
So am now going to try ajgreeny's method several posts up.
Will report back.   This is infuriating. 

Strangely,  Firefox -> Tools -> Add-ons -> check up to date   reports that Java is disabled 
and requires updating, as per; 

"For your safety, Firefox has disabled your outdated version 
of Java. Please [upgrade to the latest version."]("http://java.com/inc/BrowserRedirect1.jsp")             


Ubuntu 11.10,    Firefox 11.0

---

### Post by lovinglinux on 2012-04-02
> **cetag said:**
> Using Beta version, via Flash-Aid wizard, as in the post above, hasn't worked for me. 


Thanks for reporting.

---

### Post by cetag on 2012-04-02
Success, for me.   Again, with reference to the  ajgreeny  post above;

On my machine, 
/usr/lib/firefox-addons/plugins/libflashplayer.so   
is a link to 
/usr/lib/mozilla/plugins/libflashplayer.so  (17406436 bytes) 

The libflashplayer.so extracted from the tar install file (see above), is,
../Downloads/install_flash_player_11_linux.i386/libflashplayer.so  (17047244 bytes) 

In su, I copied the newly extracted version and overwrote the 
version in /usr/lib/mozilla/plugins/ 

Success, and this seems robust.  Great!  Many thanks. 

Ubuntu 11.10,    Firefox 11.0

---

### Post by lovinglinux on 2012-04-02
> **cetag said:**
> Strangely,  Firefox -> Tools -> Add-ons -> check up to date   reports that Java is disabled 
and requires updating, as per; 

"For your safety, Firefox has disabled your outdated version 
of Java. Please [upgrade to the latest version."]("http://java.com/inc/BrowserRedirect1.jsp")


[http://blog.mozilla.com/addons/2012/04/02/blocking-java/](http://blog.mozilla.com/addons/2012/04/02/blocking-java/)

---

### Post by 2CV67 on 2013-04-20
> **ajgreeny said:**
> This whole mess is a result of the newest flash version 11.2.202.228 either causing big problems with all flash videos or in certain cases just causing colour problems in them.

See [http://ubuntuforums.org/showthread.php?t=1948626&highlight=flash](http://ubuntuforums.org/showthread.php?t=1948626&highlight=flash) for a lot of discussion of the problem, and the best way to solve it, in my opinion, by going back to version 11.1r102.

I am still stuck in this time-warp of having to use 11.1r102, which now causes big red "vulnerable" warnings & automatic disabling in Lubuntu 12.10 with FF20.0.

Whenever I try to update to 11.2r202 then nothing works - no YouTube videos, no Streetwiew images etc etc.

Any suggestions very gratefully received!

---

### Post by Bucky Ball on 2013-04-20
[I][B]Thread Closed

Reason:[/B][/I] Necromancy. Old thread put to bed.

If a thread hasn't seen any action for a year or more please post a new thread outlining your problem rather than resurrecting it. This will greatly improve your chances of getting help. Good luck.

---

