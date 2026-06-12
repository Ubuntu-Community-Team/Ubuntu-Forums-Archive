---
title: "How do I get Ubuntu to stop asking me for my password so many times?"
date: 2010-06-06
forum: General Help
---

### Post by Ulysses1994XF04 on 2010-06-06
I appreciate Ubuntu's security concerns for my laptop, but really, there's no chance of anyone else using this laptop besides me.

Whenever I turn on my computer, asks, (after I enter my login password) for the password for my "default keyboard settings" (or something like that) 4 times and my WEP 128 (whatever that is) password. I just hit "cancel" or the little "x" in the corner, but it's a bit of a nuisance to do it each time I turn on my computer.

How do I get Ubuntu to stop asking me for my password for so many things?

---

### Post by kerry_s on 2010-06-06
for the login, system-> administration-> users & groups
where it says "password" click "change", check "don't ask for password on login" & ok, don't worry about the rest, just check the box & ok.

for the wep, don't put a password on the key manager & make sure you select "available to all users" in the edit connections.
do a search of the forum for detailed instructions, it has been covered so many times it's getting old.

i don't know what you mean about the keyboard.

for programs you can add a sudoers entry to not ask for a password, for what ever programs you want.

---

### Post by Ulysses1994XF04 on 2010-06-06
I typed "WEP password" into search and all I got was posts to "networking and security" threads that didn't seem to cover my concern. I just want the computer to stop asking me for my WEP 128 password. I don't even know what a WEP 128 is.

---

### Post by Sef on 2010-06-06
> I typed "WEP password" into search and all I got was posts to  "networking and security" threads that didn't seem to cover my concern. I  just want the computer to stop asking me for my WEP 128 password. I  don't even know what a WEP 128 is.

WEP is an old wireless encryption program has been so thoroughly hacked that if you are using it, then you are inviting people to hack your system.  You should turn it off and if you do need wireless, you need to use WPA2.

---

### Post by Ulysses1994XF04 on 2010-06-06
How do I install WPA 2? Will it still work with my ordinary cable internet and wireless router?

---

### Post by jocko on 2010-06-06
To avoid the login password, open up gdmsetup (System-->Administration-->Login Screen) and just set it up to automatically log in your user.

