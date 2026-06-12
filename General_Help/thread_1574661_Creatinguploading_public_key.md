---
title: "Creating/uploading public key"
date: 2010-09-14
forum: General Help
---

### Post by J V on 2010-09-14
I created a public key, self signed etc ages ago, but every time I try to upload it to keyservers it never shows up on a search... Seahorse help please?

---

### Post by J V on 2010-09-15
What no-one on ubuntu uses public keys? ...

---

### Post by robbiemacg on 2010-09-15
I have succeeded in doing this a couple of times.

If you enter the command **gpg --list-keys**, does it return information about public id? Terminal should print something like:

```
/home/robbiemacg/.gnupg/pubring.gpg
-----------------------------------
pub   2048R/886DDD89 2009-09-04 [expires: 2014-09-03]
uid                  deb.torproject.org archive signing key
sub   2048R/219EC810 2009-09-04 [expires: 2012-09-03]

pub   2048R/7B5D666B 2010-07-20
uid                  robbiemacg <publisher@invisiblepublishing.com>
sub   2048R/B75A87E4 2010-07-20
```What your interested in, if you're trying to upload your public key to a key server is your public id. In my case, **2048R/7B5D666B**. The first part just refers to the number of bits. It's the information following the **/** you'll require when uploading your public key to a key server.

Without closing Terminal, you can now send your public key to a key server by entering the command **gpg --send-keys --keyserver [keyserver.address.com] [yourpublicid]**. So, I'd do something like this:

```
gpg --send-keys --keyserver keyserver.address.com 7B5D666B
```Do you think I have correctly understood what you're trying to accomplish? Are these steps similar to the ones you've tried? Have you checked out some of this information [http://www.gnupg.org/gph/en/manual.html?](http://www.gnupg.org/gph/en/manual.html?)

---

### Post by J V on 2010-09-15
Yes but I was trying to accomplish it via seahorse... If the key is constantly getting updated with signs wouldn't seahorse need to work properly to handle it?

The only error seahorse gives is:
```
(seahorse:4550): GLib-CRITICAL **: g_error_new_literal: assertion `message != NULL' failed
```
Using the CLI the keyserver.pgp.com didn't work, got it onto the pgp.mit.edu one though...

Still, I worry seahorse isn't doing what it should...

---

### Post by robbiemacg on 2010-09-15
Sorry, I'm not familiar with Seahorse. I use GNU Privacy Assistant. I was thinking that trying to send your key via the CLI might return an error that could help us figure out what was going on. As things stand, I'm not sure I can offer a whole lot.

---

### Post by J V on 2010-09-17
Bump, anyone know whats wrong with seahorse?

---

### Post by J V on 2010-09-19
/sigh
buump!

---

