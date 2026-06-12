---
title: "Ubuntu won't let me in after updates"
date: 2011-12-21
forum: General Help
---

### Post by Arnoldsat on 2011-12-21
Hello everyone,

If you would be so kind as to help me please. I'm using Ubuntu 10.04 LTS desktop 32bit.
The update manager asked if it could install updates this morning, and after it finished it said it required a reboot.

After rebooting it shows a violet screen, plays a short drum sound (which is weird because I have all sounds turned off) and asks me to click on my username and enter the password.
It never asked me that before, it's supposed to boot directly to the desktop.
But when I enter the password the screen becomes black, and after a second the violet screen reappears, and asks me to click on my username and enter the password.

I can do this forever, I never reach the desktop. Although it does not tell me if I entered the password correct or incorrect I tried setting the password through recovery. That went as it's supposed to but that did not help me to log in afterwards.

Since this occurred after the udates I also tried 'repair broken packages' in recovery but that did not help either, after checking it shows there were no bad packages.

In recovery I can choose 'drop to shell prompt' and then I get the terminal prompt.
Still no desktop but I am able to log in the FTP server (vsftpd) that is installed on the system. And after starting the apache2 webserver with the correct commands this works too.

Any ideas how I can get to the desktop please?

Thanks Arnold.

---

### Post by TeoBigusGeekus on 2011-12-21
> **Arnoldsat said:**
> 
After rebooting it shows a violet screen, plays a short drum sound (which is weird because I have all sounds turned off) and asks me to click on my username and enter the password.

Did you upgrade to Oneiric by mistake?

---

### Post by jwbrase on 2011-12-21
Can you get a text mode login? Boot normally, then, when you get to the purple login screen, hit CTRL-ALT-F1.

You should see the line "[name of your computer] login:" and a blinking cursor. Enter your username.

You'll be prompted for your password. Type it in.

At this point, if something isn't horribly, horribly wrong, you should get a shell prompt.

If you do, it means that the system is accepting your username and password, but something is wrong on the graphical side of things.

If you don't, please post any error messages you get.

You can type CTRL-ALT-F7 to get back to the graphical login screen.

---

### Post by Arnoldsat on 2011-12-24
Thanks for the info dear friends,

But I'm afraid I got impatient...
There is a freshly installed Ubuntu on the system now.
Sorry I didn't follow your suggestions.

Greetings [Arnoldsat]("http://www.arnoldsat.com")

---

### Post by abednego4609 on 2011-12-25
it happens to me right now too... i cant login after i do a hard reset. 
i hope someone can help me here, i dont want to do a fresh install... i dont have an internet connection to support my ubuntu...

i tried login from text mode, but it gives me "Module is unknown" error. 
it reallyreally wont let me login.

---

### Post by abednego4609 on 2011-12-25
checked the .xsession-errors, found out that something happenned in  /etc/profile. all the "new line" ,somehow, replaced with "\n".  

i replaced all "\n" with the enter button.
everything goes well..
:)

---