To avoid the key**ring** password, you need to reset the default keyring password (open up the keyring manager (Program-->Accessories-->Passwords and encryption keys).
There may be two or more entries under "passwords", highlight them one by one, right-click and choose "Remove".
Log out and log back in. Next time it asks you to set up a keyring password, just leave it empty and click ok. On the pop up that informs you that this is insecure, just click "enable insecure storage".

For the wep password: Just enter it once and it will get stored in your keyring (that's probably the only reason why you get asked for the keyring password).
Without your wep password you won't have access to your wireless network.

---

### Post by jocko on 2010-06-06
> **Ulysses1994XF04 said:**
> How do I install WPA 2? Will it still work with my ordinary cable internet and wireless router?
That's not something you install in ubuntu, it's a setting in your wireless router.

---

### Post by jrg3 on 2010-06-06
Before removing/deleting old keys you should know that the default keyring password is the very first user password you created. If you can remember what that was then that's the password you need to use.

You can then change the password in:

*applications > accessories > passwords and encryption keys > default*

---

### Post by jocko on 2010-06-06
> **jrg3 said:**
> ... the default keyring password is the very first user password you created.
That's wrong. It's got nothing to do with the user password. The default keyring password is created the first time something is stored in the default keyring, which for most people with wireless networks is the first time they try to access their network.

---

### Post by jrg3 on 2010-06-06
[http://en.wikipedia.org/wiki/GNOME_Keyring]("http://en.wikipedia.org/wiki/GNOME_Keyring")

---

### Post by jrg3 on 2010-06-06
Most problems occur only after a user has changed their user password (login password). Once they change this the applications that use the default keyring are still looking for the original key, which is no longer being typed. 

The process frustrates me because if the default keyring is set as the user password upon account creation (which it is), then it should also change for every subsequent user password change (which it doesn't).

---

### Post by jocko on 2010-06-07
> **jrg3 said:**
> The process frustrates me because if the default keyring is set as the user password upon account creation (which it is), then it should also change for every subsequent user password change (which it doesn't).

You are not entirely correct.
One keyring ("Login") is stored on your first successful login, not when the account is created, and it's password is set to the same as you used on *that login*. If you don't use automatic login your wep/wpa password will be stored in the "Login" keyring and will get automatically unlocked every time you login. If you change your user's password the keyring password will not be changed, as there is no real connection between the keyring daemon (which runs under your user account and stores the keyrings in your ~/.gnome2/keyrings directory) and passwd (which runs as root and stores the password somewhere else, /etc/passwd if I'm not mistaken).
So, if you change a user's password and want to reset the keyring password, just delete the user's  ~/.gnome2/keyrings directory and log off and log back in again. You'll be asked for the wep/wpa password this one time, but after this it will be unlocked when you log in.
If you change to using automatic login, you will have to enter the keyring password every time you login (or reset it and set a blank password).

---

### Post by germanix on 2010-06-07
Hi Jocko, thank you for this explanation. I certainly now understand the way the keyring and passwords work better than before. You learn something new everyday thanks to people like you taking the time to explain it properly. Have a nice day.

---

### Post by badou on 2011-03-11
why it is suggested to first delete all the passwords? the following is what I did and it seems working, and the old passwords are fine.
go to preference - passwords 
right click "passwords: login", select "change password", set the new password to blank, then click "use unsafe save"

> **jocko said:**
> To avoid the login password, open up gdmsetup (System-->Administration-->Login Screen) and just set it up to automatically log in your user.

To avoid the key**ring** password, you need to reset the default keyring password (open up the keyring manager (Program-->Accessories-->Passwords and encryption keys).
There may be two or more entries under "passwords", highlight them one by one, right-click and choose "Remove".
Log out and log back in. Next time it asks you to set up a keyring password, just leave it empty and click ok. On the pop up that informs you that this is insecure, just click "enable insecure storage".

For the wep password: Just enter it once and it will get stored in your keyring (that's probably the only reason why you get asked for the keyring password).
Without your wep password you won't have access to your wireless network.

---

### Post by goughy on 2011-03-16
> **kerry_s said:**
> for the login, system-> administration-> users & groups
where it says "password" click "change", check "don't ask for password on login" & ok, don't worry about the rest, just check the box & ok.



> **jocko said:**
> To avoid the login password, open up gdmsetup (System-->Administration-->Login Screen) and just set it up to automatically log in your user.


Hi all.  I'm having the problem where every time my laptop screen goes off or it goes to sleep it asks me for my password to login.  I have both the settings above set as described.  It doesn't ask me to login when I first turn it on though.  Wondering if anyone has any other ideas?

Ta

---

### Post by WorMzy on 2011-03-16
Change your screensaver settings.

System -> Preferences -> Screensaver

Uncheck the box that says something like "Lock this computer when screensaver activates".

---

### Post by goughy on 2011-03-16
Jeeze, so bloody easy!

I owe you a beer!! :D

---

### Post by new2zorin on 2011-03-18
I am using the Zorin version of Ubuntu, which I just installed yesterday. I was also getting a message that stated "Enter password for Keyring "Default" to unlock"; every time I started up the computer. This appeared about 5 times and I would click on Cancel each time and then it would finally let me get to the desktop. After getting some hints form various Internet forums I fixed this with the following process. 
Opened the main menu > System > Preferences > Passwords and Encryption Keys

Highlighted "Passwords: Default" 
Clicked on the Edit tab at the top and deleted "Passwords Default". 

Closed out and rebooted. I got a new massage that wanted to create a NEW DEFAULT KEYRING PASSWORD. I left both the new password and confirm password fields blank and clicked OK or whatever the affirmative choice was. Then got a complaint message that a blank password is not a good idea. I told it to do it anyway. 

Rebooted again and now boots fine.:)

---

