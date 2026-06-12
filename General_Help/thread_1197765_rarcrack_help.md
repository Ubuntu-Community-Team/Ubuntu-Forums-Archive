---
title: "rarcrack help"
date: 2009-06-26
forum: General Help
---

### Post by nmaster on 2009-06-26
I first want to say that this is for legal purposes.  A professor at Delft sent me this *.rar but forgot to give me a password.  Its the middle of the night for him (I'm in Cali) but I don't want to wait; I need the contents for the work I'm doing.

So I run "rarcrack thing.rar"  and after a bunch of lines it returns ```
GOOD: password cracked: '1hU'
```The *.xml shows this:
```

<rarcrack>
&#8722;
<abc>
0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
</abc>
<current>1hW</current>
<good_password>1hU</good_password>
</rarcrack>


```'1hW' and '1hU' are not the passwords.
I obviously don't know how to use rarcrack.  Any help?

---

### Post by nmaster on 2009-06-26
I know its only been an hour, but...

anyone?

---

### Post by DeMus on 2009-06-26
> **neal.m.master said:**
> I know its only been an hour, but...

anyone?

At the moment in Delft it is 22.46, so not the middle of the night.

---

### Post by blueridgedog on 2009-06-26
The website states the usage is:

```
rarcrack your_encrypted_archive.ext [--threads thread_num] [--type rar|zip|7z]
```


Try it with --type rar

---

### Post by t4thfavor on 2009-06-26
I have never had much luck with any cracking tools. And if your prof used even a moderatly strong PW you will never get it with brute force.

That said, use words that he may like, such as his dogs name, or where he works or his initials. If you don't know any of this, you can just about forget it.


You will be better off to wait, and explain that he forgot to give you the PW, and that you were unable to complete you assignment.

EDIT:
Oh unless you have a dual i7 quad, that might get you through the passwords a bit faster.

---

### Post by t0p on 2009-06-26
I too had this problem with rarcrack: the program claims it has cracked a password when in fact it has not.  I dumped it in the end.

But that wasn't the real reason I dumped the stupid program.  The way rarcrack works is that it tries to *bruteforce* the password.  Bruteforcing is a truly crap way to crack a password.  For a start, how long is the password?  There's no way you can know this, so the program must waste time running all the combinations of 6 characters, for example, when the password is actually 8 characters long.  And bruteforcing takes a very long time.  Forget it.

The most effective way to crack a password is the approach suggested above by t4thfavor.  People generally choose passwords that are easy to remember - "password", "abcdefg", the wife's maiden name, the dog's date of birth.  So research your target, build up a wordlist personal to him, then put that wordlist in your password-breaking software.  There are still no guarantees this will work, but it has a better chance than rarcrack.

---

### Post by nmaster on 2009-06-26
> **DeMus said:**
> At the moment in Delft it is 22.46, so not the middle of the night.


yeah, i meant that i'd rather not disturb him while he's with his family.

---

### Post by nmaster on 2009-06-26
i'm just gunna wait for him.  its not really that big of a deal.  thanks for the suggestions tho.

---

### Post by skralljt on 2010-05-16
what a typical linux user solution to a problem: waste hours on a computer when a phone call taking 2 minutes would suffice.

---

### Post by K.Mandla on 2010-05-16
Thread closed. Necromancing.

---

