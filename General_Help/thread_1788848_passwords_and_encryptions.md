---
title: "passwords and encryptions"
date: 2011-06-23
forum: General Help
---

### Post by beacon on 2011-06-23
I am having a problem with passwords, and there is a lot of help offered that seems relevant. All, however, start with going to system>preferences>passwords and encryption. When I go there, however, I am told 'could not launch password and encryption keys', so I am stuck at the starting gate. Please can anyone tell me what to do next?

---

### Post by haqking on 2011-06-23
> **beacon said:**
> I am having a problem with passwords, and there is a lot of help offered that seems relevant. All, however, start with going to system>preferences>passwords and encryption. When I go there, however, I am told 'could not launch password and encryption keys', so I am stuck at the starting gate. Please can anyone tell me what to do next?


mmm corrupt package maybe ?

try going to your synaptic package manager and searching for seahorse and making sure it is installed.

You might want to remove then re-add again.

There is a couple of ways to do this, i am keeping it simple for now.

What version of Ubuntu you running ?

---

### Post by beacon on 2011-06-23
Thanks a lot haqking. I have done as you suggested and uninstalled and then reinstalled seahorse. It didn't make a difference. I am using Ubuntu 11.04.

---

### Post by haqking on 2011-06-23
> **beacon said:**
> Thanks a lot haqking. I have done as you suggested and uninstalled and then reinstalled seahorse. It didn't make a difference. I am using Ubuntu 11.04.

can you launch it from CLI ?

sudo seahorse

---

### Post by beacon on 2011-06-23
Thanks again. I did log in as suggested and got the site, but there is nothing in it. I did have the following message: ** (seahorse:7657): WARNING **: couldn't get default keyring name: Error communicating with gnome-keyring-daemon  I don't know if this will help make other suggestions.

---

### Post by haqking on 2011-06-23
> **beacon said:**
> Thanks again. I did log in as suggested and got the site, but there is nothing in it. I did have the following message: ** (seahorse:7657): WARNING **: couldn't get default keyring name: Error communicating with gnome-keyring-daemon  I don't know if this will help make other suggestions.


mmm not sure what the problem is off hand.

you say you are having password problems ? what type of issues or you mean the issue with seahorse ?

also it will be pretty empty until you create something (PGP for email files, keyring, ssh etc)

you can try install GNU Privacy Assistant (GPA) in software centre

does same thing and will show any keys you have on the system already if you have any.

I am not 100% on this though, it might be obvious why you are having problems to someone else on here, hopefully someone else will intervene soon ;-)

---

### Post by gandaran on 2011-06-23
> **beacon said:**
> Thanks again. I did log in as suggested and got the site, but there is nothing in it. I did have the following message: ** (seahorse:7657): WARNING **: couldn't get default keyring name: Error communicating with gnome-keyring-daemon  I don't know if this will help make other suggestions.
try renaming the /home/'user'/.gnome2/keyrings to keyrings0 then start passwords and encryption keys, if no work you can replace the folder again.

---

