---
title: "Thunderbird crashes"
date: 2012-03-18
forum: General Help
---

### Post by yoramdavid on 2012-03-18
Hello,

I am having a problem with Thunderbird, first it stopped downloading messages and now it does not start at all.

When launching the program I get the error:

[HTML]The application had a problem and crashed.
Unfortunately the crash reporter is unable to submit a report for this crash.
Details: The application did not identify itself[/HTML]

I updated it, reinstalled it, still the same.

Can any body help please?
Thank you very much.

Greetings,
Yoram

---

### Post by Rodney9 on 2012-03-18
Thanks to SeijiSensei

you might try forcing a rebuild of your configuration. Shut down all instances of Thunderbird, then open a terminal and enter this at the "$" prompt (without the "$" of course):

Code:

> $ cd
$ mv .thunderbird .thunderbird.old
$ thunderbird &

The first of these moves to the top of your home directory. The next command moves your current TBird configuration and folders into a safe place. The last command runs the current version of Thunderbird as a separate process (the "&" operator).

TBird should ask you again for your email configuration. After you enter your account information, does it work?

[rant]
Firefox and Thunderbird provide essentially no debugging information when run from the command prompt. I've been left scratching my head on a number of occasions wondering why one or the other doesn't start. I know to remove the "lock" and ".parentlock" files from my configuration folders, but when that doesn't fix the problem, I'd love to see some more debugging information. It's as though the Mozilla Foundation decided to ignore its *nix roots and treat programs the way Windows does, hiding useful information from the person running the program.[/rant]
Last edited by SeijiSensei; August 26th, 2011 at 10:44 AM..

---

### Post by yoramdavid on 2012-03-19
> **Rodney9 said:**
> Thanks to SeijiSensei

you might try forcing a rebuild of your configuration. Shut down all instances of Thunderbird, then open a terminal and enter this at the "$" prompt (without the "$" of course):

Code:



The first of these moves to the top of your home directory. The next command moves your current TBird configuration and folders into a safe place. The last command runs the current version of Thunderbird as a separate process (the "&" operator).

TBird should ask you again for your email configuration. After you enter your account information, does it work?

[rant]
Firefox and Thunderbird provide essentially no debugging information when run from the command prompt. I've been left scratching my head on a number of occasions wondering why one or the other doesn't start. I know to remove the "lock" and ".parentlock" files from my configuration folders, but when that doesn't fix the problem, I'd love to see some more debugging information. It's as though the Mozilla Foundation decided to ignore its *nix roots and treat programs the way Windows does, hiding useful information from the person running the program.[/rant]
Last edited by SeijiSensei; August 26th, 2011 at 10:44 AM..

Removing the thunderbird folder, the program now launches.
I tried to add an account but it could not configure, it returned the error that the username or password are not correct. (I know they are). So I then restored my profile folder back and it still works but does not download the messages.

Running from the terminal give the following code:
```
[2] 13426
[1]   Fim da execução com status 127        $ thunderbird
```

Thank you.

Yoram

---

### Post by fonsi2099 on 2012-05-07
This way seems to work for me :
$ cd
$ mv .thunderbird .thunderbird.old
$ thunderbird & 

Your need to resetup your mail. 
Thank you.
:guitar:

---

### Post by yoramdavid on 2012-05-07
Thunderbird somehow started to work again, not sure what made it work again.
Thanks.

---

