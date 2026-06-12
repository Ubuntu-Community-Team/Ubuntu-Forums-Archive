---
title: "Thunderbird. Exchange. Questions."
date: 2010-01-21
forum: General Help
---

### Post by Roasted on 2010-01-21
Using Ubuntu 9.10, I can connect to our exchange server fine with Thunderbird. But there is one thing I miss dearly. Our global address list...

Can Thunderbird somehow pick this up?

---

### Post by jamesisin on 2010-01-21
Is that address list a part of Active Directory?  If so you can connect Tb to an LDAP server (which AD is).

---

### Post by Aenima99x on 2010-01-26
> **Roasted said:**
> Using Ubuntu 9.10, I can connect to our exchange server fine with Thunderbird. But there is one thing I miss dearly. Our global address list...

Can Thunderbird somehow pick this up?

How did you get Thunderbird to connect to your Exchange server?

---

### Post by t4thfavor on 2010-01-26
He's probably using <= exchange 2003, as exchange 2007 has broken all third party exchange clients.

Also he's probably just connecting IMAP instead of real exchange protocol(RPC or whatever), because AFAIK the only linux mail client with exchange support is evolution which coincidently stopped working on echange 2007...

Did I mention that Microsoft broke third party support for exchange?

---

### Post by Roasted on 2010-01-26
I just used imap instead of pop, and typed in the name of the exchange server in the send/receive address, which in our case is simply "exchange."

Worked great...

---

### Post by jamesisin on 2010-01-26
Can you provide a little more detail?  Where is this send/receive located?  In the preferences somewhere?

---

### Post by t4thfavor on 2010-01-26
When he set the account up, he told Thunderbird it was of type IMAP, and then in the outgoing mailserver he put his exchange server, same on the incoming, and voila you are now connected to your exchange server. Not that you get any of the cool stuff Exchange does that way, but you will get emails, and possibly contacts.

---

### Post by jamesisin on 2010-01-26
t4thfavor - And this provided him with a global address list?

---

### Post by Roasted on 2010-01-26
> **jamesisin said:**
> Can you provide a little more detail?  Where is this send/receive located?  In the preferences somewhere?

If you didn't notice, I was the one who asked the original question. I never did get the global address list working. I was telling somebody else who asked how I even got thunderbird to work with exchange. My response above was just how I got the email portion to work... not the address list.

---

### Post by jamesisin on 2010-01-26
I see.  Confused.

Did you make any progress getting access to your global address list?

---

### Post by t4thfavor on 2010-01-26
Nope, I used evolution to get it at one point, but have since upgraded to Exchange 2007 which doesn't support third party clients anymore.

---

### Post by jamesisin on 2010-01-26
So you are looking at specifically an Exchange address list then and not an address list in Active Directory.

---

