---
title: "Reset Password"
date: 2012-08-30
forum: General Help
---

### Post by stangdaman on 2012-08-30
So, I always use my Ubuntu laptop along with a windows machine using synergy and I thought I was logging into the linux machine but synergy didn't change focus like I thought it had and I chatted my password out to someone in the office. I need to change my password before some well deserved hijinx begin. 

I tried searching for reset password or change root password but I seem to only find references to how to do it through the recovery console for people that have forgotten their password. I don't really need that since I know what it is and am currently logged in. Is there another simple way to change my password on my linux machine. I'm sure this is the most simple thing and I'm just too much of a newb.

---

### Post by MG&amp;TL on 2012-08-30
Head to the users and groups dialog and set it there.

Or:

```
passwd <user>
```

replacing <user> with your username.

---

### Post by stangdaman on 2012-08-30
Would it be the same for the root password as well?

---

### Post by MG&amp;TL on 2012-08-30
> **stangdaman said:**
> Would it be the same for the root password as well?

Yes, although that's not encouraged. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by coldcritter64 on 2012-08-30
The root account is disabled by default in Ubuntu OP, you don't need to even think about the root password unless you have actually enabled it yourself .

The command "sudo" is how you raise privileges when and as needed. Cheers.

Edit : just to add, when you use the sudo command it is your user password you enter.

---

### Post by stangdaman on 2012-08-30
That's good to know. Thanks guys.

---

