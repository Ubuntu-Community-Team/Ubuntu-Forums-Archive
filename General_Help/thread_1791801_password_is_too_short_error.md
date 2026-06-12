---
title: "password is too short error"
date: 2011-06-27
forum: General Help
---

### Post by sdibaja on 2011-06-27
I have been trying to change my password on this install to a simple 2 character alpha.

I tried using the "users and groups" menu and got the error "password is too short" that also tells me that I need more that 5 characters.
After searching for a bit I found the passwd <username> command to be used in the recovery mode.  I got a similar massage there too.

upon doing a fresh install I am able to initially set a simple password to do what I want, but after changing to a more secure password I have not yet found a way to get back to where I want to be.  I really don't want to burn this down do yet another install.

yes, I know the system is trying to protect me from myself but that is off the point.

Thanks, Peter

---

### Post by haqking on 2011-06-27
> **sdibaja said:**
> I have been trying to change my password on this install to a simple 2 character alpha.

I tried using the "users and groups" menu and got the error "password is too short" that also tells me that I need more that 5 characters.
After searching for a bit I found the passwd <username> command to be used in the recovery mode.  I got a similar massage there too.

upon doing a fresh install I am able to initially set a simple password to do what I want, but after changing to a more secure password I have not yet found a way to get back to where I want to be.  I really don't want to burn this down do yet another install.

yes, I know the system is trying to protect me from myself but that is off the point.

Thanks, Peter


by default is has a minimum of 4 characters.

it can be edited with

gksudo gedit /etc/pam.d/common-password

however if you are unfamiliar with editing these types of files i would not recommend it and it contravenes the built in security model

an example would be to modify the pam_unix.so line with

password   [success=1 default=ignore]   pam_unix.so nullok obscure min=2 max=8 sha512

where min=2 would be a 2 character password etc and nullok means blank passwords are accepted which again is a security risk

---

### Post by seawolf167 on 2011-06-27
I'd suggest keeping the minimum and following Unix password conventions. The quickest and easiest solution if you don't think you can remember any more passwords is to simply double your password, i.e. if you password is "Ab!", you can just double it to "Ab!Ab!" and you'll be good to go.

---

### Post by warl0q on 2012-02-25
root can set shorter passwords like on install. just use sudo passwd username.

---

