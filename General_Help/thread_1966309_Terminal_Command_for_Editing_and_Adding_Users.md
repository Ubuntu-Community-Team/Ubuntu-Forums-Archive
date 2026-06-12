---
title: "Terminal Command for Editing and Adding Users"
date: 2012-04-26
forum: General Help
---

### Post by merlinus on 2012-04-26
For some reason, I cannot unlock the Users dialog. My best guess is because I get a prompt to unlock the keyring upon logging in, and then cannot get sudo privileges.

Another instance of this is when there are kernel updates.  I have to use the terminal -- sudo update-manager -- in order to download these.

Is there a workaround for this problem?

---

### Post by gschoper on 2012-04-27
Are you saying that you can sudo from the commandline but not when prompted graphically? Does this happen with all apps requiring SU priviledges or just updates?

---

### Post by merlinus on 2012-04-27
System updates, not others.  And the Unlock button on dialog boxes such as User Accounts does not work.  I click on it and nothing happens.

---

### Post by gschoper on 2012-04-27
What happens if you type gksu xterm as you normal user account from a terminal? Do you get prompted for your password, and do you end up with a root xterm?

---

### Post by merlinus on 2012-04-27
I get a root xterm.  But how will that allow me to use the Unlock button in the Users dialog?

---

