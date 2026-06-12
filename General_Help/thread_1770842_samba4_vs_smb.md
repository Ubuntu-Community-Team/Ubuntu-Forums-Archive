---
title: "samba4 vs smb"
date: 2011-05-29
forum: General Help
---

### Post by Vevusio on 2011-05-29
ok i know there are a couple of samba threads out there but i did not find anything about this specific issue

i have ubuntu server and tried to 
```
apt-get install samba
```ubuntu kindly told me that i should install samba4, and so i did

now, my very first issue is, the smb.conf file that is being delivered with samba4 (or was it already there? i did not choose to install samba when i installed the server at any rate) is wrong

it contains parameters that samba does not recognize while starting

i kicked it and installed samba (3.x i presume) - the one which has "smbd" as name and not "samba" - which worked out of the box as i expected - ALMOST

the shares worked fine but the problem i had is, i apparently could not stop that thing?!

```

smbd stop

```executed without any error - but smbd kept running in the process list, shares i added/removed/changed rights/etc updated at arbitrary times (instead of after calling "smdb restart") so ye... that kinda sucks

so my questions are

- is samba 4 ready for use now and i just can't seem to find ANYTHING concrete on how to use it?
- any idea why i can't properly stop smbd from running?

---

### Post by Morbius1 on 2011-05-29
Open up Synaptic and look at the description for samba4:
> These packages contain snapshot versions of Samba 4, the next-generation version of Samba. These should be considered _experimental_, and should not be used in production.Don't know why something told you to install it. I don't know why it's in the repository. 

As far as stopping samba why do you need to stop it? The usual way is :
```
sudo service smbd stop
```Although "sudo stop smbd" should work.

---

