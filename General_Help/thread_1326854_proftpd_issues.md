---
title: "proftpd issues"
date: 2009-11-14
forum: General Help
---

### Post by evilbuntu on 2009-11-14
just installed 9.10 from scratch, reinstalled webmin and went to set up my proftpd.

lets me into the desired directories fine but when i set up the users accounts it just keeps continuously giving me the login prompt like im entering the passwords wrong.

an ideas?

its set up inetd

been doing it the same exact way ive always done. if i set their directories as default or home they can get in but not when i put them to the one i want which is located on an external drive.

thanks

---

### Post by evilbuntu on 2009-11-15
Know i should edit but im tryin to bump it a bit

right now no one has ftp access unless i let them use my account

as saud before its set up inetd
previously it was stand alone

could that have something to do with it
i tried editing the config and that screwed it worse soo i put it back. Then tried to remove and reinstall ( through terminal and wweb min ) but it keeps going back in with the same setup. Anyone know how to change it to stand alone so i can try that
thanks

okay, found out this problem only applies to my external drive (which i have ALWAYS used for my ftp previously).

If i set the ftp to ANY folder on the c drive it works fine..... i went into the properties to try and set up "others" permission (using nautilus) and none of the permissions i set seem to stick. AHHHHHHHH I CANT GET IT!!!!!!!!


it is mounting on boot but do i have to manually set up the ftab to mount it?

---

