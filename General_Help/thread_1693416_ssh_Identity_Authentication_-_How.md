---
title: "ssh Identity Authentication - How?"
date: 2011-02-22
forum: General Help
---

### Post by steevven1 on 2011-02-22
I am asking both a theoretical and a practical question here: When I connect to an ssh server, how can I GUARANTEE that the server I am communicating with is indeed the server that I think I am communicating with, before entering my passphrase? And a follow-up question: Is this method secure against man-in-the-middle attacks, and if so, how?

I have studied cryptography as a hobby, so I am familiar with some of the language, but I am still a beginner. What I would like is (most importantly) a theoretical explanation of how this is done, as in what's going on behind the scenes, and, less importantly, how do I set it up on my server and client machines?

Thanks in advance!

---

### Post by mikewhatever on 2011-02-22
You should probably search for something like - 'how ssh works'.

---

### Post by steevven1 on 2011-02-22
> **mikewhatever said:**
> You should probably search for something like - 'how ssh works'.

Yes, I have done this, and I have found lots of information about the method of transmission encryption (public key cryptography), but everything I have read ASSUMES that you are already communicating with someone whose identity is known, and that there is no "man in the middle."

Even a link to a discussion of what I'm talking about would be appreciated.

---

### Post by mikewhatever on 2011-02-22
Hmm..., by man in the middle, do you mean ISPs and transitional server? I though ssh defeats those by using encryption. 
As for logins, using authentication keys is more secure then passwords.

---

### Post by asmoore82 on 2011-02-22
> **steevven1 said:**
> Yes, I have done this, and I have found lots of information about the method of transmission encryption (public key cryptography), but everything I have read ASSUMES that you are already communicating with someone whose identity is known, and that there is no "man in the middle."

This is correct. There is no way to guarantee it is the right server on that first connection.
You should use some other means to verify it is correct. This is why clients
always warn you and show the server's key fingerprint. Once you save this key
associated with that server, you are guaranteed it is that server.

At this point, A man in the middle can attempt to impersonate the server and
present the correct public key; but the man in the middle doesn't know the
server's private key so encrypted communications will fail.

Even better, any data that you send to the man in the middle encrypted by
that public key cannot even be read by the man in the middle &#8212; the
matching private key is required to decode it. Any data that the server
sends to you cannot be read by the man in the middle &#8212; your private key
is required to decode it.

If the man in the middle attempts to impersonate the server with a new key
that he has created, and you have the previous correct key already,
SSH prints a nice big warning message:

[quote=SSH]@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
32:6b:8f:7c:3a:53:30:53:6d:b7:9c:be:40:56:5c:c2.
Please contact your system administrator.
Add correct host key in /home/asmoore/.ssh/known_hosts to get rid of this message.
Offending key in /home/asmoore/.ssh/known_hosts:1
RSA host key for localhost has changed and you have requested strict checking.
Host key verification failed.[/quote]

---

### Post by steevven1 on 2011-02-22
> **asmoore82 said:**
> This is correct. There is no way to guarantee it is the right server on that first connection.
You should use some other means to verify it is correct. This is why clients
always warn you and show the server's key fingerprint. Once you save this key
associated with that server, you are guaranteed it is that server.

At this point, A man in the middle can attempt to impersonate the server and
present the correct public key; but the man in the middle doesn't know the
server's private key so encrypted communications will fail.

Even better, any data that you send to the man in the middle encrypted by
that public key cannot even be read by the man in the middle — the
matching private key is required to decode it. Any data that the server
sends to you cannot be read by the man in the middle — your private key
is required to decode it.


PERFECT! This was the exact missing link in my mind, and I understand fully now. Thank you very much!

---

