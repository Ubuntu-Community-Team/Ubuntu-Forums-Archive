---
title: "access to the default keyring but it is locked"
date: 2011-05-11
forum: General Help
---

### Post by naomibrown on 2011-05-11
Hi,

I've got an error message saying "An application wants access to the keyring 'default' but it is locked" when I log in as a guest. I can't remember the password that I used. Is there any way to reset this password or if not, how do I remove my guest account and set a new one up?

Thanks,
Naomi

---

### Post by tredegar on 2011-05-11
Not sure what you mean by "logging in as guest", but if you login an then **rm -rf ~/.gnome2/keyrings** then the keyrings will be gone after a logout and login, and you'll be asked to set them up again.

Personally, I dislike the whole keyring thing, and leave the options for keyring passwords blank. Then it goes away, and stays away.

---

### Post by naomibrown on 2011-05-14
Thank you!!!

What I meant by the guest thing was that I have one log-in that I use for me and one that I have set up to be accessed by a guest, without a password.

I used that command to delete the keyring that I had forgotten. Then I logged out and back in again and left the password blank when asked for a new password by the key chain dialogue box. This means that they won't be asked for a password after they log in. Then I entered my wireless password as this means that the guest can have access to our wireless network.

It works! Yay!

---

