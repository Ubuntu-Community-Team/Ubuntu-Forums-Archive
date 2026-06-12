---
title: "How to stop Update Manager from always asking for password?"
date: 2010-11-12
forum: General Help
---

### Post by calande on 2010-11-12
Hello,

I recently set up an Ubuntu computer for a friend who is new to Ubuntu and who is complaining that very often, Ubuntu's Update Manager pops up and asks for password to install updates. How could we make the Update Manager install updates quietly in the background without interrupting and asking for password? Maybe this should even be set as default in forthcoming versions of Ubuntu!
Thanks,

Charles.

---

### Post by Dan_Dranath999 on 2010-11-12
Nothing should be installed without user's permission.

---

### Post by calande on 2010-11-12
But then, your system is insecure... I want a secure system with all software up-to-date.

---

### Post by Verbeck on 2010-11-12
system wide changes always require root privileges and removing the password prompt will make the system insecure

this link gives instructions for removing the password prompt for sudo, so might work in this case : [link]("https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20sudo")
it is NOT recommended  to do so though

---

### Post by calande on 2010-11-12
So what do you recommend in my case?

---

### Post by Verbeck on 2010-11-12
its the devs who aren't recommending it, not me ;)

in software sources (system>administration>) you can set the time interval to check for updates

---

### Post by calande on 2010-11-12
I trust Ubuntu's repository, and I want to allow the computer to install updates that come from this specific repository automatically. I consider this much more secure than not installing any security updates at all. I just would like to find out how to do it.

---

### Post by plucky on 2010-11-12
> **calande said:**
> I trust Ubuntu's repository, and I want to allow the computer to install updates that come from this specific repository automatically. I consider this much more secure than not installing any security updates at all. I just would like to find out how to do it.

Isn't there an option under **Software Sources > Updates** if ticked to download and "install security updates without confirmation" in the background?

Never tried it so don't know if it will work.

Good Luck

---

### Post by ajgreeny on 2010-11-12
You can easily set the system to install security updates without authentication by going to **System ->Administration ->Software sources update** tab, and selecting that tick box.

That will make sure that security is not compromised, but will not install other recommended updates that do not have any effect on security.  A password will still be needed for those to be updated, but they are much less important to the system.

It is possible to stop the sudo password being required for specific applications and actions, but for users who may not be aware of the possible pitfalls, I would certainly not recommend it for all activities.  If you really think it is needed come back again and we can give you more information about editing the /etc/sudoers file, something that must be done with care and only using a specific command, and certainly not simply using gedit.

---

### Post by calande on 2010-11-12
OK, I'll try this, thanks!

---

### Post by TBABill on 2010-11-12
Just keep in mind many updates are application updates (such as your browser) and those should always require a password. Otherwise that system is wide open to attack, which is the major point of using Linux (security). Although that password may be an irritant, that is the major step preventing a maliciously downloaded file from executing, installing, etc. It may be of assistance to your friend to do some reading on Linux security measures so he/she can gain a better perspective of the pitfalls of bypassing some security steps. Then if they are comfortable with doing so at least they will have made a better informed decision rather than just eliminating a step altogether because it is annoying. It should only occur once per day anyhow.

---

### Post by calande on 2010-11-27
But if you only have repositories of well-known sources (Google Chrome, Opera, Adobe), you should be safe, right? My friend doesn't want to spend time learning technical stuff, and usually click "OK" instantly without reading the message (or even types password whenever asked for, not even knowing the program asking).

---

### Post by DeMus on 2010-11-27
> **calande said:**
> But if you only have repositories of well-known sources (Google Chrome, Opera, Adobe), you should be safe, right? My friend doesn't want to spend time learning technical stuff, and usually click "OK" instantly without reading the message (or even types password whenever asked for, not even knowing the program asking).

If (s)he is so used to have a Windows system (that is the place to just click OK and OK and OK without reading what you are agreeing to) then with using Linux (s)he should really change his/her view of using the system safe or not.
When you update your system once a week you only have to use the password once a week. Is that a too high price to pay for having a safe system? I don't think so.
Even without the latest safety releases the system is still safe when using it as a simple user. So when it takes a bit longer before you install the updates, there is still no harm done.
Just convince your friend to keep using the password and don't set the system open as an administrator because then you can expect trouble.

---

