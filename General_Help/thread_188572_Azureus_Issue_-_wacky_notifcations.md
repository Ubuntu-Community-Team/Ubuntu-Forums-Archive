---
title: "Azureus Issue - wacky notifcations"
date: 2006-06-04
forum: General Help
---

### Post by badrad on 2006-06-04
Not sure if this is the right place to post this, but maybe someone can help.

I used Azureus in Windows and would prefer to keep using it now that I have switched to Ubuntu. It runs beautifully, its just that under certain conditions it has these notifications that slide up in the bottom right of the screen. They have a "hide" button on them to dismiss them - clicking on them I cannot dismiss them, they stay forever! There is one stuck on now and it renders the program useless. It still works but I can keep this program open if its going to keep this thing on my screen on top of everything. I click hide and it does nothing.

Any help appreciated, I don't even know where to start :)

---

### Post by no1wantdthisname on 2006-06-04
Either restart Azureus to get rid of the popup or download the beta version of Azureus.
Or go to [http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)
and replace your Azureus2.jar with the new one.
The beta fixes the popup problem and it's stable so far as I can tell.

---

### Post by panurge77 on 2006-06-04
I hapenned to me. I killed java on the system monitor and opened azureus again and taht worked for me...

---

### Post by badrad on 2006-06-04
I had tried killing Java with no luck.

[QUOTE=no1wantdthisname]Either restart Azureus to get rid of the popup or download the beta version of Azureus.
Or go to [http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)
and replace your Azureus2.jar with the new one.
The beta fixes the popup problem and it's stable so far as I can tell.[/QUOTE]

Well I had already tried restarting, but using the latest beta sure did fix the problem, thanks no1wantdthisname!

I was able to figure out how to install it too which was cool. For any one who stumbles on this thread, if you download the latest to your desktop you would do this:

```
sudo cp Azureus2.jar /usr/share/java/Azureus2.jar
```

---

### Post by Hairy_Palms on 2006-06-04
i have the same problem on windows and linux, so im pretty sure its just an azureus problem in that the "hide" button lacks functionality. just kill java and restart azureus works for me.

---

