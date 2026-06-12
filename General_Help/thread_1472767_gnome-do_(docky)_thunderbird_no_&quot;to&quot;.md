---
title: "gnome-do (docky) thunderbird no &quot;to&quot;"
date: 2010-05-04
forum: General Help
---

### Post by thebigob on 2010-05-04
Hi all, Using docky I have managed to hook it up to my thunderbird contacts. This works fine. I have also changed my default mail to thunderbird. My problem is when i type in an email address -> tab  -> email -> enter it opens a new compose email but the "TO" field is not populated with the address I selected. any ideas?

---

### Post by camaron1 on 2010-05-05
> **thebigob said:**
> Hi all, Using docky I have managed to hook it up to my thunderbird contacts. This works fine. I have also changed my default mail to thunderbird. My problem is when i type in an email address -> tab  -> email -> enter it opens a new compose email but the "TO" field is not populated with the address I selected. any ideas?
I understand what you want to do is send email from gnome-do. If this is the case is much easier: start typing (on gnome-do) the name or the email address you want to send your e-mail to and press enter when you see to option on right panel. It'll open thunderbird compose window with the email field filled in. This is how it works for me anyway.

---

### Post by timgood on 2010-05-05
This doesn't work for me either. Yes, a new mail window opens, but the email address is not filled in. Using 10.04 64bit with Thunderbird 3.04 from repos. Any ideas?

---

### Post by thebigob on 2010-05-05
> **camaron1 said:**
> I understand what you want to do is send email from gnome-do. If this is the case is much easier: start typing (on gnome-do) the name or the email address you want to send your e-mail to and press enter when you see to option on right panel. It'll open thunderbird compose window with the email field filled in. This is how it works for me anyway.

Indeed this does open the window however the to field is just blank.

> **timgood said:**
> This doesn't work for me either. Yes, a new mail window opens, but the email address is not filled in. Using 10.04 64bit with Thunderbird 3.04 from repos. Any ideas?

This is exactly what I am experiencing

---

### Post by thebigob on 2010-05-05
ok digging a bit deeper the problem appears to reside withing xdg-email.

This is the tool gnome-do calls when sending an email.

when I changed to evolution the output is

```

Running gnome-open "mailto:Jeremy%20White%20%3Cjwhite@example.com%3E"

```

this works great. When using thunderbird this is changed to

```

Running thunderbird -compose ""

```

however if I manually run gnome-open "mailto:Jeremy%20White%20%3Cjwhite@example.com%3E" it works even in thunderbird.

No idea why this changes?

---

### Post by thebigob on 2010-05-05
Ok this is because of a typo in the xdg-email command. I have found a fix for this also so I will get a bug filled and a patch made.

bug can be found [here]("https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/575779") along with the fix if your feeling brave if not this should be patched and fixed soon.

---

### Post by timgood on 2010-05-06
> **thebigob said:**
> Ok this is because of a typo in the xdg-email command. I have found a fix for this also so I will get a bug filled and a patch made.

bug can be found [here]("https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/575779") along with the fix if your feeling brave if not this should be patched and fixed soon.

Thanks for this - works very well!

---

### Post by ClouDdM on 2010-06-01
Hey

I have the same problem. I understand from the above that I have to go in and do changes in the xdg-email command. But how do I do that? Which command do I use to go inside and edit??

Greatly appreciate any help!

---

### Post by thebigob on 2010-06-01
Find out where the command is by using the which command

Then use sudo gedit to open a text editor to change the command like so:

```

callum@callumlap:~$ which xdg-email
/usr/bin/xdg-email
callum@callumlap:~$ sudo gedit /usr/bin/xdg-email
[sudo] password for callum: 
callum@callumlap:~$ 

```

Then find this line
```

TOqul=$(echo "$MAILTO" | grep '^to=' | sed 's/^to=//' | awk '{  printf "%s,",$0 }')

```

and change it to

```

  TO=$(echo "$MAILTO" | grep '^to=' | sed 's/^to=//' | awk '{ printf  "%s,",$0 }')

```

Let me know if this fixes the problem or if i have not explained it very well.

---

### Post by ClouDdM on 2010-06-01
Cheers mate!

That worked like a charm!
Thank you very much.

---

### Post by thebigob on 2010-06-01
> **ClouDdM said:**
> Cheers mate!

That worked like a charm!
Thank you very much.

Your very welcome :)

---

