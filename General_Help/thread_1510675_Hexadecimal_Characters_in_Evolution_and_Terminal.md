---
title: "Hexadecimal Characters in Evolution and Terminal"
date: 2010-06-15
forum: General Help
---

### Post by rdunnion on 2010-06-15
Hi - I have been dredging the internet trying to find the answer to this and frankly, my brain hurts. On some e-mails that show up fine in Windows are showing up with hexadecimal characters in Evolution. I assume that it is because of the encoding because I have downloaded every font in the book, it seems, including the microsoft tty fonts. I only can find how to change the encoding on Evolution and aside from foreign (I'm in US) encodings I just have the unicode 7 & 8 which don't help. I'm thinking there is some sort of proprietary Microsoft encoding that I need. Am I correct? How do I fix this issue? Thanks. - Ryan

---

### Post by rdunnion on 2010-06-16
Bumpity --- Any tips? I can't find a solution anywhere.

---

### Post by quadproc on 2010-06-16
> **rdunnion said:**
> ...On some e-mails that show up fine in Windows are showing up with hexadecimal characters in Evolution.
It would help to know a bit more about the problem.  If the email is not sensitive then you might consider posting it, or part(s) of it here so that we could see it.

You may get some insight into the problem by using ```
od -x 
```to interpret the file as hex.  A posting consisting of a problem area (perhaps one sentence) copied from the output of _od -x_ would probably be useful.

If it turns out that the problem characters can be translated into other ASCII characters, or deleted, then the _tr_ command would be useful - just pipe the file through _tr_ with appropriate translation set up.

quadproc

---

### Post by rdunnion on 2010-06-16
Thx quadproc. Sorry for the lack of information. I wasn't quite sure what was needed.
This is the file cut down somewhat:
[IMG]http://www.flickr.com/photos/47888734@N07/4706912486/[/IMG]
And this is the od output of the file. 
```
ryan@ryan-desktop:~$ od -x email
0000000 6f43 746e 6e65 2d74 7954 6570 203a 6574
0000020 7478 702f 616c 6e69 203b 6863 7261 6573
0000040 3d74 4922 4f53 382d 3538 2d39 2231 430a
0000060 6e6f 6574 746e 542d 6172 736e 6566 2d72
0000100 6e45 6f63 6964 676e 203a 6238 7469 0a0a
0000120 4d28 6961 696c 676e 6c20 7369 2074 6e69
0000140 6f66 6d72 7461 6f69 2c6e 6920 636e 756c
0000160 6964 676e 7520 736e 6275 6373 6972 7470
0000200 6f69 206e 6e69 7473 7572 7463 6f69 736e
0000220 202c 7369 6c20 636f 7461 6465 6120 2074
0000240 6874 2065 650a 646e 6f20 2066 6874 7369
0000260 6d20 7365 6173 6567 292e 4920 2066 6f79
0000300 2075 6163 6e6e 746f 7220 6165 2064 6874
0000320 7369 6d20 7365 6173 6567 202c 6874 6e65
0000340 7020 656c 7361 2065 6f67 7420 206f 680a
0000360 7474 3a70 2f2f 7173 2d6c 6573 7672 7265
0000400 6e2e 2e61 726f 2f67 2f74 3337 3036 2f35
0000420 3831 3935 3931 2f31 3131 302f 202f 4a0a
0000440 6e75 2065 3631 0a0a 6341 6563 7470 6e69
0000460 2067 696c 6566 0a0a 5393 6d6f 2065 6874
0000500 6e69 7367 7720 2065 756d 7473 6120 6363
0000520 7065 2c74 6f20 6874 7265 2073 6577 6320
0000540 6e61 6320 6168 676e 2e65 2020 6854 2065
0000560 6977 6473 6d6f 7420 206f 6e6b 776f 7420
0000600 6568 6420 6669 6566 6572 636e 2065 6f63
0000620 656d 2073 6977 6874 6720 6f72 7477 2068
0000640 6e69 6f20 7275 7320 6970 6972 7574 6c61
0000660 7020 6f72 7267 6d61 942e 0a0a 6142 6973
0000700 2063 6554 7478 202c 2e70 3920 0a35 960a
0000720 9696 3d96 9696 9696 0a0a 7449 7392 7220
0000740 6c65 7461 7669 6c65 2079 6165 7973 7420
0000760 206f 6361 6563 7470 7420 6568 7420 6968
0001000 676e 2073 6577 6c20 6b69 9765 7469 7392
0001020 7420 6568 7420 6968 676e 2073 6577 6420
0001040 6e6f 7492 6c20 6b69 2065 6874 7461 6120
0001060 6572 6820 7261 2064 6f74 6120 6363 7065
0001100 2e74 2020 7542 2074 6572 616d 696b 676e
0001120 7420 6568 7720 726f 646c 6120 646e 6520
0001140 6576 7972 6e6f 2065 6e69 6920 2074 6f74
0001160 7320 6975 2074 756f 2072 6174 7473 7365
0001200 7720 756f 646c 7320 6c6f 6576 6e20 746f
0001220 6968 676e 202e 4120 7466 7265 6120 6c6c
0001240 202c 6874 2065 6469 6165 7420 6168 2074
0001260 6874 2065 6f77 6c72 2064 6177 2073 6f74
0001300 6220 616c 656d 6620 726f 6120 6c6c 6f20
0001320 7275 7020 6f72 6c62 6d65 2073 6177 2073
0001340 6874 2065 7461 6974 7574 6564 7420 6168
0001360 2074 656b 7470 7520 2073 7375 6e69 9767
0001400 6e61 2064 6874 7461 6120 7474 7469 6475
0001420 2065 656e 7261 796c 6b20 6c69 656c 2064
0001440 7375 0a2e 0a0a
0001446
```

---

### Post by quadproc on 2010-06-16
> **rdunnion said:**
> Thx quadproc. Sorry for the lack of information. I wasn't quite sure what was needed.
This is the file cut down somewhat:
[IMG]http://www.flickr.com/photos/47888734@N07/4706912486/[/IMG]
And this is the od output of the file. 
[CODE]ryan@ryan-desktop:~$ od -x email
0000000 6f43 746e 6e65 2d74 7954 6570 203a 6574
...

We would need to see what part(s) of the file contain the problem characters.  The first line, quoted above, contains legitimate ASCII characters but there is too much to scan manually.

If you run od -a then you will get ASCII interpretations of each character.  I don't know how od -a will react to non-ASCII characters but that may be an easy way to find them.

Once you know where the problem characters are then you could point out the addresses (from the left-most column of od) where they are.

quadproc

---

### Post by rdunnion on 2010-06-17
Here is the output of 1 sentence for od -a and -x. I used a sentance with the most mixed up characters, which appear to be apostrophes for the most part.
```
ryan@ryan-desktop:~$ od -a email
0000000   I   t dc2   s  sp   r   e   l   a   t   i   v   e   l   y  sp
0000020   e   a   s   y  sp   t   o  sp   a   c   c   e   p   t  sp   t
0000040   h   e  sp   t   h   i   n   g   s  sp   w   e  sp   l   i   k
0000060   e etb   i   t dc2   s  sp   t   h   e  sp   t   h   i   n   g
0000100   s  sp   w   e  sp   d   o   n dc2   t  sp   l   i   k   e  sp
0000120   t   h   a   t  sp   a   r   e  sp   h   a   r   d  sp   t   o
0000140  sp   a   c   c   e   p   t   .  nl
0000151
ryan@ryan-desktop:~$ od -x email
0000000 7449 7392 7220 6c65 7461 7669 6c65 2079
0000020 6165 7973 7420 206f 6361 6563 7470 7420
0000040 6568 7420 6968 676e 2073 6577 6c20 6b69
0000060 9765 7469 7392 7420 6568 7420 6968 676e
0000100 2073 6577 6420 6e6f 7492 6c20 6b69 2065
0000120 6874 7461 6120 6572 6820 7261 2064 6f74
0000140 6120 6363 7065 2e74 000a
0000151

```

---

### Post by dcstar on 2010-06-17
> **rdunnion said:**
> Hi - I have been dredging the internet trying to find the answer to this and frankly, my brain hurts. On some e-mails that show up fine in Windows are showing up with hexadecimal characters in Evolution. I assume that it is because of the encoding because I have downloaded every font in the book, it seems, including the microsoft tty fonts. I only can find how to change the encoding on Evolution and aside from foreign (I'm in US) encodings I just have the unicode 7 & 8 which don't help. I'm thinking there is some sort of proprietary Microsoft encoding that I need. Am I correct? How do I fix this issue? Thanks. - Ryan

Viewing the Message Headers or Message Source in Evolution will show you the relevant stuff, like:

```
Accept-language: en-US, en-AU
**Content-language: en-US**
X-ms-has-attach: 
X-ms-tnef-correlator: 
Acceptlanguage: en-US, en-AU
**Content-type: text/plain; charset="us-ascii"**
Content-transfer-encoding: quoted-printable
Mime-version: 1.0
```

---

### Post by rdunnion on 2010-06-17
> **dcstar said:**
> Viewing the Message Headers or Message Source in Evolution will show you the relevant stuff, like:

```
Accept-language: en-US, en-AU
**Content-language: en-US**
X-ms-has-attach: 
X-ms-tnef-correlator: 
Acceptlanguage: en-US, en-AU
**Content-type: text/plain; charset="us-ascii"**
Content-transfer-encoding: quoted-printable
Mime-version: 1.0
```

Here's what Mine says:
```
Date: Tue, 15 Jun 2010 20:59:00 -0700
MIME-Version: 1.0
Content-Type: multipart/alternative;boundary="MIMEBoundarydfabcbcce8de53151543825b988a5e51"
Content-Type: text/plain; charset="ISO-8859-1"
Content-Transfer-Encoding: quoted-printable

```

I tried changing the encoding to ISO-8859-1 on Evolution but it didn't help.

---

### Post by dcstar on 2010-06-17
> **rdunnion said:**
> Here's what Mine says:
```
Date: Tue, 15 Jun 2010 20:59:00 -0700
MIME-Version: 1.0
Content-Type: multipart/alternative;boundary="MIMEBoundarydfabcbcce8de53151543825b988a5e51"
Content-Type: text/plain; charset="ISO-8859-1"
Content-Transfer-Encoding: quoted-printable

```

I tried changing the encoding to ISO-8859-1 on Evolution but it didn't help.

You may need to manually install the ISO-8859-1:

[http://andreas.scherbaum.la/blog/archives/272-locales-on-Ubuntu.html](http://andreas.scherbaum.la/blog/archives/272-locales-on-Ubuntu.html)

---

### Post by quadproc on 2010-06-17
> **rdunnion said:**
> Here is the output of 1 sentence for od -a and -x. I used a sentance with the most mixed up characters, which appear to be apostrophes for the most part.

I see two non-ASCII characters in the portion that you posted; as you mentioned, the dc2 character appears to represent an apostrophe.  The etb appears to be some sort of a delimiter, perhaps an extra long dash?

Assuming that those two are the only non-ASCII characters in the file then you could translate twice to convert them to something normal.  Something like
```
tr '\222' "'" < infile | tr '\227' "-"
```
would replace the dc2s wiith apostrophes and the etb with dash (assuming that I got the hex to octal conversions right).  Of course, none of this actually produces displayed output according to the original characters used.  Perhaps the suggestions of the other posters regarding character sets will do that.

If you have more than just a few files to translate then it would probably save effort to code a simple function to do the translation so that you wouldn't have to write it out every time.

quadproc

---

### Post by rdunnion on 2010-06-18
@dcstar - I tried this but it did not seem to help. I followed the instructions in the link then changed the default encoding for Evolution to ISO-8859-1. Am I missing a step?
edit - I just ran locale -a and ISO-8859-1 was not listed. I am researching this issue.

@quadproc - thanks for your help. the e-mail is part of a subscription I receive every night. I would prefer to find a way, if possible, to have the character appear correctly within Evolution rather than creating a txt file then running tr command. It's more of a aesthetics thing, I can figure out what is being said in the email.

---

### Post by curtainsup on 2010-06-18
> **rdunnion said:**
> Bumpity --- Any tips? I can't find a solution anywhere.

I can't find a solution either.

---

