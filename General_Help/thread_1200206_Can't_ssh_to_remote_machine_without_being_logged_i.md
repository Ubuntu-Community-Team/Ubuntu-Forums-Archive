---
title: "Can't ssh to remote machine without being logged in already, key authentication only"
date: 2009-06-29
forum: General Help
---

### Post by ck0 on 2009-06-29
I have two machines running 9.04 Desktop edition, one acting as a server running OpenSSH. I've set up the server as per the instructions [here]("https://help.ubuntu.com/community/SSH"), and disabled password authentication.

Using key authentication, I get [FONT="Courier New"]Permission denied (pubkey)[/FONT] on attempting to ssh in. However, if I physically log into the server (as in, go hook up a screen and keyboard and log in) then I can ssh in from the client machine without issue.

With password authentication enabled, I can ssh into the server whether or not I am logged in physically.

I've attached the output of [FONT="Courier New"]ssh -vvv ...[/FONT] for both cases using key authentication. Any help would be appreciated.

---

### Post by ck0 on 2009-07-03
:o

---

### Post by brentwpeterson on 2011-04-29
I am getting a simular problem, I can't login with SSH until someone logs into the console?

---

