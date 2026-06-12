---
title: "URL Link in Thunderbird does NOT launch browser"
date: 2006-05-17
forum: General Help
---

### Post by Delphi123 on 2006-05-17
Dear friends:

This is a pretty serious error. When I click on a URL link in a message in Thunderbird, nothing happens. It doesn't launch any browser, not Konqueror or Firefox. How can I please fix this? This makes using my mail quite difficult.

Would appreciate your help.

Thank you.

Benjamin

---

### Post by taipan899 on 2006-05-17
Ben,

I don't know if this will help but, I had the same problem in Firefox after an upgrade. I had to remove Firefox and then reinstall it. You could try a reinstall through,  System - Adminstration - Synaptic Package Manager.
Best of luck.

Taipan899

---

### Post by Delphi123 on 2006-05-17
Dear taipan:

Everything OK now. Don't know what happened except that I set the home page in Firefox, which solved both the URL issue and the strange error message. 

Thanks so much.

Benjamin

---

### Post by dibble5504 on 2008-06-07
A simpler solution than re-installing is to do:
Edit > Preferences > Advanced > System Defaults > General
Click on the Check Now button to verify that Firefox is set as your default browser.  

Chances are that this association has been lost.

Regards,

Paul

---

### Post by papabean on 2008-06-09
Neither of these solutions worked for me.  I'm running Kubuntu 8.04 and resorted to installing thunderbird-gnome-support.

```
sudo apt-get install thunderbird-gnome-support
```

Now, links work just fine in Thunderbird.  Of course, I have extra Gnome crud, but small price to pay for working linkage in my mail client.

---

