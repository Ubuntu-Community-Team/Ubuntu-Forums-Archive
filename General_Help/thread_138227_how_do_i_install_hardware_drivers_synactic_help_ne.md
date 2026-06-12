---
title: "how do i install hardware drivers? synactic help needed too"
date: 2006-03-01
forum: General Help
---

### Post by slipout on 2006-03-01
Hi ya, this is my first linux com, so please pardon me if this sound stupid. I did a search and learnt about installing via synactic and from the terminal commands. I tried to install my nvidia gfx, but when i type what ever command with sudo, it prompt me with a error. When i cilked on synactic package mangage, nothing happens. Could someone guide me? Thanks alot

---

### Post by az on 2006-03-01
Hmmm.  That is not normal.

What happens when you run

sudo apt-get -f install


If you are not allowed to do that, reboot into recovery mode (press escape to see the boot menu and pick the recovery mode) and try.

---

### Post by slipout on 2006-03-01
Oh yeah the error i got was "unable to lookup XXX via gethomebyname()"
where xxx is my username

edited: i got the same error again. I realise i got the same error whenever there is sudo thingy. And is the synactic stuff normal? I cliked the manager but nothing happens

I got a "could not look up internet address for xxx" when i log in my account too

---

### Post by slipout on 2006-03-01
I think I know what is going on, I dont have any admin status to config anything but I had only created one account. How do I fix this?

Okay found the solution, need to add a addition line to my /etc/hosts right? But when i opened the file, i tried to type in a line, but i couldnt type any words in

---

### Post by slipout on 2006-03-01
ok i guess i fixed the problem. Just incase pp who have the same error with me, this is the solution:

type ls -l /etc/hosts
then
type chmod 644 /etc/hosts

dam it still cant works, 

when i typed
chmod 644 /etc/host it says
"changing permissions of '/etc/hosts': operation not permitted

---

