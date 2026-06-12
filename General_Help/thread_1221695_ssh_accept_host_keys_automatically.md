---
title: "ssh accept host keys automatically"
date: 2009-07-24
forum: General Help
---

### Post by b-boy on 2009-07-24
Hi 


How can ssh accept host keys automatically and can a specify a password

---

### Post by nikhilk on 2009-07-24
> **b-boy said:**
> How can ssh accept host keys automatically and can a specify a password

Are you talking about setting up a passwordless SSH login between two hosts? If yes, [here]("http://www.brandonhutchinson.com/Passwordless_ssh_logins.html") are the instructions.

---

### Post by b-boy on 2009-07-24
I have looked at this but it will not help me as the pc I want to ssh into get reloaded often and I can not set the keys each time

---

### Post by nikhilk on 2009-07-24
> **b-boy said:**
> I have looked at this but it will not help me as the pc I want to ssh into get reloaded often and I can not set the keys each time

In that case you can take a backup of the ~/.ssh/authorized_keys file(s) on the SSH server and restore them after reloading the OS. As long as the key of the clients does not change, I imagine, that should only be a minor hassle.
Is this feasible in your scenario?

---

