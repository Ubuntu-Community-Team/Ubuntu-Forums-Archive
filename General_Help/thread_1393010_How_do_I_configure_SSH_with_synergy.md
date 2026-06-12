---
title: "How do I configure SSH with synergy?"
date: 2010-01-28
forum: General Help
---

### Post by axima on 2010-01-28
> **Authentication and Encryption**

 Synergy does not do any authentication or encryption.  Any computer can connect to the synergy server if it provides a screen name known to the server, and all data is transferred between the server and the clients unencrypted which means that anyone can, say, extract the key presses used to type a password.  Therefore, synergy should not be used on untrusted networks. 
 However, there are tools that can add authentication and encryption to synergy without modifying either those tools or synergy.  One such tool is SSH (which stands for secure shell).  A free implementation of SSH is called [OpenSSH]("http://www.openssh.com/") and runs on Linux, many Unixes, and Windows (in combination with [Cygwin]("http://www.cygwin.com/")). 
 
**Configuring the Server**

 Install the OpenSSH server on the same computer as the synergy server. Configure the OpenSSH server as usual (synergy doesn't demand any special options in OpenSSH) and start it.  Start the synergy server as usual;  the synergy server requires no special options to work with OpenSSH. 
 
**Configuring the Clients**

 Install the OpenSSH client on each synergy client computer.  Then, on each client, start the OpenSSH client using port forwarding: 
  ssh -f -N -L localhost:24800:server-hostname:24800 server-hostname
The server-hostname is the name or address of the computer with the OpenSSH and synergy servers. The 24800 is the default network port used by synergy;  if you use a different port then replace both instances of 24800 with the port number that you use.  Finally, start the synergy client normally except use localhost as the server host name.  For example:   synergyc -f localhost
Synergy will then run normally except all communication is passed through OpenSSH which decrypts/encrypts it on behalf of synergy.

I need help with configuring the server and the client. I downloaded HotSSH from the software center and now how do i proceed?

---

### Post by audiomick on 2010-01-28
Excuse the question, but why do you need to encrypt synergy? Are there other people in the same network than you?

---

### Post by axima on 2010-01-28
> **audiomick said:**
> Excuse the question, but why do you need to encrypt synergy? Are there other people in the same network than you?

more secure. yes.

---

### Post by axima on 2010-01-30
i take it that most people leave synergy unsecured?

---

### Post by axima on 2010-02-01
synergy is not popular here?

---

