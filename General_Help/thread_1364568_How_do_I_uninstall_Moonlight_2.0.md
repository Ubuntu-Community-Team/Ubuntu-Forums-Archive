---
title: "How do I uninstall Moonlight 2.0?"
date: 2009-12-26
forum: General Help
---

### Post by dln9 on 2009-12-26
I am running Ubuntu 9.10, and I am using Firefox 3.5.6.  I installed the extension Moonlight 2.0.  It doesn't seem to do anything useful.  So, I tried to uninstall it by going to Tools|Add-ons in Firefox, then going to Extensions, and then clicking on Uninstall for Moonlight 2.0.  When I do that, I get a message that says I should Restart Firefox.  I click on Restart.  Firefox closes, and then restarts.  But, when Firefox restarts, it presents me with the Add-ons window showing all my installed Extensions, with Moonlight 2.0 highlighted as installed (!), and with a message telling me that "1 new add-on has been installed", presumably referring to Moonlight 2.0.  If I try uninstalling it again, I end up going through the same endless cycle.  

I tried uninstalling other extensions, those worked just fine, so the problem is with Moonlight.  

How do I uninstall this extension?  

Thanks.

---

### Post by ankspo71 on 2009-12-26
Hi,
I have moonlight installed from the repositories and I have moonlight 2.0 installed from the moonlight site. A quick search using...
```
sudo updatedb
locate moon
```
found these results:

The moonlight addon in my /home/<user>/ folder:
/home/james/.mozilla/firefox/1jl2fnvr.default/extensions/moonlight@novell.com/

Some system files and folders:
/usr/lib/libmoon.so
/usr/lib/libmoon.so.0
/usr/lib/libmoon.so.0.0.0
/usr/lib/moon/*     

And then finally the xulrunner plugin folder:
/usr/lib/xulrunner-addons/plugins/libmoonloader.so

So my advice would be, uninstall moonlight in Synaptic Package Manager.
Uninstall moonlight 2.0 from firefox.

Run the code above to locate remaining moonlight files
then I would probably rename each remaining file to something like libmoon.so.0.0.0.backup

If the ubuntu keeps running fine AND moonlight disappears from firefox, then you know it will be safe to delete them. uninstall them as properly as you can first though.
Hope this helps.

---

### Post by dln9 on 2009-12-28
Thanks, this seemed to work.

---

