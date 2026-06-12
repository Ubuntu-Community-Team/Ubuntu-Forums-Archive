---
title: "reading boot time messages"
date: 2009-10-28
forum: General Help
---

### Post by mike_87 on 2009-10-28
Hello folks,

I'm a brand new Ubuser and relatively new to linux systems except for a brief experience with red hat half a dozen years ago. I like this community as it seems very altruistic and willing to help newbies like myself.

Now, to the point:
At boot time I notice an error message which says something about IO APIC resources, and, although I've spent almost all last night doing research about it, I haven't been able to figure out what that means, and more importantly, I'm unable to read the message entirely, as it blinks for like a tenth of second and is then hidden by the ubuntu loading bar graphic.
So far I went to the Administration -> Log Viewer applet, which seemed very complete (maybe too much, since there're a lot of logs to browse), but the "boot" log had no entry in it, so I read somewhere how to enable boot logging (even though now I don't recall the exact command line) and rebooted, but still it gave me no entry in that file, not even in the /var/log/ directory.
Then I tried using the*dmesg* and *grep* commands, but still I'm unsure how to get *exactly* that little message right before the ubuntu loading bar comes up.

---

### Post by masux594 on 2009-10-28
Don't u remember just a word that is displayed in this error? .. Even a part of it..

Sysc, A

---

### Post by Anthon on 2009-10-28
You could try to temporary remove the word 'splash' from your boot entry in the /boot/grub/menu.lst file.
You might still get other messages pushing useful information away but that probably takes longer than the loading bar to clobber the screen

---

### Post by phillw on 2009-10-28
Hi,

try this thread ...

[http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

Just turned mine on !!!

Regards,

Phill.

---

### Post by mike_87 on 2009-10-28
> **masux594 said:**
> Don't u remember just a word that is displayed in this error? .. Even a part of it..

Sysc, A

yes, it's something about "IO APIC resources"

Anthon, phillw, thanks for your advice, I'm going to try those now.

---

### Post by masux594 on 2009-10-28
Tyy with @phillw solution.. or typing ```
dmesg | grep resources
``` you will see all the messages with "resources" string.. or [if isn't "resources" the correct word] try with another word..

Sysc, A

---

### Post by mike_87 on 2009-10-28
> **masux594 said:**
> Tyy with @phillw solution.. or typing ```
dmesg | grep resources
``` you will see all the messages with "resources" string.. or [if isn't "resources" the correct word] try with another word..

Sysc, A

That did the trick (and I also enabled boot-time logging)

I get this:
```
[    2.351359] IO APIC resources could be not be allocated.
```

Perhaps I should open another thread about it. Thanks for your help folks :)

---

### Post by masux594 on 2009-10-28
if you search over the net you'll find many posts about it..

Sysc, A

---

### Post by P4man on 2009-10-28
Im not sure if that message is actually a reason to worry. If everything works and is stable, I wouldnt worry about it. If you do have stability issues, then add a boot option for the kernel:

```
noapic
```

You can read here how to add boot options:
[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

(scroll up if you havent installed ubuntu yet, scroll further down if you want to make this change permanent)

---

### Post by mike_87 on 2009-10-28
> **P4man said:**
> Im not sure if that message is actually a reason to worry. If everything works and is stable, I wouldnt worry about it. If you do have stability issues, then add a boot option for the kernel:

```
noapic
```You can read here how to add boot options:
[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

(scroll up if you havent installed ubuntu yet, scroll further down if you want to make this change permanent)

I know that philosophy, if it's not broken don't fix it, and I will probably stick to that :)
Thank you all for the advice.

---

