---
title: "Setting up sudoers."
date: 2006-04-04
forum: General Help
---

### Post by lex1 on 2006-04-04
i am following this thread:

[http://www.ubuntuforums.org/showthread.php?t=66694](http://www.ubuntuforums.org/showthread.php?t=66694)

section 9 talks about  Setting up sudoers.

wHAT i did was :I went

 /usr/share/doc/sudo/examples

and edited that file as stated in the thread under section 9 above.

the only line i could not find was ;
# Members of the admin group may gain root privileges

so what i did was at the end of the file examles I added this line
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%admin ALL=NOPASSWD:QEMU

in section 9 it says
sudo init.d/sudo restart

but this must be wrong because its in
/etc/init.d/sudo

AND when I ran sudo /etcinit.d/sudo restart it did not say
ok the cursor just retuned to the prmpt so i asumed it restated

anyway when I tried to test it by inviking
sudo -K
sudo ifconfig

I WAS asked for a password according to the section 9 
I should not have been asked for a password.

many thnaks for any feedback.

Lex18) 8) :mrgreen: :mrgreen: :mrgreen: :mrgreen:
---------------------------------------------------------
Man is rich in the fewness of his wants

---

### Post by Jason_25 on 2006-04-04
Did you use visudo to edit the file?

---

### Post by lex1 on 2006-04-04
thanks for your post i used nano there could be my problem.
what a sleepy head i am](*,) 

thanks

lex1

---

