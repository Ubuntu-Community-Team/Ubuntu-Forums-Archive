---
title: "k7 suddenly doesn't boot"
date: 2006-06-12
forum: General Help
---

### Post by Ramses de Norre on 2006-06-12
When I booted up my pc this afternoon I got just a black screen after grub.. No splash nor text and there was just a very little bit of hard drive activity.
This only happens with the 2.6.15-k7 kernel, the 2.6.12-k7 and 2.6.15-386 work perfect.
I don't know where to look for logs or anything to troubleshoot this.. I hope someone has an idea. Reinstalling linux-k7 didn't help.

---

### Post by taurus on 2006-06-12
You can look in /var/log/messages for any error message!!!
```

more /var/log/messages

```
After a little HD activity, does your system boot up at all?

---

### Post by Ramses de Norre on 2006-06-12
Hmm I don't now what to look for and the file is huge.. I greped for error and fail but didn't saw any panical looking errors, do you have any idea what could be causing this or what to look for specifically? I attached the file.

And it doesn't boot after the hd activity, this is not in the next 5min and it normally doesn't take 2min to boot into the desktop.

---

### Post by Ramses de Norre on 2006-06-13
Ok I tried again today and I saw that there were no logs in /var/log/messages from the attempt to boot the k7 kernel, all logging for today starts with the 386 kernel I booted up after needing to reset of the k7. I do see the few lines about unpacking linux and so on after I enterd in grub but then my screen remains black.. 
Anyone who knows what could be causing this?

---

