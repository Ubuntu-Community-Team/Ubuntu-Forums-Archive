---
title: "Cannot install firefox add-ons"
date: 2009-10-10
forum: General Help
---

### Post by ruinen on 2009-10-10
I am running Ubuntu 9.10 Beta and cannot install any firefox add-ons. 

1. When I click 'Add to firefox' at for example [https://addons.mozilla.org/en-US/firefox/addon/173](https://addons.mozilla.org/en-US/firefox/addon/173) I get a long wait of about 3 minutes, with the status bar at the bottom of firefox saying, "waiting for addons.mozilla.org...". 

2. Finally the Software Installation pop-up appears and I click 'Install Now'

3. Add-ons pop-up appears, on the Installation tab, with a progress bar that doesn't move.

4. Eventually after about 5 minutes I get the error: 

    Firefox could not install the file at 
    [https://addons.mozilla.org/en-US/firefox/downloads/latest/173/addon-173-latest.xpi?src=addondetail](https://addons.mozilla.org/en-US/firefox/downloads/latest/173/addon-173-latest.xpi?src=addondetail)
    because: Download error
    -228

---

### Post by aheckler on 2009-10-10
[This]("http://kb.mozillazine.org/Unable_to_install_themes_or_extensions_-_Firefox#Download_Error_-228") might help.

---

### Post by ruinen on 2009-10-16
thanks but that didn't help. 

I can't even get firefox to work with, "right-click the download link, select "Save Link As..." and download the .xpi"

I select Save Link As, and nothing happens. With any non-xpi file this works fine.

---

### Post by ruinen on 2009-11-06
Just done a fresh install of 9.10, and still the same problem :(

---

### Post by winotree on 2009-11-06
> **ruinen said:**
> Just done a fresh install of 9.10, and still the same problem :(
If you haven't changed your Firefox profile then the problem may still be there.  See the section on Profile here [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567) to see if it helps.

---

### Post by ruinen on 2009-11-06
Thanks I created a new profile and that worked. No idea why, I formatted the partition before installing.

---

### Post by winotree on 2009-11-06
:)

---

### Post by drale on 2009-11-09
I have the release of 9.10 now. I had the same issue, tried upgrading Firefox, recreating profile, reinstall Firefox. Didn't work. Can't even rightclick and save. What did work though was I right-click and saved the plugin on another machine then transfered the plugin installer file over to my Ubuntu and dragged the .xpi file into Firefox. It automatically prompt for install, and worked!

---

### Post by sonickydon on 2009-11-09
It sounds like a cache issue to me. Check the properties of the cache folder within your profile folder.

---

### Post by Petrik on 2009-11-09
This post solved it for me. Use your own ISP DNS numbers instead of copying the ones there though.

[http://ubuntuforums.org/showthread.php?p=8279983#post8279983](http://ubuntuforums.org/showthread.php?p=8279983#post8279983)

---

### Post by ruinen on 2010-05-02
> **ruinen said:**
> Thanks I created a new profile and that worked. No idea why, I formatted the partition before installing.

Just installed 10.04, completely erasing old partitions and have this problem back :(

---

### Post by ruinen on 2010-05-02
> **ruinen said:**
> Just installed 10.04, completely erasing old partitions and have this problem back :(

New profile didn't fix it this time :(

---

### Post by ruinen on 2010-05-02
> **ruinen said:**
> New profile didn't fix it this time :(

Fixed!!

I disabled ipv6 and now it works. I've no idea why that fixes it:)

I am using a new install of 32-bit Ubuntu Desktop 10.04. The only other things installed on it are Skype and NetBeans 6.8. When installing Ubuntu I selected encrypted home folders.

I have a HP530 laptop connecting via wifi to a D-Link  DSL-G624T ADSL router.

---

