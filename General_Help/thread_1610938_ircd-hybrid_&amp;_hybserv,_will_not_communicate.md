---
title: "ircd-hybrid &amp; hybserv, will not communicate"
date: 2010-11-01
forum: General Help
---

### Post by tdiaz on 2010-11-01
I've got both installed and while I can connect to the server, I'll be darned if I anything I have tried with either ircd.conf or hybserv.conf has resulted in the two talking:

hybserv.log shows this:

> Mon Nov  1 07:27:40 2010 Connecting to 127.0.0.1[127.0.0.1] tcp/6667
Mon Nov  1 07:27:40 2010 Connected to 127.0.0.1 tcp/6667
Mon Nov  1 07:27:40 2010 Server Error: Closing Link: 127.0.0.1 (Invalid servername.)
Mon Nov  1 07:27:40 2010 Read error from server: File exists


Or the variant of (Server ID Exists) depending on what I do with the servername. Right now it's all 127.0.0.1, I've had it real names, the same as the DNS, and I've had it bogus. If they match, I get server ID exists. If they're not matched, I get Invalid Servername. 

hyberserv.conf:
[PHP]O:operator@127.0.0.1:passwordfrommkpasswd:operator:segj
A:user <user@domain.org>
N:127.0.0.1:my.irc
S:password:127.0.0.1:6667
V:127.0.0.1
C:#services
I:*.blah.com:6:1[/PHP]


[PHP]connect {
	/* name: the name of the server */
	name = "my.irc";

	/* host: the host or IP to connect to.  If a hostname is used it
	 * must match the reverse dns of the server.
	 */
	host = "127.0.0.1";

	/* passwords: the passwords we send (OLD C:) and accept (OLD N:).
	 * The remote server will have these passwords reversed.
	 */
	send_password = "password";
	accept_password = "password";

	/* encrypted: controls whether the accept_password above has been
	 * encrypted.  (OLD CRYPT_LINK_PASSWORD now optional per connect)
	 */
	encrypted = no;
	hub_mask = "*";
	class = "server";
};
[/PHP]

Any clues, anyone have a working example?

The install is 9.10,  mythbuntu with ubuntu desktop added, if that makes a difference.

Google, the docs, etc - all lead to seemingly everything I've tried.

---

