---
title: "Installing printer from command line"
date: 2006-06-12
forum: General Help
---

### Post by pubwho on 2006-06-12
I know the printer I have ( Epson Stylus D68 ) works fine under Ubuntu with CUPS and Gutenprint when I install it using Ubuntu Desktop.

I'm wanting to set up a print server, I've installed Ubuntu server edition. I don't want to install Ubuntu Desktop because the computer isn't very powerful.

Can anyone tell me how I go about installing and setting up the printer from the command line?
pubwho is online now   	Edit/Delete Message Reply With Quote Quick reply to this message Multi-Quote with this Post

---

### Post by 5-HT on 2006-06-12
The easiest way I can think of would be to use CUPS webadmin via  console-based browser.

w3m is installed by default for the desktop install (not sure about server, you may need to install w3m or your preferred console-based browser) so it should be as simple as: ```
 w3m http://127.0.0.1:631 
``` 

You may need to add cupsys to the shadow group to be able to add a printer from CUPS webadmin:

```
sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart
``` 
To remove cupsys from the shadow group once you're done:
```
sudo deluser cupsys shadow
sudo /etc/init.d/cupsys restart
``` Hope that helps.

---

