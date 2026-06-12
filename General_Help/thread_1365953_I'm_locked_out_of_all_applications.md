---
title: "I'm locked out of all applications"
date: 2009-12-27
forum: General Help
---

### Post by dpdx on 2009-12-27
I'm just getting started with Ubuntu. By incorrectly typing in my password, it appears I have been locked out of all applications. My computer boots up, but no bootable application icons or drop-down menus are available. Right clicking results in absolutely no response, no matter where I click. All I am able to do is shut off the power supply manually (not system quit) to the box and restart. That's as far as my admin login will take me.

How can I recover from this?

Thank you much!:(

---

### Post by dkmiles on 2009-12-27
> **dpdx said:**
> I'm just getting started with Ubuntu. By incorrectly typing in my password, it appears I have been locked out of all applications. My computer boots up, but no bootable application icons or drop-down menus are available. Right clicking results in absolutely no response, no matter where I click. All I am able to do is shut off the power supply manually (not system quit) to the box and restart. That's as far as my admin login will take me.
 
How can I recover from this?
 
Thank you much!:(
 I have forgotten my password, and can't install programs. I may be wrong, but I think for both of us, the only solution is to use the recover or reinstall disk that comes with our computers - and reinstall everything. That's the only way you can get rid of the old password unless you are a computer programmer and knew where to find that code in the program and delete it. Since that isn't us - we are screwed and will have to do a complete reinstallation.

---

### Post by drdanielfc on 2009-12-27
Perhaps this can help?

[http://ubuntuforums.org/showthread.php?t=1365956](http://ubuntuforums.org/showthread.php?t=1365956)

---

### Post by marshmallow1304 on 2009-12-27
When the Grub menu appears, boot into recovery mode.  If you have only Ubuntu on your computer, you may need to hold down Shift or hit Esc when "Grub loading" appears to get to the menu.  Once at the prompt, issue
```
passwd <yourusername>
```
where <yourusername> is your username.  Give it a new password when it asks and confirm.  Then
```
reboot
```

See [here]("http://psychocats.net/ubuntu/resetpassword") for more info.

---

### Post by dpdx on 2009-12-28
Thanks but how do I get the GRUB mention to appear. Upon powerup, I get nothing on my desktop, when it loads. Is there a shortcut key to launch GRUB?

---

### Post by stinkeye on 2009-12-28
[_[COLOR="DarkRed"]http://psychocats.net/ubuntu/resetpassword[/COLOR]_]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by dpdx on 2009-12-28
Cool. Well I was able to change my user passwords doing a recover reboot, but I still can't change the admin password, and my application icons and menus remain unresponsive. Thanks for any clues.

---

