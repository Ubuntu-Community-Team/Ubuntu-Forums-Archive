---
title: "password / passwords"
date: 2011-03-17
forum: General Help
---

### Post by telegiovi on 2011-03-17
Dear Ubuntu expert users,
I am very new here and look for little help; I am using Maverick Merkaat and if I stay away from the PC (running) for some minutes, when I am back the monitor is black. When I move the mouse a window appears and I have to put a password in order to continue. How can I remove this function?
I live alone and I am the alone user of my PC. How cam I remove the use of all passwords?
Thank you.

---

### Post by mcduck on 2011-03-17
> **telegiovi said:**
> Dear Ubuntu expert users,
I am very new here and look for little help; I am using Maverick Merkaat and if I stay away from the PC (running) for some minutes, when I am back the monitor is black. When I move the mouse a window appears and I have to put a password in order to continue. How can I remove this function?
I live alone and I am the alone user of my PC. How cam I remove the use of all passwords?
Thank you.

Go to System/Preferences/Screensaver and turn off the "Lock screen when screensaver is active"-option. :)

---

### Post by Frogs Hair on 2011-03-17
from the same page use the power management tab set monitor shut off and sleep time

---

### Post by telegiovi on 2011-03-17
Thank you. It works!  But how to remove passwords at all? Is it possible?

---

### Post by mcduck on 2011-03-17
> **telegiovi said:**
> Thank you. It works!  But how to remove passwords at all? Is it possible?

Sure, it's possible. But depending on what passwords you'd want to remove not secure and thus not recommendable.

If you want, I can help with disabling login password (for desktop) and the keychain password.

Login password can be disabled by going to System/Administration/Login Screen and enabling the automatic login option (for your user account, of course). Or if you have many users on the computer and what to still show the login scree, but just not require a password, System/Administration/Users and Groups, and then click the "Change"-button next to each user's password option and enable the "Don't ask password for login"-setting.

If you disable the login password, you'll most likely also have to remove keyring password as well. The keyring is usually unlocked automatically when you log in, but with automatic/passwordless login you'd need to unlock it yourself when  some program tries to access stored keys. Go to System/Preferences/Passwords and Encryption Keys, right-click on the "Passwords:login"-keyring and select "Change Password". Type in your current password and leave the fields for new one empty.

If you want to also remove password from administration tasks, you'll have to wait for somebody else to give the instructions. I have a rule of not helping anybody shoot themselves in the foot. :D

---

### Post by telegiovi on 2011-03-17
"I have a rule of not helping anybody shoot themselves in the foot."

Thank you for your explanations. But why is it so dangerous to remove the administrator password? I do not understand it

---

### Post by mcduck on 2011-03-17
Anyone (or any program) getting any kind of access to your computer, locally or through network, would immediately have full permissions to do whatever they want on your computer. Linux doesn't have quite the same virus & malware problems Windows does, but that's not because of some magical way how it works better, but mainly because of it's strict way of handling users (both human users and system services) and their permissions.

Also it makes it a lot easier for you to to accidentally break things. With a password, you ate least recognize that you are doing something serious, and have a bit of extra time to consider if that's really what you were supposed to do.

You said you are the only user on the system, so you probably don't consider such things important. But the truth is that any computer connected to Internet should be handled like a multi-user system, You might be the only person with access to the machine *now*, but remove all the security and there's no way to guarantee that you'll *stay* the only user of the computer...

Besides, admin tasks really aren't something you should have to do too often. Giving up all security just to avoid having to type in a password once a day/week/month or something like that just doesn't make any sense.

But like I said, in the end it's up to you what you choose to do. Finding information about disabling such security features is very easy, and probably somebody else will even jump in to give you instructions if you ask.

edit. here's something interesting to read about the subject:
[http://www.linuxuser.co.uk/features/security-in-linux/]("http://www.linuxuser.co.uk/features/security-in-linux/")
[http://www.linuxtopia.org/LinuxSecurity/LinuxSecurity_Introduction1.html]("http://www.linuxtopia.org/LinuxSecurity/LinuxSecurity_Introduction1.html")

---

### Post by antaios256 on 2011-03-17
I fully support the not shooting oneself. the information you are looking for is on the forums (this debate came up 2 or 3 days ago. if you search the answer is there.

---

### Post by telegiovi on 2011-03-17
your explanations are very full of sense. I will not remove password.
Thank you!

---

