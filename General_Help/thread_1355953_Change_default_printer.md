---
title: "Change default printer"
date: 2009-12-15
forum: General Help
---

### Post by jim1932 on 2009-12-15
I am using ubuntu 8,04,LTS Kernel 2.6.24-26 generic. I have a new printer and tried to change the default printer. I always get instructions to give admin password. Then I get invalid password. I have tried some of the fixes that were given in the forum but none worked for me. Being a navies at the Linux OS I do not know the appropriate commands. Could some one give me step by step instructions to get around the password problem? I hate to have to go back to windows everytime I have something that I have to print!

---

### Post by coffeecat on 2009-12-15
If you are using the first created user account, your login password is the same as your admin password. Presumably you are able to log in OK, or do you have the system set to auto-login? Also, you would need to use your login/admin password when using the update manager or the Synaptic package manager. Are you having the same problem there?

When prompted for your password, make sure you haven't got caps-lock on.

What were the "fixes" you found in the forum, and which didn't work?

---

### Post by khelben1979 on 2009-12-15
What method did you choose to change your default printer?

Also, what is the printer model?

---

### Post by jim1932 on 2009-12-15
All of these suggestions I have tried. There seems to be a general problem with the default changing of printers for there is a bunch of folks having the same problem. The Admin password, or any other one does not work. I was given instructions as to how to work around the problem but I am not smart enough with the OS to figure all of it out

---

### Post by jim1932 on 2009-12-15
I went to the system> admin> printer. and followed the directions for changing the default printer. I always get "enter Admin password" when I enter it gives error password not correct. I know all about the capital lower case issue and make sure I am correct but it will not take it. This is a wide problem for I have read of many others having the same problem. One gave me a way to work around it but I am not saavy enough with the OS to do it. the printer is a HP J3600 and it is in the list of supported printers.

---

### Post by jim1932 on 2009-12-15
I was told to go to Exec= gkdudo/usr/bin/system-confif-printer also I was told to use sudo system-config-printer. I aaumed that I was to input the commands in the terminal. But you can always know how to spell a s u m e. Was I in the right place to do this or is there another place to use the dos commands?

---

### Post by coffeecat on 2009-12-15
> **jim1932 said:**
> There seems to be a general problem with the default changing of printers for there is a bunch of folks having the same problem. The Admin password, or any other one does not work.

I have used every version of Ubuntu since 5.10 on several machines, and I have never come across this. I'm not disputing that you and some others have experienced a problem, but it's not a 'general' problem.

Try this: open Firefox and type 'localhost:631' (no quotes) in the address bar. Click on either 'Administration' or 'Printers' to make the changes you want. You will be prompted for your account username and account password. This worked for me.

---

### Post by khelben1979 on 2009-12-15
I found some drivers when looking at [this page]("http://hplipopensource.com/hplip-web/models/officejet/officejet_j3600_series.html"). I don't know anything about the driver which is provided in Ubuntu, but let's assume it's working.

I think you should try another application to change your printer. Perhaps a KDE printer setup would work better?

Do you have [CUPS]("http://en.wikipedia.org/wiki/CUPS_%28software%29") installed in the system?

---

### Post by jim1932 on 2009-12-15
I don't want to labor the point, however 52 bugs saying they experience the same problem may not be a general problem but it sure is a "bunch" in my mind. Anyway your fix seemed to work for me. I want to thank you for your help. Have a great day and a Merry Christmas!

---

