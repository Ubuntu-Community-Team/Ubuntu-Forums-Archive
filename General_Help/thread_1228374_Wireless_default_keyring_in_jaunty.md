---
title: "Wireless default keyring in jaunty"
date: 2009-07-31
forum: General Help
---

### Post by n.hinton on 2009-07-31
Wireless default keyring in jaunty has been buging me since my first install of jaunty a couple of months ago.

I edited my witless network connection almost by accident discovered “make available to all users” check box, checked it, now jaunty boots connected, with no requests for passwords.

After accomplishing my objective, I googled edit network connection and found 

[http://preview.tinyurl.com/n2jv9y](http://preview.tinyurl.com/n2jv9y)

[http://www.eteanga.ie/solution-to-ubuntu-904-enter-password-for-default-keyring-to-unlock/](http://www.eteanga.ie/solution-to-ubuntu-904-enter-password-for-default-keyring-to-unlock/)

Why isn't this stuff published in the support pages, how to do it and implications etc. there are enough posts in this forum regarding this issue. It reminds me very much of Microsoft and the way they attempt to conceal configuration settings, only to be made public by users - - - this is Ubuntu - - - So why should this be?

---

### Post by W3ird_N3rd on 2009-08-21
Thanks a million buddy! In previous Ubuntu versions I used to set a blank keyring password to make it connect by default, but I couldn't find again how to do that in Jaunty. Asked Google "jaunty wireless keyring" and this was the first page to pop up, and it works perfectly!

I'm aware it's not perfectly totally 100% secure (what if the laptop gets stolen and somebody chases the owner to his or her home and breaks into their wireless network [-X) but I really don't want to ask my mother to enter a password everytime she boots up the system.

---

### Post by tgeer43 on 2009-08-21
> **n.hinton said:**
> Why isn't this stuff published in the support pages?Is this your question?

At any rate, this probably belongs in the [COLOR=RoyalBlue][Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")[/COLOR] forum.

tgeer

---

### Post by jrssystemsnet on 2009-08-28
Thank you, n.hinton!

---

### Post by ricojonah on 2009-10-22
Just in case the site that those URLs refer to change, here's the quick info on how to correct the keyring-prompt-on-startup issue:

1) Right-click on your Network Manager applet (tray icon) and select "Edit Connections"
2) Click on the Wireless tab, make sure your wireless network is selected, and click on "Edit".
3) At the bottom on the new window, check "Available to all users".
4) Close all the windows, reboot, and test to ensure that this solves the issue.

This seems like a much better approach than simply using a blank password for the keyring. While it's unlikely, I certainly wouldn't want anyone to  have access to my keyring passwords by simply power on my laptop. (Beware the snooping room-mates!)

Thanks for the links!

---

### Post by guriinii on 2009-10-29
Thank you very, very much. This has been doing my head in.

---

### Post by MockY on 2009-10-30
> **ricojonah said:**
> Just in case the site that those URLs refer to change, here's the quick info on how to correct the keyring-prompt-on-startup issue:

1) Right-click on your Network Manager applet (tray icon) and select "Edit Connections"
2) Click on the Wireless tab, make sure your wireless network is selected, and click on "Edit".
3) At the bottom on the new window, check "Available to all users".
4) Close all the windows, reboot, and test to ensure that this solves the issue.


THANK YOU SOOO MUCH!! 
Sorry for the caps but this is something I always though was a bug, starting with Feisty (unless this capability is new for Karmic). I have always been a user of WiCd because of this reason. Now I don't have to.
Awesome!

---

### Post by xboxSlayer on 2010-05-13
> **ricojonah said:**
> Just in case the site that those URLs refer to change, here's the quick info on how to correct the keyring-prompt-on-startup issue:

1) Right-click on your Network Manager applet (tray icon) and select "Edit Connections"
2) Click on the Wireless tab, make sure your wireless network is selected, and click on "Edit".
3) At the bottom on the new window, check "Available to all users".
4) Close all the windows, reboot, and test to ensure that this solves the issue.

Thanks! This worked for me as well.

---

### Post by JAS40 on 2010-10-21
> **ricojonah said:**
> Just in case the site that those URLs refer to change, here's the quick info on how to correct the keyring-prompt-on-startup issue:

1) Right-click on your Network Manager applet (tray icon) and select "Edit Connections"
2) Click on the Wireless tab, make sure your wireless network is selected, and click on "Edit".
3) At the bottom on the new window, check "Available to all users".
4) Close all the windows, reboot, and test to ensure that this solves the issue.

This seems like a much better approach than simply using a blank password for the keyring. While it's unlikely, I certainly wouldn't want anyone to  have access to my keyring passwords by simply power on my laptop. (Beware the snooping room-mates!)

Thanks for the links!
Thanks, that worked a treat!

---

### Post by GregoryMA on 2010-10-23
I also wanted to thank you for this.  I have been looking for a way to make the password free login actually a password free login for a long time.

Greg

---

