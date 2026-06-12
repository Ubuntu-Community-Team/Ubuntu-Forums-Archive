---
title: "updating karmic to lucid from the alternate disk is driving me insane, please help!"
date: 2010-05-04
forum: General Help
---

### Post by shebaw on 2010-05-04
Hi everyone

I have a super slow connection so upgrading live is unthinkable. I can't install Lucid from scratch since restoring my pc back to how it was will be a major pain.I've been using ubuntu 9.10 exclusively for about 2 months now. Everything works great except my graphics cards but I don't mind. Anyways, I got the Lucid CD and tried it and loved it. It had out of the box support for my graphics card for the first time and it looked and felt better. So I tried to upgrade from that but found out that I need the alternate CD to do that. So I made my friend download that for me and I tried to upgrade from that but no luck. I mounted the iso file and managed to get the upgrade manager to run, but it still requires internet connection to continue even after choosing not to update from the internet. What is the problem?

Thanks in advace.

P.S. My diskimage isn't corrupted, I've checked the hash against the one on the Canonical's site and its the same.

---

### Post by Portmanteaufu on 2010-05-04
I had the exact same experience. The trick is to right click your network connection tray icon and uncheck "enable networking". Once it's down, start the upgrade and tell it not to use the internet.

For whatever reason, if it detects a connection during the upgrade setup, it tries to use it to pull down checksums. I'm sure it was an oversight on the devs' part, but I had to try a few things before I got it to go.

Hope that helps!

---

### Post by shebaw on 2010-05-04
> **Portmanteaufu said:**
> I had the exact same experience. The trick is to right click your network connection tray icon and uncheck "enable networking". Once it's down, start the upgrade and tell it not to use the internet.

For whatever reason, if it detects a connection during the upgrade setup, it tries to use it to pull down checksums. I'm sure it was an oversight on the devs' part, but I had to try a few things before I got it to go.

Hope that helps!

I will try it out and will post my result.

Thanks for the reply.

---

### Post by shebaw on 2010-05-04
Nope, it didn't work.

It displays an error message that reads
"The upgrade is now aborted. Please check your Internet connection or installation media and try again. All files downloaded so far are kept."

I have some other programs like Google Chrome that I installed manually, not from the Ubuntu software center. Could that be the problem, but still, I don't see the reason why it asks for internet connection when I'm doing offline upgrade.

Any help will be appreciated!

---

### Post by shebaw on 2010-05-05
*bump*

Edit:
I just partitioned my harddrive, backedup my documents onto the new partition and installed lucid from scratch. 

Portmanteaufu, thanks for trying to help.

---

### Post by Portmanteaufu on 2010-05-05
> **shebaw said:**
> *bump*

Edit:
I just partitioned my harddrive, backedup my documents onto the new partition and installed lucid from scratch. 

Portmanteaufu, thanks for trying to help.

Sure thing. Sorry the easy path didn't work out for you this time.

---

