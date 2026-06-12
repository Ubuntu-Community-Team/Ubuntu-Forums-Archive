---
title: "problem with resetting password"
date: 2010-06-30
forum: General Help
---

### Post by didix_1 on 2010-06-30
Hello,
I have changed my password by mistake (or stupidity) and i don't know what is the password now, well i searched the internet about how to reset the password and i did find out that from the grub loader i edit the line kernel...
I inset "rw init=/bin/bash" and then i reboot
This is what i did when i rebooted i was loged in to root i inserted the command "passwd marc" (marc is my username) and then as i insert the new password i got the error :
[COLOR=Red]passwd: Authentication token manipulation error
passwd: password unchanged 
[COLOR=Black]THIS IS MY Problem how can i reset my password plz help coz i'm stuck now with windows 7 :mad: THIS SUCKS :([/COLOR]
[/COLOR]

---

### Post by didix_1 on 2010-07-01
I managed to log in as root in shell is there anyway from there to reset my password user "marc"??:confused:

---

### Post by dino99 on 2010-07-01
only for the lazy

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by didix_1 on 2010-07-01
In fact dino99 this is what i already did but as you see when i type "passwd *username*" and change the passwrod i got the "aunthentication token" error thanks anyway for your reply but i just solved my problem this in fact what i did:
As i manage to login as root in shell i deleted the password of the user "*username*" with the command /usr/bin/passwd *<username*> -d 
and i rebooted 
"voila" it worked!:KS
I was directly logged in to my user and in Terminal i typed "passwd [I]username"
[/I]I was able to set new password now   :guitar:

---

### Post by WanderingAlbatross on 2011-10-18
You should mark this as solved, since it contains good information.  I had a similar issue and solved it with [this advice]("http://ubuntuforums.org/showthread.php?t=1862543&highlight=authentication+token+manipulation+error") for Ubuntu 11.10.

---

