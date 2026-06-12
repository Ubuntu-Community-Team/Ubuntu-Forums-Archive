---
title: "Evolution and GPG signatures"
date: 2010-02-15
forum: General Help
---

### Post by gigimava on 2010-02-15
Hi everybody, I'm new here, so nice to meet you all.

I'm having the following problem:
I created an RSA signature key with gpg, and then used it in evolution to send a message to myself.
Evolution signs the message and, when it is received again, the signature is successfully verified.

The matter is that evolution seems to be the only client able to verify that signature:
if I open the message with another client (I actually tried Windows live mail and thunderbird), instead of a common signed mail, I see a mail with empty body and two attachments: a .txt and a .sig.
The .txt contains the text of the message, while I guess .sig stands for "signature"...
Though, if I download the attachments and try "gpg --verify signature.sig TXTA005.txt" I get a BAD signature message.

To further analyze the situation, I signed the .txt using the terminal, and compared this signature with the other one, and they are different (maybe also because of the timestamp). Anyway, if I use the terminal to verify the .txt using the signature produced by the terminal, the verification succeeds.

So, what I think is that Evolution actually signs something which is not *just* the .txt file. So the question is, what do I need to pass gpg if I want it to tell me "good signature"?

---

### Post by gigimava on 2010-02-16
I got it! Well... it's quite a mess...
What i did is to create a dummy gpg executable, which just writes down to a file the arguments it's passed.
So I saw Evolution doesn't actually sign just the text, but the whole attachment segment. Ie it does sign
```
Content-Type: text/plain
Content-Transfer-Encoding: quoted-printable

this is a test
```
rather than just
```
this is a test
```

Besides, if you export the message through evolution, a text file is created which uses standard GNU newline format (which is 0A), while the signed segment uses windows newline (0D 0A).
So, if I wish to verify the signature through the terminal, all I have to do is export the mail as a text file, delete everithing I don't need and replace "0A" with "0D 0A".

---

