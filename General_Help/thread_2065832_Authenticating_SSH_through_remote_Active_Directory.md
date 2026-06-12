---
title: "Authenticating SSH through remote Active Directory"
date: 2012-10-03
forum: General Help
---

### Post by samradio on 2012-10-03
I'm an IT professional needing help.  Here's the situation:  we have control of an Ubuntu server in the cloud.  We maintain an SSH tunnel for a group of employees.  Right now, those employees just use the same private key for a single public key stored on the server.  We rotate the key periodically, but we wondered if there was a more secure way.

We use Active Directory for authentication for everything but ssh.  We'd like to start to authenticate our people connecting (SSH'ing) to that Linux server via our Active Directory.  However, our Active Directory is not at the same site as the linux server.  We've played with likewise-open, and while we can connect the remote linux server to our domain, we can't sustain that connection except through an always-on VPN to our domain controller, which isn't what we'd like.  Looking for options.

Is there a way for users logging into an SSH server to be authenticated via a remote Active Directory?  Thanks for any suggestions.

---

