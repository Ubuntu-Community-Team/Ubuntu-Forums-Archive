---
title: "GPG - PGP - Evolution - a feature"
date: 2010-03-03
forum: General Help
---

### Post by nerderello on 2010-03-03
when I receive an encrypted email, Evolution recognises it and pops up a password/pass pharse box, to enter the GPG password/pass phrase. It then decrypts the email for me.

This, however doesn't happen if the email has been given one of those auto-generated messages at the end (such as this:
```

This e-mail (including any attachments) is intended for the above-named
 person(s). It is confidential and may contain legally privileged 
information....... 


```

When I get one of those sort of emails (such as if I send one from my work place using WinXP and PGP Desktop software) then I get to see the encrypted email and not its decrypted contents.

I can (and do) of course simply either :-
save the PGPexch.htm.pgp attachment (this is how it appears) to a handy folder and then decrypt it using (in the terminal)
```

gpg -d PGPexch.htm.pgp > clear-text.html

```
Which produces a file called **clear-text.html** which I can then open in Firefox.

or (if the email hasn't got an attachment) I can cut and paste 
```

-----BEGIN PGP MESSAGE----- 
Version: 9.6.0 (Build 214)

qANQR1DBwU4D3sT8DF9BIzMQB/9vxhTwgAWpWNcmuYn/8DsuRsWOZPeoe/4swBoG 
qUpufYTTp....
....
YENKhFgMJJXz26kBAPUN9xXSvj6pZ9RIYKmxTRmfQPE91Ie1ucPmtSfH6w== 
=YMp4 
-----END PGP MESSAGE-----

```
into my favourite editor (gedit), save that text file as something obvious (like **encrypted.txt**) and then go through the decryption phase with gpg (as described above).

All a bit of a pain.

Wouldn't it be nice if Evolution could recognise such emails in the first place? 

I think the problem lies in the email header. in the emails that it doesn't recognise as encrypted the email has:
```

Content-Type: text/plain; charset="us-ascii"

```

whereas the emails that are recognised have:
```

Content-Type: application/pgp-encrypted

```


Is it really too much to ask that Evolution looks past the header and sees if the email is encrypted? When I'm at work, using WinXP, Outlook and PGP Desktop, it does all of the above fiddling around for me.

---

### Post by godjil on 2010-07-05
hm.. how i can use pgp in evolution without save attach?

---

### Post by dcstar on 2010-12-18
> **nerderello said:**
> when I receive an encrypted email, Evolution recognises it and pops up a password/pass pharse box, to enter the GPG password/pass phrase. It then decrypts the email for me.

This, however doesn't happen if the email has been given one of those auto-generated messages at the end (such as this:
```

This e-mail (including any attachments) is intended for the above-named
 person(s). It is confidential and may contain legally privileged 
information....... 


```
.........
Wouldn't it be nice if Evolution could recognise such emails in the first place? 

I think the problem lies in the email header. in the emails that it doesn't recognise as encrypted the email has:
```

Content-Type: text/plain; charset="us-ascii"

```

whereas the emails that are recognised have:
```

Content-Type: application/pgp-encrypted

```


Is it really too much to ask that Evolution looks past the header and sees if the email is encrypted? When I'm at work, using WinXP, Outlook and PGP Desktop, it does all of the above fiddling around for me.

I seriously doubt that this is an Evolution problem, this is most likely a problem of the e-mail client/server not correctly processing the adding of the Disclaimer message to the encrypted e-mail.

You should not have an e-mail with mixed encrypted and unencrypted content, and if a disclaimer is required then the original encrypted e-mail should then be a separate attachment within the new e-mail with the clear text Disclaimer content - then you would just be able to access it directly as with any other attachment.

Most likely the problem is just another Microsoft kludge which breaks the relevant RFCs (that Evolution adheres to) but works with MS products.

---

