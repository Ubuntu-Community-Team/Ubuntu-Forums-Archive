---
title: "Launchpad - can't validate new OpenPGP key"
date: 2010-04-19
forum: General Help
---

### Post by itsjustarumour on 2010-04-19
Is anybody aware of any problems with the Keyserver on Launchpad.Net?

I've been trying to register my new key for 27 hours... I go through the instructions on Launchpad, generate the "Fingerprint", paste it into the box, the automated email is sent out, I open the email (in KMail), get the box asking me to enter the passphrase to decrypt the email... but when I do I just get "Invalid passphrase; please try again"...

---

### Post by johngreth on 2010-04-20
The problem might also be KMail. It works fine for me in gmail using firegpg.

---

### Post by itsjustarumour on 2010-04-23
> **johngreth said:**
> The problem might also be KMail. It works fine for me in gmail using firegpg.

Hey Johngreth, thanks for the message.  You might be right, could be a KMail issue.  I'd forgotten about firegpg, I'll give that a try!

Cheers,

itsjustarumour

:)

---

### Post by WinterRain on 2010-04-23
Worked fine for me in Thunderbird. But I've never had to go through such a lengthy process just to sign up for something, geez.

---

### Post by itsjustarumour on 2010-04-23
Gah, can't use FireGPG - "This add-on is for older versions of Firefox..."

---

### Post by itsjustarumour on 2010-04-24
Well, I got FireGPG installed on a machine with an older version of Firefox.  Enter the key to decrypt the message, get:

"PGP Encrypted Message, Decryption failed. The specified password is incorrect."

Jeez, what a palaver...  ](*,)

---

### Post by itsjustarumour on 2010-04-24
Perhaps I'm doing this wrong...

When I send off my "fingerprint", I get the message:

"A message has been sent to (my email address), encrypted with the key ****/********. To confirm the key is yours, decrypt the message and follow the link inside."

- where the stars are the series of alpha-numeric characters - those are the ones I put in the box to decrypt the automated email, right?  Or am I  being a donut and theres something else obvious that I'm missing?  :confused:

---

### Post by itsjustarumour on 2010-04-24
DOH! (palm to face) :shock:

It appears that "password" to decrypt the email means my Launchpad password, not the key that was generated... which was a bit misleading to say the least!

---

### Post by itsjustarumour on 2010-04-24
GAH.

Decrypted the email, and still more problems!

The decrypted email contains this bit:

"Please go here to finish adding the key to your Launchpad account:
https://launchpad.net/token/********************"

- where the stars are a list of alpha-numeric characters.  But when I cut and paste that link into a browser, I get:

"Error: Page not found"!

](*,)](*,)](*,)

---

### Post by WinterRain on 2010-04-26
I had a heck of a time getting signed up over at launchpad. It took me a couple of days of pulling my hair out. I'm guessing they only want hardcore geeks reporting bugs, because it takes a hardcore geek just to sign up there.

---

### Post by itsjustarumour on 2010-04-26
> **WinterRain said:**
> I had a heck of a time getting signed up over at launchpad. It took me a couple of days of pulling my hair out. I'm guessing they only want hardcore geeks reporting bugs, because it takes a hardcore geek just to sign up there.

@WinterRain - lol, thanks for the comments.  Been trying on and off all day, just tried again now and it miraculously worked - and I wasn't doing anything differently!  Hay ho, well I guess we've both passed the "trial by ordeal" to become hardcore geeks now eh  :)

Cheers!

itsjustarumour

---

