---
title: "passwd doesn't work on Kubuntu 8.10"
date: 2009-07-02
forum: General Help
---

### Post by wagner.rafael on 2009-07-02
[Kubuntu 8.10 kernel 2.6.27-7 generic]
Good morning, 

I'm trying to change my 'l0327' user password via passwd, and I'm not able to succeed. 

Firstly, I provide a new password with 10 characters, different from the previous one by only the last character. The message is 
"Bad: new password must be different than the old one"

Then, I want to quit and repeatedly press 'Enter'. The odd "updated successfully" message appear:
"No password supplied
Enter new UNIX password:
Retype new UNIX password:
No password supplied
passwd: password updated successfully
l0327@rafaelw-desktop:~$"

In the end, the password isn't changed at all.

Thank you in advance for any help and information. Rafael W.
----

---

### Post by t0p on 2009-07-02
passwd on Kubuntu *does* work - you're just not using it correctly. The Ubuntu (and Kubuntu) version of passwd has some rules about the passwords that can be generated. For example, the new password can't be "too short" (at least 7 characters I think), it cannot be a palindrome (a word spelt the same backwards as forwards) and it must be materially different from the password it is replacing. So you will have to make it something other than what you have been trying.

---

### Post by wagner.rafael on 2009-07-02
OK, thank you t0p. So this is a different policy than the one in Kubuntu 6.4, which I was used to.

---

### Post by t0p on 2009-07-02
These stupid policies are a pain. I would like to make my password on one machine a simple press of the Return key, in old Stallman style. But Ubuntu won't let me. 

Something I've wondered before is: where are the policies set? And is it possible to change them? I've asked this here before, but no one could answer me then. Can anyone tell me now?

---

### Post by sisco311 on 2009-07-02
> **t0p said:**
> These stupid policies are a pain. I would like to make my password on one machine a simple press of the Return key, in old Stallman style. But Ubuntu won't let me.


[http://ubuntuforums.org/showthread.php?t=513820]("http://ubuntuforums.org/showthread.php?t=513820")

> 
Something I've wondered before is: where are the policies set? And is it possible to change them? I've asked this here before, but no one could answer me then. Can anyone tell me now?

Change the password as root.

---

### Post by t0p on 2009-07-02
Thanks sisco311! When I get home I shall put this into effect. Insecurity is such a comfort.

---

### Post by sisco311 on 2009-07-02
> **t0p said:**
> Thanks sisco311! When I get home I shall put this into effect. Insecurity is such a comfort.

:)

In the meantime I've found the configuration file: /etc/pam.d/common-password. Read the man page for more info:
```
man pam_unix
```

---

### Post by t0p on 2009-07-02
And thanks again!

---

