---
title: "Managing/adding users in Lucid Lynx"
date: 2010-05-07
forum: General Help
---

### Post by Niva on 2010-05-07
Hello folks,
I'm not sure there's a bug filled out on this but the behavior I'm seeing out of the user admin tool is unexpected.

Basically if you go through System > Administration > Users and Groups then I do not get prompted for a password, I cannot see the root account, nor can I add/modify other accounts.

I understand that Ubuntu has now moved away from allowing the root account desktop access which is ok by me even though it's very much in line with something Apple would do. (odd that this comes right after Ubuntu went all apple style with the default theme too.)  However, I would like to add other accounts to the machine, for my wife and anyone else i choose for example.  Anyways, pushing the "add" button does nothing.  Thankfully the "help" button did work which allowed me to do the following workaround.

I managed to get around this by working through the command prompt, open terminal:

user> sudo -i
type in your password
root> users-admin

This allows the addition of accounts, also seems it allows the root account to be enabled though I haven't bothered to test it.  The one thing I'll say is that it runs VERY SLOW!  

Anyways, this is more of a report than a question for help.

---

### Post by pfnorris on 2010-05-07
The users and groups tool doesn't prompt for a password when it is launched. However if you click on the 'Add' button or the 'Advanced Settings' button you will be prompted for your password in the normal way, and can then proceed to add/configure users.

---

### Post by antenna on 2010-05-07
Well that's what should happen.. but here it doesn't do anything either.

---

### Post by Niva on 2010-05-07
Yeah, it doesn't work the way it's supposed to for sure.  This is the first machine I'm putting 10.04 on which is an amd laptop.  I think I'll give it another month or two before I put it on the main workstation which is still running 9.04

---

