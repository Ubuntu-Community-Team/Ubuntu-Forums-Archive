---
title: "vi not working properly"
date: 2010-12-21
forum: General Help
---

### Post by Vexille on 2010-12-21
Hi

Does anyone know why vi text editor would not work. I'm running Ubuntu server with SIP service and apache and when i try to edit config files with vi it gets messy.

On the bottom of the screen it would not indicate if I'm in backup mode or not. I won't same changes, and it messes up the layout when you use arrow keys to move between the lines. Also sometimes when I use arrow keys it will insert capital A, B, C or D.

Thanx

---

### Post by dandnsmith on 2010-12-21
You're describing a badly configured vi.

For some time (ie a number of releases) I've joyed in the fact that all my arrow keys, Pge Up and Page down do the desired thing, wheres they used to generate odd control characters.

Where is the real problem?
- how about some hand configuration carried down from the past, or incorrect description of the actual keyboard in use?

---

### Post by CharlesA on 2010-12-21
Use vim.

I ran into a similar thing when I used vi on Ubuntu Desktop, had to install vim to get around it.

---

### Post by ph03nix on 2010-12-21
> **Vexille said:**
> Hi

Does anyone know why vi text editor would not work. I'm running Ubuntu server with SIP service and apache and when i try to edit config files with vi it gets messy.

On the bottom of the screen it would not indicate if I'm in backup mode or not. I won't same changes, and it messes up the layout when you use arrow keys to move between the lines. Also sometimes when I use arrow keys it will insert capital A, B, C or D.

Thanx

i have the exact same problem with my vi and the problem with the arrows is permanent; i can't navigate in my text using the arrows on Ubuntu 9.10!plus my backspace won't delete letters when i want to correct my text!is there a way to fix it?i don't want to use vim!i want to fix my vi!

---

### Post by gmargo on 2010-12-21
There unfortunately are multiple versions of **vim**, and the "tiny" version is installed by default.  If you have not already done so, install the **vim-gtk** package.  This contains a much more capable vim, and includes gvim, the gui version.

---

### Post by ph03nix on 2010-12-21
> **gmargo said:**
> There unfortunately are multiple versions of **vim**, and the "tiny" version is installed by default.  If you have not already done so, install the **vim-gtk** package.  This contains a much more capable vim, and includes gvim, the gui version.


That did work for me!Thank you!

---

