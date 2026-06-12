---
title: "removing passwords etc"
date: 2011-12-16
forum: General Help
---

### Post by loseby on 2011-12-16
What I want to do is to have one very strong password when I logon and thats it, dont want any other password features etc etc. If PC goes to sleep when I go to use it again I dont want to enter a password. I dont want to enter a password for password ring or whatever its called.

No one else has access to this computer so only need the one password.....  can this be done and how do I do this ?

---

### Post by yetiman64 on 2011-12-16
Use the logoff button > System Settings > Screen, settings to remove the lock on resuming for the screensaver lock. (I am assuming you are on 11.10 - the location of/access to, the system settings may differ with older releases)

If your login password has changed since the keyring was set up initially set up and it keeps asking for your password for a device/program needing to access it, then you may need to look into resetting the keyring password to match with your current password. Once set up correctly the keyring should work automatically for the device/program needing to access it.

The rest of the system will still need the sudo password (your user password as you are the only user) to elevate privileges when necessary, eg. changing some system settings or adding/removing software etc. Turning off these style of password prompts is not supported here (This site supports Canonical's security model), though searching elsewhere on the web you may find useful information for doing this.

---

### Post by loseby on 2011-12-19
I only use Ubuntu for my banking type transactions. Its on an external hard drive that i turn on and select ( f12 key ). Now I want to make my original logon password pretty strong . Now I dont want to have to enter that password twice  when I boot up the system or when using it. No one else has access to this computer 

Surely there should be some simple easy way for me to do this ?

---

### Post by yetiman64 on 2011-12-19
> No one else has access to this computer You have stated that you use the install for internet banking. You are connecting it to a network. Removing password prompts for everything but login/fixing the keyring, is very foolhardy in this case. 

The keyring in your install sounds like it needs fixing, it is not supposed to do what you are suggesting it does. But I am not quite sure what other passwords you mean, I have already explained how to turn off the password for the screen lock. 

Turning off password prompts for installing software or changing system settings is asking to get your machine infected/taken over by malware when internet connected (yes, malware does exist for Linux, but aren't commonly encountered as most people stick with Linux security practices and DON'T turn off password prompts). 

It appears you think Linux + a strong login password is all you need to protect you on the Internet, what is largely protecting you is the need to enter a password for any system changes or software additions.

Please note you can set a strong password and set autologin safely (if no local threats exist for your install, ie other people where you live using your machine etc) also fixing the keyring sounds necessary in your case. But beyond that what you want cannot be answered fully here (**site guidelines**). Google is your friend if you want to reduce the security of your internet banking when online (think, keyloggers and other rootkit style malware, have to get into your system with your assistance, like by turning off system password prompts etc while using a browser online :wink:)

Consider how much you want to compromise your internet banking with the convenience of no passwords (how many local users on your machine is unimportant when connecting to a network like the internet).

---

### Post by lisati on 2011-12-19
> **losbey said:**
> No one else has access to this computer

Not quite true: as soon as you connect to your bank's website, they know enough about you to at least try to access the data on your computer. Although this is unlikely to happen with trustworthy websites, there's always a small risk of something going wrong.

---

