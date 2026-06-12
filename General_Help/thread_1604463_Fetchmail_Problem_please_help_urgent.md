---
title: "Fetchmail Problem please help urgent"
date: 2010-10-24
forum: General Help
---

### Post by snake_eyes on 2010-10-24
Hello,

I have setup the fetchmail as below:

```
poll domain.com
	proto pop3
	via domain.com
	user "user@domain.com"
	pass "123456789"
	is user@domain.com
	keep
	no fetchall
```

when I try to login it gives the following message:

```
fetchmail: 6.3.8 querying domain.com (protocol POP3) at Sun 24 Oct 2010 10:51:52 AM EEST: poll started
Trying to connect to domain.com/110...connected.
fetchmail: POP3< +OK Dovecot ready.
fetchmail: POP3> CAPA
fetchmail: POP3< +OK
fetchmail: POP3< CAPA
fetchmail: POP3< TOP
fetchmail: POP3< UIDL
fetchmail: POP3< RESP-CODES
fetchmail: POP3< PIPELINING
fetchmail: POP3< STLS
fetchmail: POP3< USER
fetchmail: POP3< SASL PLAIN LOGIN
fetchmail: POP3< .
fetchmail: POP3> STLS
fetchmail: POP3< +OK Begin TLS negotiation now.
fetchmail: Issuer Organization: Unknown
fetchmail: domain.com key fingerprint: B1:F4:2D:54:3B:CF:BB:3B:91:09:5A:76:E6:3E:F7:82
fetchmail: Server certificate verification error: self signed certificate
fetchmail: POP3> CAPA
fetchmail: POP3< +OK
fetchmail: POP3< CAPA
fetchmail: POP3< TOP
fetchmail: POP3< UIDL
fetchmail: POP3< RESP-CODES
fetchmail: POP3< PIPELINING
fetchmail: POP3< USER
fetchmail: POP3< SASL PLAIN LOGIN
fetchmail: POP3< .
fetchmail: domain.com: upgrade to TLS succeeded.
fetchmail: POP3> USER user@domain.com
fetchmail: POP3< +OK
fetchmail: POP3> PASS *
fetchmail: POP3< -ERR Authentication failed.
fetchmail: Authentication failed.
fetchmail: Authorization failure on user@domain.com@domain.com
fetchmail: POP3> QUIT
fetchmail: POP3< +OK Logging out

```

Although I'm able to login to the webmail of my domain.com cpanel with the same username and password, please note also that it some time working smoothly and most time it gives login authentication failure:S

Please help gentleman

Sincerely,

---

### Post by SeijiSensei on 2010-10-24
According to "man fetchmail"
>       --sslproto <name>
              (Keyword: sslproto)
              Forces  an  SSL/TLS protocol. Possible values are '', 'SSL2', 'SSL23', (use of these
              two values is discouraged and should only be used as  a  last  resort)  'SSL3',  and
              'TLS1'.   The  default behaviour if this option is unset is: for connections without
              --ssl, use 'TLS1' that fetchmail will  opportunistically  try  STARTTLS  negotiation
              with  TLS1.  You can configure this option explicitly if the default handshake (TLS1
              if --ssl is not used, does not work for your server.

              Use this option with 'TLS1' value to enforce a STARTTLS connection. In this mode, it
              is highly recommended to also use --sslcertck (see below).

              [B]To  defeat  opportunistic  TLSv1  negotiation when the server advertises STARTTLS or
              STLS, use ''. [/B] This option, even if the argument is the empty string, will also sup&#8208;
              press  the  diagnostic  'SERVER:  opportunistic  upgrade to TLS.' message in verbose
              mode. The default is to try appropriate protocols depending on context.

Looks like adding "sslproto ''" to your option list might do the trick.

---

### Post by snake_eyes on 2010-10-24
> **SeijiSensei said:**
> According to "man fetchmail"


Looks like adding "sslproto ''" to your option list might do the trick.

Thank you for your reply, you mean replace the proto with the sslproto? or what the confirmation should be as per the example above?

---

### Post by SeijiSensei on 2010-10-26
> **snake_eyes said:**
> Thank you for your reply, you mean replace the proto with the sslproto? or what the confirmation should be as per the example above?

I doubt you'd replace the protocol statement; just add another line with " sslproto '' " as the man page says.  You did read the man page, right?

---

