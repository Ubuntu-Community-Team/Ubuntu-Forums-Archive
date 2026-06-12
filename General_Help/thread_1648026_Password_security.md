---
title: "Password security"
date: 2010-12-18
forum: General Help
---

### Post by Scunnered on 2010-12-18
I am proposing to better secure my system by improving my password(s) and am seeking guidance on this.   Firstly how do I easily change the current sudo password or would it be better to do a complete re-install?

If a complete re-install is best how may I save my current set-up to avoid having to go around the circuit again.  I have changed quite a lot and don't feel like starting all over again.  I currently have all my basic data backed up and can easily copy that to the home folder.

I see from the Community Documentation that an Automatic Password Generator is available within Ubuntu but find that no reference is made on storage of any generated password.  I would like to adopt better passwords but would need some means of safely storing these. Can you offer any suggestion for storage which would automatically let me access e-mail and other sites.

Thanking you in anticipation

---

### Post by nothingspecial on 2010-12-18
Hi ian,

To change your password,

```
sudo passwd ian
```

You will then have to enter our current password

Then you will be prompted to enter a new one twice, that`s it

There are many ways to generate a secure password, I do it like this


I have one password, the only one I`ve ever had. Let`s say for example it's "rollingstones"

Every month, I modify it, differently.

So 


r o l l i n g s t o n e s
(for example) reverse it


s e n o t s g n i l l o r
give every second character a numerical ( if A=1 and B=2........) equivalent

s 5 n 1 5 t 1 9 g 1 4 i 1 2 l 1 5 r

Make every second number the special character that would happen if you pressed "Shift" on my English keyboard............ so
s 5 n ! 5 t ! 9 g ! 4 i ! 2 l ! 5 r

Ok, next month we start with


r o l l i n g s t o n e s
again

Let`s swap each second letter



o r l l n i g n t s n o s e
Then move them one letter down


n q k k m h f o s r m n r d
Then make every third letter a capital


n g K m h F o s R m n R d
So, I always have the same password.   It`s what I do to it that changes. It always starts "rollingstones"

But it could end up
ngKmhFosRmnRd
or



s5n!5t!9g!4i!2l!5r
And as completely different as they are, they are the same, with 3 different 'moves'.

I already know the password, for the first few days I have to remember the moves till my fingers get used to the new password.

---

### Post by Megaptera on 2010-12-18
I like PasswordCard for use at work where I have to change p/w too often!

"A PasswordCard is a credit card-sized card you keep in your wallet, which lets you pick very secure passwords for all your websites, without having to remember them! You just keep them with you, and even if your wallet does get stolen, the thief will still not know your actual passwords. You already protect your wallet very well, and even if it does get stolen the thief will still not know which of the many thousands of possibilities on the card is your password."

[http://www.passwordcard.org/en](http://www.passwordcard.org/en)

---

### Post by Rubi1200 on 2010-12-18
Another great tool that I have seen recommended many times is keepassx, also available from the repositories.

---

### Post by Scunnered on 2010-12-18
My thanks to you all for your advice.

As my advancing years have me asking which day it is I don't see me adopting the first option.  I followed the sudo instruction and even managed to copy it wrongly the second time. Imagine the fun I could have!!

I will look further into the other two options and see how they suit.

At least I have beefed up the initial password now to follow up on the others

Again thanks

---

### Post by Zill on 2010-12-18
Scunnered:  You may like to take a look at [Figaro's Password Manager 2 (FPM2)]("http://als.regnet.cz/fpm2/") (it's in the repos).

This will allow you to keep different passwords for different websites securely, generating them according to your preferences if desired.

You only need to remember one (good!) password then to have secure access to all the others.

This app will also launch a website by double-clicking on it's FPM2 entry, temporarily saving the username and password to quickly paste into the appropriate website fields, avoiding typing errors!

It works well with my doddery old memory :-)

---

### Post by CharlesA on 2010-12-18
> **Rubi1200 said:**
> Another great tool that I have seen recommended many times is keepassx, also available from the repositories.

I use that ^

---

### Post by Megaptera on 2010-12-18
> **Scunnered said:**
> My thanks to you all for your advice.

You're welcome!

---

