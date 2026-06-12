---
title: "Problems with Tor setup"
date: 2012-07-26
forum: General Help
---

### Post by stepking2 on 2012-07-26
I installed Tor yesterday with Vidalia, and got it working after  changing 120 > 100 in the /etc/passwd file. It all worked fine, until  today. 

So today, Tor stopped working. Error message said something like this:
"Could  not access /var/run/tor on (myuser,1000), but debian-tor (115) could,  are you sure you are running this as the right user?"

So I changed the folder permission to me, and now it says:
"Permissions on directory /var/run/tor are to permissive." What does that mean?

Then I tried /etc/init.d/tor start(as regular X user):
"/etc/init.d/tor: line 129: ulimit: open files: cannot modify limit: Operation not permitted
* Checking if tor configuration is valid
Jul 26 19:18:25.912 [notice] Tor v0.2.3.19-rc (git-adf14e42194ebfb7) running on Linux
Jul  26 19:18:25.912 [notice] Tor can't help you if you use it wrong! Learn  how to be safe at [https://www.torproject.org/download/download#warning](https://www.torproject.org/download/download#warning)
Jul 26 19:18:25.912 [notice] Read configuration file "/etc/tor/torrc"
Jul 26 19:18:25.918 [notice] This version of OpenSSL has a known-good EVP counter-mode implementation. Using it.
Configuration was valid"

Then /etc/init.d/tor status:
"* tor is not running"

Then /etc/init.d/tor start (as root):
"* Starting tor daemon..."
The rest of the error message is that /var/run/tor is owned by myuser and not debian-tor.

And if I try to use TCP connection instead of local Unix socket:
/usr/bin is not owned by myuser (1000) perhaps try to use it on another user.

My system is Ubuntu 12.04 64bit, 8GB RAM, Crucial M4 512GB.

EDIT: After trying sudo vidalia, my Ubuntu install is broken. Every command return /usr/bin something.

---

