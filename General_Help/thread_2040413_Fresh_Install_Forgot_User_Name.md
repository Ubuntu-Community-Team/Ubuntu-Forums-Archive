---
title: "Fresh Install Forgot User Name"
date: 2012-08-11
forum: General Help
---

### Post by JrockZ on 2012-08-11
I just installed Ubuntu from the Mini.iso i burned to CD,, either i forgot my username or my password,, probably more like the user name,, it was one of two things but neither work 
Is there a wat to rest the user name and password without being logged on to the desktop? 
Thanks!!
 
***-----------------------***
***Rock On!!***
***JRockZ***

---

### Post by JrockZ on 2012-08-11
disreguard,, i found this,,
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
still doesnt work though and wont reset passwd Grrrrrrrrrrrrr
 
Authentication Token Manipulation Error
Password unchanged

---

### Post by chadk5utc on 2012-08-11
try to reboot and select recovery from there you should be able to get to a terminal as root and find users and change passwords? sorry just checked the link you posted and that should have done it??

---

### Post by JrockZ on 2012-08-11
Edited above post new password typed corectly,, tried this several times
 
[IMG]http://img193.imageshack.us/img193/783/sam1593u.jpg[/IMG]
 
# mount -rw -o remount /
Was done as well

---

### Post by JrockZ on 2012-08-11
Jeeze this is getting crazy! ok it wasnt changing to read/write,, got that finally now normal boot leads me to ubuntu login: initctl: event failed
 
what next?? Grrrrrrrrrrrrrr

---

### Post by JrockZ on 2012-08-11
> **JrockZ said:**
> Jeeze this is getting crazy! ok it wasnt changing to read/write,, got that finally now normal boot leads me to ubuntu login: initctl: event failed
 
what next?? Grrrrrrrrrrrrrr
 [IMG]http://img339.imageshack.us/img339/6397/sam1594i.jpg[/IMG]
 
Something tells me this is NEVER going to work!! So what does this crapola mean???

---

### Post by MG&amp;TL on 2012-08-11
> **JrockZ said:**
> 
 
Something tells me this is NEVER going to work!! So what does this crapola mean???

This will work. This is Ubuntu being verbose so that (admittedly, experienced) people can sort it out. I've no idea what that means, but you can login. Which is good. (That's what toshiba@ubuntu:~$ means, you've got a shell).

What happens if you type:

```
sudo service lightdm restart
```

to (re) start the graphical login.

---

### Post by Supaikoo on 2012-08-11
I had this same problem an hour ago when creating a new admin account for saftey, but the admin account got locked and had no password and i removed admin from my other account.

From the recovery TTY screen you need to remount / because when you boot to TTY in recovery mode, linux is in READ only mode.

Unmount / like below:

> 
sudo umount /
sudo mount -o rw,remount /


umount - unmount /
rw of course implies read/write and then to remount / as read/write mode
 now try running the same commands again, it should work this time to recover your username and password.

Reply with completion

---

### Post by Supaikoo on 2012-08-11
If done correctly it should look like these from my screen. The Umount / got cut off but u get the jist.


See attachment.

---

### Post by JrockZ on 2012-08-11
> **MG&TL said:**
> This will work. This is Ubuntu being verbose so that (admittedly, experienced) people can sort it out. I've no idea what that means, but you can login. Which is good. (That's what toshiba@ubuntu:~$ means, you've got a shell).
 
What happens if you type:
 
```
sudo service lightdm restart
```
 
to (re) start the graphical login.
 Oh good that that is good,, heres what i got on my most recent start up 
[IMG]http://img713.imageshack.us/img713/7180/sam1595k.jpg[/IMG]
 
Then got logged in again and tried what you suggested: (sorry this one is a bit blurry)
 
[IMG]http://img543.imageshack.us/img543/435/sam1597j.jpg[/IMG]
 
Hmmm so now what?

---

### Post by Cheesemill on 2012-08-11
When you got the option in the installer, did you select to install a GUI?

By default the mini CD doesn't install a graphical interface, just the command line interface which is what you are seeing.

You have a properly installed system at the moment just one without a GUI.

If you are connected to the internet and want the standard Ubuntu interface you can install it by typing:
```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---

### Post by JrockZ on 2012-08-11
Oh well im stuck on this now i guess,,,, may have this computer sold -as is- today but just incase not what the heck do i do now?? anyone?

---

### Post by jockyburns on 2012-08-11
Try downloading the ISO to a USB stick (using another computer). Set the problem computer to boot from USB first, by entering he bios screen, then completely install Ubuntu over the top of everything (you do get this option) Result? One working PC. :D:D

---

### Post by MG&amp;TL on 2012-08-12
> **JrockZ said:**
> Oh well im stuck on this now i guess,,,, may have this computer sold -as is- today but just incase not what the heck do i do now?? anyone?

As cheesemill said, depending on what CD you chose, if you want a user interface (your current one isn't too bad, but browsing the web, etc is a no-no), you'll have to run the command he gave. Alternatively, you can download the recommended one for your system from the ubuntu download page. Which will install a GUI.

If you DID have a GUI before, it's possible something got corrupted on your hard disk. In which case, try running Cheesemill's command and see what you get.

---

### Post by JrockZ on 2012-08-12
*> **jockyburns said:**
> Try downloading the ISO to a USB stick (using another computer). Set the problem computer to boot from USB first, by entering he bios screen, then completely install Ubuntu over the top of everything (you do get this option) Result? One working PC. :D:D*
*Cant get it to boot from USB anymore or i would have done that,,,, *
 
*Ill try that Cheesemill *

---

