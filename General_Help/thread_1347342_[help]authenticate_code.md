---
title: "[help]authenticate code"
date: 2009-12-06
forum: General Help
---

### Post by zhenbanjiezhuan on 2009-12-06
im  a noob to ubuntu. i just got started today..version 9.10
im having problem with my authenticate code. today morning, i was able to authenticate anything with my login password. but tonight, i cant. it just say 'authentication failure'..im 100% sure i enter the correct password. ive tried many times. im not a stupid typer like that!!..

the biggest problem is..i cant mount any hdd. I go to 'user settings' (try to change user privileges) and click 'click to make changes', the same thing (authentication failure)..

i reboot, i can login with my password..how weird~~

i can only successfully authenticate to change my password in 'user settings', but no luck. I tried changing my password to 123456789.. and i still cant authenticate anything..

please help!!

---

### Post by arcull on 2009-12-06
how many users (logins) did you define, is the user you are working with member of admin group?

---

### Post by 3rdalbum on 2009-12-06
What happens if you type:

```
sudo whoami
```

into the terminal?

Remember, in Ubuntu you need to use the "sudo" command. DON'T use the "su" command, this will always say "Authentication Failure" (because it expects the root password, and there isn't a real root account in Ubuntu).

---

### Post by 3rdalbum on 2009-12-06
Oh I think I understand what's happened. Have you gone into Users And Groups and unchecked the "Administer the system" privilege for your user? If so, then you won't be able to do any of those things.

You'll need to boot up in Recovery Mode to give this permission back to your user account.

---

### Post by zhenbanjiezhuan on 2009-12-06
> **3rdalbum said:**
> Oh I think I understand what's happened. Have you gone into Users And Groups and unchecked the "Administer the system" privilege for your user? If so, then you won't be able to do any of those things.

You'll need to boot up in Recovery Mode to give this permission back to your user account.
..
'
thank you all...
i have no idea lol~~maybe i will try the recover mode tonight....can you provide more detail how you do it in recovery???

thx again..

---

### Post by zhenbanjiezhuan on 2009-12-06
> **3rdalbum said:**
> What happens if you type:

```
sudo whoami
```into the terminal?

Remember, in Ubuntu you need to use the "sudo" command. DON'T use the "su" command, this will always say "Authentication Failure" (because it expects the root password, and there isn't a real root account in Ubuntu).


it says im not in the sudoers file. this incident will be reported.

---

