---
title: "Login Keyring"
date: 2010-10-12
forum: General Help
---

### Post by evworld on 2010-10-12
I upgraded from 10.04 to 10.10 threw software manager.

Now I get an unlock keyring popup after startup. 

It says:  The Login Keyring did not get unlocked when you logged into your computer.  I had it setup to auto login with lucid and I upgraded to 10.10.  

It still auto logs in with 10.10 put I get the Unlock Keyring pop up.  

Any ideas...

---

### Post by Rasa1111 on 2010-10-12
well, Im not positive, 

 But Ive seen it come up a few times in my 10.10 install, 

 and just a little while ago,
 I went into "startup applications",
and there is a "Certificate and key storage"GNOME Keyring"
[ATTACH]172127[/ATTACH]
 that you can apparently stop from starting upon startup. 

 I havent bothered to try it yet, as Ive only seen it a few times,
but you might give that a try if it's annoying you. 

 hope it helps.

---

### Post by evworld on 2010-10-12
> **Rasa1111 said:**
> well, Im not positive, 

 But Ive seen it come up a few times in my 10.10 install, 

 and just a little while ago,
 I went into "startup applications",
and there is a "Certificate and key storage"GNOME Keyring"
[ATTACH]172127[/ATTACH]
 that you can apparently stop from starting upon startup. 

 I havent bothered to try it yet, as Ive only seen it a few times,
but you might give that a try if it's annoying you. 

 hope it helps.


Mine is checked like your picture.  Is there any danger to uncheck it and start my computer back up.  I new to linux and I found in the past that I screw things up by my changes.   I just don't want to wreck my system.  But,  I don't want to keep putting my password in either.    I dual boot with windows and it annoying when I boot to linux..

---

### Post by Rasa1111 on 2010-10-12
> **evworld said:**
> Mine is checked like your picture.  Is there any danger to uncheck it and start my computer back up.  I new to linux and I found in the past that I screw things up by my changes.   I just don't want to wreck my system.  But,  I don't want to keep putting my password in either.    I dual boot with windows and it annoying when I boot to linux..

Well, I can't tell you yes or no with 100% certainty,
So I won't tell you either... 

my intuition tells me that it would not wreck your system. 

 But,
 I just did some searching, and on this gnome.org/gnomekeyring page , [http://live.gnome.org/GnomeKeyring/Ssh](http://live.gnome.org/GnomeKeyring/Ssh) 

 It does indeed provide the same instructions,
to disable it from startup apps. 

> Use the "Startup Applications" capplet (ie: gnome-session-properties) and disable the "SSH Key Agent" startup program.

 there are also a few other methods one can use to do the same thing.

 

 good luck.

---

### Post by 3Miro on 2010-10-12
If you use a wireless network with a passphrase, then you will be asked to unlock the keyring at startup and I don't think you can disable it. I think you can change the settings on the keyring itself so that it doesn't require a password to unlock (like setting an empty password), but this is a security risk (especially if you use the keyring to store more than just the network password).

If removing it from the startup applications (uncheck the box) doesn't help, then I suggest you leave it alone and type in the password every time. Some security features are there for a reason.

---

### Post by evworld on 2010-10-12
> **3Miro said:**
> If you use a wireless network with a passphrase, then you will be asked to unlock the keyring at startup and I don't think you can disable it. I think you can change the settings on the keyring itself so that it doesn't require a password to unlock (like setting an empty password), but this is a security risk (especially if you use the keyring to store more than just the network password).

If removing it from the startup applications (uncheck the box) doesn't help, then I suggest you leave it alone and type in the password every time. Some security features are there for a reason.

Thanks for your response.

I have my computer wired to my router.  

I disabled auto login.  When I do it that way I log in from the login screen.  I don't get the pop up about the keyring.

I then went and activated auto log in.  And once again I get the keyring pop-up.

---

### Post by evworld on 2010-10-13
Still can't figure out..

---

### Post by 3Miro on 2010-10-13
If you are using a desktop computer wired to the Internet and you have good control on who is allowed to use it (i.e. it is in your house and you trust everyone else in it), then you can set an empty password for the keyring. You will only need to click enter without typing anything.

---

### Post by evworld on 2010-10-13
> **3Miro said:**
> If you are using a desktop computer wired to the Internet and you have good control on who is allowed to use it (i.e. it is in your house and you trust everyone else in it), then you can set an empty password for the keyring. You will only need to click enter without typing anything.


Thanks again for your response.  I just wondering why I need to do anything.  I never got the keyring thing with 10.04.  Now I upgraded I get the keyring popup.

---

### Post by xnostradamusx on 2010-10-13
click system -preferences - password and encryption keys 

then in the password tab you will see something passwords. under that you can right click the first selection and change password. enter your current password and for the new password leave it both blank. click ok it will tell you that your about to use unsafe storage. ignore it. problem solved

---

### Post by evworld on 2010-10-13
> **xnostradamusx said:**
> click system -preferences - password and encryption keys 

then in the password tab you will see something passwords. under that you can right click the first selection and change password. enter your current password and for the new password leave it both blank. click ok it will tell you that your about to use unsafe storage. ignore it. problem solved


That seems to work...

---

### Post by repunante on 2010-10-13
> **evworld said:**
> That seems to work...


I think I've found a better way here:

[http://ubuntuforums.org/showthread.php?p=9938975](http://ubuntuforums.org/showthread.php?p=9938975)

Basically store the passwords in "Login Keyring" instead of the "Default Keyring". Seems to work and without security problems.

---

### Post by Rasa1111 on 2010-10-14
> **repunante said:**
> I think I've found a better way here:

[http://ubuntuforums.org/showthread.php?p=9938975](http://ubuntuforums.org/showthread.php?p=9938975)

Basically store the passwords in "Login Keyring" instead of the "Default Keyring". Seems to work and without security problems.

 awesome, worked great! thanks. :D <3

---

### Post by dhbc on 2010-10-19
I wish I could click the f'ing thing. Due to company policy I've had to change my password and now, when I logion the Unlock Login keyring dialogue appears but the machine is totally locked. I can't do anything. Nothing. This is the end for me. I've had it with fighting Ubuntu. Any ideas people or I'm back to Windows. 

I'm on 10.04 on a IBM T60p.

---

### Post by diwant on 2011-02-02
> **xnostradamusx said:**
> click system -preferences - password and encryption keys 

then in the password tab you will see something passwords. under that you can right click the first selection and change password. enter your current password and for the new password leave it both blank. click ok it will tell you that your about to use unsafe storage. ignore it. problem solved

You don't want to do this.  If you do this and a friend with a very basic knowledge of Gnome borrows your computer to check email or something, that person can within ten seconds see your password for everything.  I have this problem of the keyring not getting unlocked on login, but I am going to find another fix.

---

### Post by jasker on 2011-03-02
For those getting the "Keyring was not unlocked on login" message, try installing package *libpam-gnome-keyring*  (i'm assuming you're using gdm as your login manager still)

Package description: "This package contains a PAM module that will automatically unlock the keyrings using your login password, making gnome-keyring usage transparent without losing its security benefits."

---

### Post by FacesComix on 2011-03-18
My Ubuntu shows that I already have that PAM installed... is there any other reason why this would be doing this? maybe someone should make a ticket...

---

