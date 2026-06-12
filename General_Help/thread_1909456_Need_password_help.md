---
title: "Need password help"
date: 2012-01-15
forum: General Help
---

### Post by gowings83 on 2012-01-15
Sorry for the probably easy question, but I haven't touched Linux in say 5 years or so.  Anyways I'm looking for a way to remove the password I have to enter to make changes, it's really annoying.  I just want to click to say install a game and have it go without asking for it.  BTW I have Ubuntu 11.10

---

### Post by BC59 on 2012-01-15
I don't know if you change your password and instead of putting a new one, just leave the space blank. I never tried it though....

---

### Post by haqking on 2012-01-15
> **gowings83 said:**
> Sorry for the probably easy question, but I haven't touched Linux in say 5 years or so.  Anyways I'm looking for a way to remove the password I have to enter to make changes, it's really annoying.  I just want to click to say install a game and have it go without asking for it.  BTW I have Ubuntu 11.10

It is not recommended.

You are a a sudo user meaning when you supply that password you are authorising admin changes to take place.

By removing the password it means anything can run with admin privelege, when you browse the internet every site you visit and script that runs is running with admin privelege and you may as well take a hammer to your machine, it will do less damage ;-)

Please read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

Peace

---

### Post by Rebelli0us on 2012-01-15
You have to edit your “sudoers” file and add the NOPASSWD flag.

This is a taboo subject among linux geeks, so don’t ask much more because the censors will close the thread.

---

### Post by haqking on 2012-01-15
> **Rebelli0us said:**
> You have to edit your “sudoers” file and add the NOPASSWD flag.

This is a taboo subject among linux geeks, so don’t ask much more because the censors will close the thread.

I wouldnt say it was taboo or limited to linux geeks, it is a common sense security concept.

IMO

cheers

---

### Post by CharlesA on 2012-01-15
> **Rebelli0us said:**
> You have to edit your &#8220;sudoers&#8221; file and add the NOPASSWD flag.

This is a taboo subject among linux geeks, so don&#8217;t ask much more because the censors will close the thread.

It's not taboo, it's just not a good idea.

I can count the number of times I have to enter my sudo password in day-to-day operations on one hand.

@OP: Read the link Haqking posted, that will tell you all you need to know. ;)

---

### Post by gowings83 on 2012-01-15
Ok well if it's not recommended then I'll just leave it.

---

