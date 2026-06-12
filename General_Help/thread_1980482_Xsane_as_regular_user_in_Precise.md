---
title: "Xsane as regular user in Precise?"
date: 2012-05-15
forum: General Help
---

### Post by Marcelo Ruiz on 2012-05-15
Hi,

I have installed an Epson TX105 multifunction printer/scanner in Precise and it works great.
Xsane is driving me insane, though. I can scan as a super user but I cannot scan as a regular user. I assume this should be a problem with permissions but I don't know how to effectively solve it.
I tried to follow instructions in some threads that I found in the forum, but the information seems outdated and it does not apply to 12.04. I did add my account to the sane and scanner groups as suggested there, but still no joy. I also tried 

chmod a+w /dev/bus/usb/001/002

but it doesn't work.
I know Xsane if famous for this problem (which should be addressed somehow by the developers because it frustrates its users).
Does anyone know how to solve this problem in 12.04? I know Simple Scan works but I would like to use Xsane instead because it has more advanced options.
Thanks!

---

### Post by matt_symes on 2012-05-15
Hi

Is there a scanner group ? Are you a member of it ?

To see if there is a scanner group

```
grep scanner /etc/group
```

To see if you are a member type

```
groups
```

If you are not a member

```
sudo usermod -aG scanner <your-user_name>
```

Case sensitive above. Change <your-user_name> for, *cough*, your username :).

Reboot your PC and check you are part of the scanner group with the groups command again.

How did that go ?

Kind regards

---

### Post by Marcelo Ruiz on 2012-05-15
Hi!

Thanks for the reply. Yes, I am a member of scanner (sorry I had a typo in my previous post) and saned.
Any other idea?
Thanks!

---

### Post by matt_symes on 2012-05-15
Hi

Not sure you had a typo. I think maybe somehow i totally misread that sentence in your first post.

You have chmoded the correct device ?

with the scanner plugged in can you post the output of

```
lsusb
```

I'm sure you changed the correct one but it's always wise to double check.

Kind regards

---

