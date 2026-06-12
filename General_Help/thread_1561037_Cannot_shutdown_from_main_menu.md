---
title: "Cannot shutdown from main menu"
date: 2010-08-25
forum: General Help
---

### Post by ismailkimyacioglu on 2010-08-25
Hello,

After upgrading to the latest kernel, which my Ubuntu 10.04 did automatically, I cannot shutdown, suspend, or restart from the main menu.  In other words, I click ubuntu logo on the taskbar, click Shut Down and select Shut Down or any of the remaining 2 options, but nothing happens.  Just the menu window disappears.

I had adjusted the power button of my notebook to shut down the computer and this works now.

Does anybody know what's wrong and how we can solve it ?

Thanks in advance !

---

### Post by TeoBigusGeekus on 2010-08-25
Try
```
sudo shutdown -h now
```
or 
```
sudo reboot
```
in terminal and post us any error messages.

---

### Post by ismailkimyacioglu on 2010-09-07
Hi TeoBigusGeekus,

Sorry, I had forgotten to activate the notification option :) so I have just seen your message.  Thanks for your reply anyway.  I was able to shutdown from terminal using commands.  Later on, I have found out that the problem was because of OpenOffice quickstarter.  When I disabled it, it became okay.  But I haven't checked further whether there is any solution to overcome this.

---

