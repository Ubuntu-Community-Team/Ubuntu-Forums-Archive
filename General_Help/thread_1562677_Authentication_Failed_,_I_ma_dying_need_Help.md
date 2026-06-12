---
title: "Authentication Failed , I ma dying need Help"
date: 2010-08-27
forum: General Help
---

### Post by Mwanitete on 2010-08-27
Hii brother

I need help ::)

I had Linux ubuntu 9.10 but when I upgraded to linux ubuntu 10.4 I cant login 

it says authentication failed..

what should i do to login normal..?


Have a nice time ::)

---

### Post by Mwanitete on 2010-08-27
I need help ::)

I had Linux ubuntu 9.10 but when I upgraded to linux ubuntu 10.4 I cant login 

it says authentication failed..

what should i do to login normal..?


Have a nice time ::)

---

### Post by wojox on 2010-08-27
Try resetting your password.

[How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by Mwanitete on 2010-08-27
Hey Yep you ::)

I remember my password verry well , I use it in eveything , mail, telephone, facebook

The problem is not about forgeting my password , 

Problem is about Linux Upgrading ,

when I enter the passwod , I dont see that black ring,(it seems like nothing i type ), and when I click enter it say , authentication failed , 

Some friends said I should Edit Pam
/etc/pam.d/gdm.conf add or remove comments @include pam-keyrings

but when i tried I dont know where to put this comments either above or down, but I tried both nothing happened...

Need help, need help , i love ubuntu ::)

---

### Post by wojox on 2010-08-27
Oh a thousand apologies. Reset the keyring

```
rm ~/.gnome2/keyrings/login.keyring
```

---

### Post by Mwanitete on 2010-08-28
Hii ::)

so how to reset this keyring , is just only to enter that Command..??

or I must do other procedures..??

have a nice time brother

---

### Post by Mwanitete on 2010-08-28
Hii Guys when I upgraded my linux ubuntu 9.10 to 10.4 I can't login 

I tried to use vi /etc/pam.d/gdm.conf

remove or comment : @include common -pamkeyring , i put it at the end of the pam:

But still I can't login ...what can I do..?? need Help


#%PAM-1.0
auth requisite pam_nologin.so
auth required pam_env.so readenv=1
auth required pam_env.so readenv=1 envfile=/etc/default/locale
auth sufficient pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth optional pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional pam_gnome_keyring.so auto_start
@include common-password

or where should I put :: @include common-pamkeyring..??

---

### Post by Elfy on 2010-08-28
Threads merged

Don't post duplicates please

---

