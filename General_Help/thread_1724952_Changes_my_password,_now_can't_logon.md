---
title: "Changes my password, now can't logon"
date: 2011-04-09
forum: General Help
---

### Post by Cool Javelin on 2011-04-09
Help Please, 

This afternoon, I tried to change the password, for the windows access via Samba, but I goofed.

While logged in with a Putty session, I typed:

```
sudo passwd mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark

```

It asked me for the new password after the first line, then again after the second line as expected.

In retrospect I probably should not have typed the first line.

Now, however, I can't log in via putty. When I attempt to, it asks for my password, but neither the new nor old password works.

I DO have access to the Samba shares from other windows machines using the new password so that is OK.

It is a non GUI 10.04 server with one user, mark. 

Help, please, how do I fix it?

Ideally, I guess I want the old password for the log in, but the new password for Samba shares.

Thanks, Mark.

---

### Post by Cool Javelin on 2011-04-09
Additional information: Last week, before this issue, I added root to the list of shares and have access to \ from windows.

This does not mean I can edit files I am not allowed to, I have not tried that.

Maybe I can fix the problem by altering something via Samba shares? Not likely but hopefully.

Mark.

---

### Post by Krytarik on 2011-04-09
I suspect that you somehow mistyped the new password upon changing it.

And you said you don't have physical access to that machine, so that you can boot into recovery mode (root shell prompt), right?

So, I guess that best available option right now is to enable the root account, if you haven't done so already, and login as root to circumvent the 'sudo' thing, then change your user's password:
[https://help.ubuntu.com/community/RootSudo#root%20account](https://help.ubuntu.com/community/RootSudo#root%20account)

Greetings.

---

### Post by Cool Javelin on 2011-04-09
Thanks, Krytarik.

I do have physical access to the machine, I think "recovery mode" is one of the options I see during boot.

I followed the link you gave, but it assumes I have a prompt to be able to run the commands

```
sudo -i
sudo passwd root

```

But, since I can' log in, I can't do those.

So, I guess I need to boot into recovery mode, then run:

```

sudo passwd mark

```

??

Or, once in recovery mode, am I a superuser and I don't need the sudo part??

I guess, in the future, I should have a second account just lying around for issues like these.

Mark.

---

### Post by Krytarik on 2011-04-09
Ah, I obviously overlooked the initial "sudo" of the proposed procedure.

Yeah, boot into "recovery mode", then choose "root shell prompt". When you are at the prompt then, you don't need to use "sudo", because you will already be root.

---

