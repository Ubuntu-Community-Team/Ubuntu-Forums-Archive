---
title: "Update Notifier doesn't require root?"
date: 2012-05-09
forum: General Help
---

### Post by DoritosBR on 2012-05-09
I just upgraded from Ubuntu 10.04 to Xubuntu 12.04.

And I was suspecting, that the update notifier wasn't requesting root privileges.
Today, I made some updates, and it doesn't asked for root permission, or administrative privileges, nor anything.

When was this changed?
And why? (Does anyone have a link on launchpad change for this?)

Updates should be made only by the root, or if your user have the management permissions, it should confirm the user by asking the password.

Updates are dangerous, especially when you have unofficial repositories.

The final question, how do I change it back to asking the password?

PS: It's Xubuntu I'm using. I can't edit the title.

---

### Post by jerome1232 on 2012-05-09
Only users in the admin group can perform updates, in addition only updates for currently installed software will be installed without prompting for a password, If new additional software must be installed then a password will be prompted for.

There's a bit more detail here: [https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates](https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates)


If after reading that faq you still think it's a bad idea for your environment, you can disable the behavior per the faq's instructions.

I wanted to point out, Ubuntu by default provides only security patches, no new features, so updating isn't all that risky. If you have unsupported repositories that you don't trust, then read the purposed updates and don't select them for updating during the update process as you would normally.

---

### Post by DoritosBR on 2012-05-09
Thanks, the FAQ was very clarifying.
I missed the 11.10 version.

---

